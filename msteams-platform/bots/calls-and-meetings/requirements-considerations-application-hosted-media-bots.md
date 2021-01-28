---
title: Requisitos e considerações para bots de mídia hospedados pelo aplicativo
description: Entenda os requisitos e as considerações importantes relacionados à criação de bots de mídia hospedados pelo aplicativo para o Microsoft Teams.
ms.topic: conceptual
keywords: vm do Azure server do Windows Media hospedado pelo aplicativo
ms.date: 11/16/2018
ms.openlocfilehash: bf75b7f689713f16cb3ff9ff4313ab829b5cc2d6
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014485"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Requisitos e considerações para bots de mídia hospedados pelo aplicativo

Nem todas as diretrizes para o desenvolvimento de mensagens e bots IVR (Resposta interativa de voz) se aplica igualmente à criação de bots de mídia hospedados pelo aplicativo. Este artigo descreve alguns dos requisitos e considerações importantes para desenvolver e executar um bot de mídia hospedado pelo aplicativo.

> [!NOTE]
> Como a Plataforma de Mídia em Tempo Real da Microsoft para Bots está na visualização do desenvolvedor, as orientações neste artigo estão sujeitas a alterações.

## <a name="application-hosted-media-bot-development-requires-cnet-and-windows-server"></a>O desenvolvimento de bots de mídia hospedados pelo aplicativo requer C#/.NET e Windows Server

- Um bot de mídia hospedado pelo aplicativo requer a biblioteca .NET (disponível aqui para acessar os fluxos de mídia de áudio e vídeo, e o bot deve ser implantado em uma máquina do Windows Server (ou o sistema operacional convidado do Windows Server no `Microsoft.Graph.Communications.Calls.Media` Azure).[](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) Portanto, o bot deve ser desenvolvido em C# e o .NET Framework padrão e implantado no Microsoft Azure. Não é possível usar APIs do tipo C++ ou Node.js para acessar mídia em tempo real e o .NET Core não é suportado para um bot de mídia hospedado pelo aplicativo.

- Um bot de mídia hospedado pelo aplicativo pode ser hospedado em um dos seguintes ambientes de serviço do Azure:
  - Serviço de Nuvem.
  - Service Fabric com VMSS (Conjuntos de Escala de Máquina Virtual).
  - Máquina Virtual (VM) Infraestrutura como Serviço (IaaS).  
  
- Um bot de mídia hospedado pelo aplicativo não pode ser implantado como um Azure Web App.

- Um bot de mídia hospedado pelo aplicativo deve estar em execução em uma versão recente da `Microsoft.Graph.Communications.Calls.Media` biblioteca .NET. O bot deve usar a versão mais recente disponível do pacote [NuGet](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)ou uma versão que não tem mais de três meses. As versões mais antigas da biblioteca serão preterida e podem não funcionar após alguns meses. Manter `Microsoft.Graph.Communications.Calls.Media` a biblioteca atualizada garantirá a melhor interoperabilidade entre o bot e o Microsoft Teams.

## <a name="real-time-media-calls-stay-on-the-machine-where-they-were-created"></a>As chamadas de mídia em tempo real permanecem no computador onde foram criadas

- Uma chamada de mídia em tempo real é fixada à instância da máquina virtual (VM) que aceitou ou iniciou a chamada. A mídia de uma chamada ou reunião do Microsoft Teams fluirá para essa instância da VM, e a mídia que o bot envia de volta para o Microsoft Teams também deve se originar dessa VM.
- Se houver chamadas de mídia em tempo real em andamento quando a VM for interrompida, essas chamadas serão encerradas abruptamente. Se o bot tiver conhecimento prévio do desligamento pendente da VM, ele poderá tentar encerrar as chamadas "normalmente".

## <a name="application-hosted-media-bots-must-be-directly-accessible-on-the-internet"></a>Os bots de mídia hospedados pelo aplicativo devem estar diretamente acessíveis na Internet

- Cada instância de VM que hospeda um bot de mídia hospedado pelo aplicativo no Azure deve estar diretamente acessível pela Internet usando um ILPIP (endereço IP público de nível de instância).
  - Para obter e configurar um ILPIP para um Serviço de Nuvem do Azure, consulte a visão geral do IP público de nível de [instância (clássico).](/azure/virtual-network/virtual-networks-instance-level-public-ip)
  - Para configurar um ILPIP para um conjunto de escala de VM, consulte [IPv4 público por máquina virtual.](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine)
- O serviço que hospeda um bot de mídia hospedado pelo aplicativo também deve configurar cada instância de VM com uma porta voltada para o público que mapeia para a instância específica.
  - Para um Serviço de Nuvem do Azure, isso requer um ponto de extremidade de entrada de instância; Confira [Habilitar comunicação para instâncias de função no Azure.](/azure/cloud-services/cloud-services-enable-communication-role-instances)
  - Para um Conjunto de Escala de VM, uma regra NAT no balanceador de carga deve ser configurada; confira [Redes virtuais e máquinas virtuais no Azure.](/azure/virtual-machines/windows/network-overview)
- Os bots de mídia hospedados pelo aplicativo não são suportados pelo Emulador da Estrutura de Bot.

## <a name="scalability-and-performance-considerations"></a>Considerações sobre escalabilidade e desempenho

- Os bots de mídia hospedados pelo aplicativo exigem mais capacidade de computação e rede (largura de banda) do que os bots de mensagens e podem incorrer em custos operacionais significativamente maiores. Um desenvolvedor de bot de mídia em tempo real deve medir cuidadosamente a escalabilidade do bot e garantir que o bot não aceite mais chamadas simultâneas do que pode gerenciar. Um bot habilitado para vídeo pode sustentar apenas uma ou duas sessões de mídia simultâneas por núcleo da CPU (se estiver usando os formatos de vídeo RGB24 ou NV12 "brutos").
- No momento, a Plataforma de Mídia em Tempo Real não aproveita as Unidades de Processamento gráfico (GPU) disponíveis na VM para decodificar/decodificar vídeo H.264. Em vez disso, a codificação e a decodificada de vídeo são feitas no software da CPU. Se uma GPU estiver disponível, o bot poderá tirar proveito dela para sua própria renderização de elementos gráficos (por exemplo, se o bot estiver usando um mecanismo gráfico 3D).
- A instância da VM que hospeda o bot de mídia em tempo real deve ter pelo menos 2 núcleos de CPU. Para o Azure, é recomendável uma máquina virtual de série Dv2. Para outros tipos de VM do Azure, um sistema com 4 CPUs virtuais (vCPU) é o tamanho mínimo necessário. Informações detalhadas sobre tipos de VM do Azure estão disponíveis na [documentação do Azure.](/azure/virtual-machines/windows/sizes-general)

## <a name="samples-and-additional-resources"></a>Exemplos e recursos adicionais

- [Aplicativos de exemplo](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
- [Documentação do SDK de Chamada do Graph](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
