---
title: Requisitos e considerações para bots de mídia hospedados pelo aplicativo
description: Entenda os requisitos e considerações importantes relacionados à criação de bots de mídia hospedados pelo aplicativo para Microsoft Teams.
ms.topic: conceptual
localization_priority: Normal
keywords: vm do windows server do windows server hospedado pelo aplicativo
ms.date: 11/16/2018
ms.openlocfilehash: a66296951dd2f704d531840f79a4c4b955af6bdf
ms.sourcegitcommit: 3560ee1619e3ab6483a250f1d7f2ceb69353b2dc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/08/2021
ms.locfileid: "53335358"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Requisitos e considerações para bots de mídia hospedados pelo aplicativo

Um bot de mídia hospedado por aplicativo requer a [ `Microsoft.Graph.Communications.Calls.Media` biblioteca .NET](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) para acessar os fluxos de mídia de áudio e vídeo. O bot deve ser implantado em um computador Windows Server ou Windows sistema operacional convidado do servidor (OS) no Azure.

> [!NOTE]
> * As diretrizes para o desenvolvimento de mensagens e ivr (resposta interativa de voz) não se aplicam completamente à criação de bots de mídia hospedados pelo aplicativo.
> * Como a Plataforma de Mídia em Tempo Real da Microsoft para bots está na visualização do desenvolvedor, as diretrizes neste documento estão sujeitas a alterações.

## <a name="c-or-net-and-windows-server-for-development"></a>C# ou .NET e Windows Server para desenvolvimento

Um bot de mídia hospedado por aplicativo requer o seguinte:

- O bot deve ser desenvolvido em C# e no padrão .NET Framework e implantado em Microsoft Azure. Não é possível usar APIs C++ ou Node.js para acessar mídia em tempo real e o .NET Core não tem suporte para um bot de mídia hospedado pelo aplicativo.

- O bot pode ser hospedado em um dos seguintes ambientes de serviço do Azure:
    - Serviço de Nuvem.
    - Service Fabric com conjuntos de escala de máquina virtual (VMSS).
    - Infraestrutura como uma máquina virtual (IaaS) (VM).  
  
- O bot não pode ser implantado como um aplicativo Web do Azure.

- O bot deve estar em execução em uma versão recente da `Microsoft.Graph.Communications.Calls.Media` biblioteca .NET. O bot deve usar a versão mais recente disponível do pacote [NuGet ou](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)uma versão que não tem mais de três meses. As versões mais antigas da biblioteca são preterida e não funcionam após alguns meses. Manter a biblioteca atualizada garante a melhor interoperabilidade entre o `Microsoft.Graph.Communications.Calls.Media` bot e Microsoft Teams.

A próxima seção fornece detalhes sobre onde as chamadas de mídia em tempo real estão localizadas.

## <a name="real-time-media-calls-stay-where-they-are-created"></a>As chamadas de mídia em tempo real permanecem onde são criadas

As chamadas de mídia em tempo real permanecem no computador onde foram criadas. Uma chamada de mídia em tempo real é fixada à instância da máquina virtual (VM) que aceitou ou iniciou a chamada. A mídia de uma chamada Microsoft Teams ou de reunião flui para essa instância da VM, e a mídia que o bot envia de volta para Microsoft Teams também deve se originar dessa VM. Se houver chamadas de mídia em tempo real em andamento quando a VM for interrompida, essas chamadas serão interrompidas abruptamente. Se o bot tiver conhecimento prévio do desligamento da VM pendente, ele poderá encerrar as chamadas.

A próxima seção fornece detalhes sobre acessibilidade de bots de mídia hospedados pelo aplicativo.

## <a name="application-hosted-media-bots-accessible-on-the-internet"></a>Bots de mídia hospedados por aplicativos acessíveis na Internet

Os bots de mídia hospedados por aplicativos devem estar diretamente acessíveis na Internet. Esses bots devem incluir os seguintes recursos:

- Cada instância de VM que hospeda um bot de mídia hospedado por aplicativo no Azure deve estar diretamente acessível da Internet usando um endereço IP público de nível de instância (ILPIP).
    - Para obter e configurar um ILPIP para um Serviço de Nuvem do Azure, consulte [instance level public IP classic overview](/azure/virtual-network/virtual-networks-instance-level-public-ip).
    - Para configurar um ILPIP para um conjunto de escala de VM, consulte [IPv4 público por máquina virtual](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine).
- O serviço que hospeda um bot de mídia hospedado por aplicativo também deve configurar cada instância da VM com uma porta pública que mapeia para a instância específica.
    - Para um Serviço de Nuvem do Azure, isso requer um ponto de extremidade de entrada de instância. Para obter mais informações, [consulte enable communication for role instances in Azure](/azure/cloud-services/cloud-services-enable-communication-role-instances).
    - Para um Conjunto de Escala de VM, uma regra NAT no balanceador de carga deve ser configurada. Para obter mais informações, consulte [redes virtuais e máquinas virtuais no Azure](/azure/virtual-machines/windows/network-overview).
- Os bots de mídia hospedados por aplicativo não são suportados pelo Bot Framework Emulator.

A próxima seção fornece detalhes sobre escalabilidade e considerações de desempenho dos bots de mídia hospedados pelo aplicativo.

## <a name="scalability-and-performance-considerations"></a>Considerações sobre escalabilidade e desempenho

Os bots de mídia hospedados pelo aplicativo exigem as seguintes considerações de escalabilidade e desempenho:
- Os bots de mídia hospedados pelo aplicativo exigem mais capacidade de computação e rede (largura de banda) do que bots de mensagens e podem incorrer em custos operacionais significativamente maiores. Um desenvolvedor de bot de mídia em tempo real deve medir cuidadosamente a escalabilidade do bot e garantir que o bot não aceite mais chamadas simultâneas do que pode gerenciar. Um bot habilitado para vídeo pode ser capaz de sustentar apenas uma ou duas sessões de mídia simultâneas por núcleo de CPU (se usar os formatos de vídeo RGB24 ou NV12 "brutos").
- No momento, a Plataforma de Mídia em Tempo Real não tira proveito de qualquer GPU (Unidades de Processamento de Elementos Gráficos) disponível na VM para descarramento/decodificação de vídeo H.264. Em vez disso, a codificação de vídeo e a decodificar são feitas em software na CPU. Se uma GPU estiver disponível, o bot poderá tirar proveito dela para sua própria renderização gráfica, por exemplo, se o bot estiver usando um mecanismo gráfico 3D.
- A instância da VM que hospeda o bot de mídia em tempo real deve ter pelo menos 2 núcleos de CPU. Para o Azure, uma máquina virtual da série Dv2 é recomendada. Para outros tipos de VM do Azure, um sistema com quatro CPUs virtuais (vCPU) é o tamanho mínimo necessário. Informações detalhadas sobre tipos de VM do Azure estão disponíveis na documentação [do Azure.](/azure/virtual-machines/windows/sizes-general) 

## <a name="code-sample"></a>Exemplo de código

Exemplos de bots de mídia hospedados pelo aplicativo são os seguinte:

| **Exemplo de nome** | **Descrição** | **Graph** |
|------------|-------------|-----------|
| Exemplo de mídia local | Exemplos que ilustram diferentes cenários de mídia local. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples) |
| Exemplo de mídia remota | Exemplos que ilustram diferentes cenários de mídia remota. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/RemoteMediaSamples) |

## <a name="see-also"></a>Confira também

- [Graph Chamando documentação do SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
- Os bots exigem mais capacidade de computação e largura de banda de rede do que bots de mensagens e incorrem em custos operacionais significativamente maiores. Um desenvolvedor de bot de mídia em tempo real deve medir cuidadosamente a escalabilidade do bot e garantir que o bot não aceite mais chamadas simultâneas do que pode gerenciar. Um bot habilitado para vídeo pode sustentar apenas uma ou duas sessões de mídia simultâneas por núcleo de CPU se usar os formatos de vídeo RGB24 ou NV12 brutos.
- No momento, a Plataforma de Mídia em Tempo Real não tira proveito de nenhuma GPU (Unidades de Processamento de Gráficos) disponíveis na VM para codificação de vídeo H.264 descarramento ou decodificação. Em vez disso, a codificação de vídeo e a decodificar são feitas em software na CPU. Se uma GPU estiver disponível, o bot tirará proveito dela para sua própria renderização gráfica, por exemplo, se o bot estiver usando um mecanismo gráfico 3D.
- A instância da VM que hospeda o bot de mídia em tempo real deve ter pelo menos 2 núcleos de CPU. Para o Azure, uma máquina virtual da série Dv2 é recomendada. Para outros tipos de VM do Azure, um sistema com 4 CPUs virtuais (vCPU) é o tamanho mínimo necessário. Para obter mais informações sobre tipos de VM do Azure, consulte [Documentação do Azure](/azure/virtual-machines/windows/sizes-general).

A próxima seção fornece exemplos que ilustram diferentes cenários de mídia local.

## <a name="samples-and-additional-resources"></a>Exemplos e recursos adicionais

- [Exemplo de aplicativos](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
- [Graph a documentação do SDK](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Formatos de mídia suportados](~/resources/media-formats.md)
