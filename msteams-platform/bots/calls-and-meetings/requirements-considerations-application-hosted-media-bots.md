---
title: Requisitos e considerações para bots de mídia hospedados em aplicativos
description: Entenda os requisitos e considerações importantes e as considerações de escalabilidade e desempenho relacionadas à criação de bots de mídia hospedados em aplicativos para o Microsoft Teams usando exemplos e exemplos de código.
ms.topic: conceptual
ms.localizationpriority: high
keywords: VM do Azure do Windows Server hospedada por aplicativo
ms.date: 11/16/2018
ms.openlocfilehash: 35ad133d898b53538f51c2ae4c699cd19368f9af
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111980"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Requisitos e considerações para bots de mídia hospedados em aplicativos

Um bot de mídia hospedado por aplicativo requer a [`Microsoft.Graph.Communications.Calls.Media` biblioteca .NET](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) para acessar os fluxos de mídia de áudio e vídeo. O bot deve ser implantado em uma máquina local do Windows Server ou em um sistema operacional (SO) convidado do Windows Server no Azure.

> [!NOTE]
>
> * A orientação para o desenvolvimento de bots de mensagens e Resposta Interativa de Voz (IVR) não se aplica completamente à criação de bots de mídia hospedados em aplicativos.
> * Como a plataforma de mídia em tempo real da Microsoft para bots está na versão prévia do desenvolvedor, as orientações deste documento estão sujeitas a alterações.

## <a name="c-or-net-and-windows-server-for-development"></a>C# ou .NET e Windows Server para desenvolvimento

Um bot de mídia hospedado por aplicativo requer o seguinte:

* O bot deve ser desenvolvido em C# e no .NET Framework padrão e implantado no Microsoft Azure. Você não pode usar APIs C++ ou Node.js para acessar mídia em tempo real e o .NET Core não é compatível com um bot de mídia hospedado por aplicativo.

* O bot pode ser hospedado em um dos seguintes ambientes de serviço do Azure:
  * Serviço de Nuvem.
  * Service Fabric com VMSS (Conjuntos de Dimensionamento de Máquinas Virtuais).
  * VM (Máquina Virtual) iaaS (infraestrutura como serviço).  
  
* O bot não pode ser implantado como um aplicativo Web do Azure.

* O bot deve estar sendo executado em uma versão recente da biblioteca .NET `Microsoft.Graph.Communications.Calls.Media`. O bot deve usar a versão mais recente disponível do [pacote NuGet](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) ou uma versão que não tenha mais de três meses. Versões mais antigas da biblioteca estão obsoletas e não funcionam após alguns meses. Manter a biblioteca `Microsoft.Graph.Communications.Calls.Media` atualizada garante a melhor interoperabilidade entre o bot e o Microsoft Teams.

A próxima seção fornece detalhes sobre onde as chamadas de mídia em tempo real estão localizadas.

## <a name="real-time-media-calls-stay-where-they-are-created"></a>As chamadas de mídia em tempo real permanecem onde foram criadas

As chamadas de mídia em tempo real permanecem no computador em que foram criadas. Uma chamada de mídia em tempo real é fixada na instância de máquina virtual (VM) que aceitou ou iniciou a chamada. A mídia de uma chamada ou reunião do Microsoft Teams flui para essa instância de VM e a mídia que o bot envia de volta para o Microsoft Teams também deve ser originada dessa VM. Se houver chamadas de mídia em tempo real em andamento quando a VM for interrompida, essas chamadas serão encerradas abruptamente. Se o bot tiver conhecimento prévio do desligamento pendente da VM, ele poderá encerrar as chamadas.

A próxima seção fornece detalhes sobre acessibilidade de bots de mídia hospedados em aplicativos.

## <a name="application-hosted-media-bots-accessible-on-the-internet"></a>Bots de mídia hospedados em aplicativos acessíveis na Internet

Os bots de mídia hospedados em aplicativos devem estar diretamente acessíveis na Internet. Esses bots devem incluir os seguintes recursos:

* Cada instância de VM que hospeda um bot de mídia hospedado por aplicativo no Azure deve ser acessível diretamente da Internet usando um endereço IP público no nível da instância (ILPIP).
  * Para obter e configurar um ILPIP para um Serviço de Nuvem do Azure, consulte [visão geral clássica de IP público em nível de instância](/azure/virtual-network/virtual-networks-instance-level-public-ip).
  * Para configurar um ILPIP para um Conjunto de Dimensionamento de VM, consulte [IPv4 público por computador](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine).
* O serviço que hospeda um bot de mídia hospedado por aplicativo também deve configurar cada instância de VM com uma porta voltada para o público que mapeia para a instância específica.
  * Para um Serviço de Nuvem do Azure, isso requer um ponto de extremidade de entrada de instância. Para obter mais informações, consulte [habilitar comunicação para instâncias de função no Azure](/azure/cloud-services/cloud-services-enable-communication-role-instances).
  * Para um conjunto de dimensionamento de VM, uma regra NAT no balanceador de carga deve ser configurada. Para obter mais informações, consulte [redes virtuais e máquinas virtuais no Azure](/azure/virtual-machines/windows/network-overview).

* Os bots de mídia hospedados no aplicativo não são compatíveis com o Bot Framework Emulator.

A próxima seção fornece detalhes sobre as considerações de escalabilidade e desempenho de bots de mídia hospedados em aplicativos.

## <a name="scalability-and-performance-considerations"></a>Considerações sobre escalabilidade e desempenho

Os bots de mídia hospedados no aplicativo exigem as seguintes considerações de escalabilidade e desempenho:

* Os bots de mídia hospedados em aplicativos exigem mais capacidade de computação e rede (largura de banda) do que os bots de mensagens e podem incorrer em custos operacionais significativamente mais altos. Um desenvolvedor de bot de mídia em tempo real deve medir cuidadosamente a escalabilidade do bot e garantir que o bot não aceite mais chamadas simultâneas do que pode gerenciar. Um bot habilitado para vídeo pode ser capaz de sustentar apenas uma ou duas sessões de mídia simultâneas por núcleo de CPU (se estiver usando os formatos de vídeo "raw" RGB24 ou NV12).
* Atualmente, a Plataforma de Mídia em Tempo Real não aproveita nenhuma Unidade de Processamento Gráfico (GPU) disponível na VM para descarregar a codificação/decodificação de vídeo H.264. Em vez disso, a codificação e a decodificação de vídeo são feitas em software na CPU. Se uma GPU estiver disponível, o bot poderá aproveitá-la para sua própria renderização gráfica, por exemplo, se o bot estiver usando um mecanismo gráfico 3D.
* A instância de VM que hospeda o bot de mídia em tempo real deve ter pelo menos 2 núcleos de CPU. Para o Azure, uma máquina virtual da série Dv2 é recomendada. Para outros tipos de VM do Azure, um sistema com quatro CPUs virtuais (vCPU) é o tamanho mínimo necessário. Informações detalhadas sobre os tipos de VM do Azure estão disponíveis na [documentação do Azure](/azure/virtual-machines/windows/sizes-general).

## <a name="code-sample"></a>Exemplo de código

Os exemplos de bots de mídia hospedados pelo aplicativo são os seguintes:

| **Nome de exemplo** | **Descrição** | **Graph** |
|------------|-------------|-----------|
| Amostra de mídia local | Exemplos que ilustram diferentes cenários de mídia local. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples) |
| Exemplo de mídia remota | Exemplos que ilustram diferentes cenários de mídia remota. | [View](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/RemoteMediaSamples) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Formatos de mídia suportados](~/resources/media-formats.md)

## <a name="see-also"></a>Confira também

* [Documentação do SDK de Chamada de Gráfico](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
* Os bots exigem mais capacidade de computação e largura de banda de rede do que os bots de mensagens e incorrem em custos operacionais significativamente mais altos. Um desenvolvedor de bot de mídia em tempo real deve medir cuidadosamente a escalabilidade do bot e garantir que o bot não aceite mais chamadas simultâneas do que ele pode gerenciar. Um bot habilitado para vídeo pode sustentar apenas uma ou duas sessões de mídia simultâneas por núcleo de CPU se estiver usando os formatos de vídeo RGB24 ou NV12 brutos.
* Atualmente, a Plataforma de Mídia em Tempo Real não aproveita nenhuma Unidade de Processamento Gráfico (GPU) disponível na VM para descarregar a codificação ou decodificação de vídeo H.264. Em vez disso, a codificação e a decodificação de vídeo são feitas em software na CPU. Se uma GPU estiver disponível, o bot a aproveitará para sua própria renderização de gráficos, por exemplo, se o bot estiver usando um mecanismo de gráficos 3D.
* A instância de VM que hospeda o bot de mídia em tempo real deve ter pelo menos 2 núcleos de CPU. Para o Azure, uma máquina virtual da série Dv2 é recomendada. Para outros tipos de VM do Azure, um sistema com 4 CPUs virtuais (vCPU) é o tamanho mínimo necessário. Para obter mais informações sobre os tipos de VM do Azure, consulte a [documentação do Azure](/azure/virtual-machines/windows/sizes-general).

A próxima seção fornece exemplos que ilustram diferentes cenários de mídia local.

## <a name="samples-and-additional-resources"></a>Exemplos e recursos adicionais

* [Aplicativos de exemplo](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
* [Documentação do SDK de chamada de gráfico](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
