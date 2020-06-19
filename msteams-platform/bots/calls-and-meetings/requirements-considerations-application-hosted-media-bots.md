---
title: Requisitos e considerações para bots de mídia hospedados por aplicativos
description: Compreenda os requisitos e as considerações importantes relacionadas à criação de bots de mídia hospedados por aplicativos para o Microsoft Teams.
keywords: mídia hospedada pelo aplicativo do Windows Server Azure VM
ms.date: 11/16/2018
ms.openlocfilehash: f5b721edacb11e867d05c8213b74036cb51f419c
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "44800946"
---
# <a name="requirements-and-considerations-for-application-hosted-media-bots"></a>Requisitos e considerações para bots de mídia hospedados por aplicativos

Nem todas as orientações para o desenvolvimento de mensagens e bots de resposta de voz interativa (IVR) se aplicam igualmente à criação de bots de mídia hospedados por aplicativos. Este artigo descreve alguns dos requisitos e considerações importantes para o desenvolvimento e a execução de um bot de mídia hospedado por aplicativo.

> [!NOTE]
> Como a plataforma de mídia em tempo real da Microsoft para bots está no Developer Preview, as orientações deste artigo estão sujeitas a alterações.

## <a name="application-hosted-media-bot-development-requires-cnet-and-windows-server"></a>O desenvolvimento de bot de mídia hospedado pelo aplicativo requer o/.NET C# e o Windows Server

- Um bot de mídia hospedado por aplicativo requer a `Microsoft.Graph.Communications.Calls.Media` biblioteca do .net ([disponível aqui](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/) para acessar os fluxos de mídia de áudio e vídeo, e o bot deve ser implantado em uma máquina Windows Server (ou em um sistema operacional convidado do Windows Server no Azure). Portanto, o bot deve ser desenvolvido em C# e no .NET Framework padrão e implantado no Microsoft Azure. Você não pode usar as APIs do C++ ou do Node.js para acessar a mídia em tempo real e o .NET Core não é suportado para um bot de mídia hospedado por aplicativo.

- Um bot de mídia hospedado por aplicativo pode ser hospedado em um dos seguintes ambientes de serviço do Azure:
  - Serviço de nuvem.
  - Service Fabric com conjuntos de escalas de máquina virtual (VMSS).
  - Infraestrutura como serviço (IaaS) Virtual Machine (VM).  
  
- Um bot de mídia hospedado por aplicativo não pode ser implantado como um aplicativo Web do Azure.

- Um bot de mídia hospedado pelo aplicativo deve estar em execução em uma versão recente da `Microsoft.Graph.Communications.Calls.Media` biblioteca do .net. O bot deve usar a versão mais recente disponível do [pacote NuGet](https://www.nuget.org/packages/Microsoft.Graph.Communications.Calls.Media/)ou uma versão que não tenha mais de três meses. Versões mais antigas da biblioteca serão preteridas e podem não funcionar após alguns meses. Manter a `Microsoft.Graph.Communications.Calls.Media` biblioteca atualizada garantirá a melhor interoperabilidade entre o bot e o Microsoft Teams.

## <a name="real-time-media-calls-stay-on-the-machine-where-they-were-created"></a>Chamadas de mídia em tempo real permanecem no computador onde foram criadas

- Uma chamada de mídia em tempo real está fixada à instância da máquina virtual (VM) que aceitou ou iniciou a chamada. A mídia de uma chamada ou reunião do Microsoft Teams fluirá para essa instância da VM, e a mídia que o bot envia de volta para o Microsoft Teams também deve se originar da VM.
- Se houver chamadas de mídia em tempo real em andamento quando a VM for interrompida, essas chamadas serão encerradas abruptamente. Se o bot tiver conhecimento prévio do encerramento da VM pendente, ele poderá tentar "executar" corretamente as chamadas.

## <a name="application-hosted-media-bots-must-be-directly-accessible-on-the-internet"></a>Os bots de mídia hospedados por aplicativos devem ser acessíveis diretamente na Internet

- Cada instância da VM que hospeda um bot de mídia hospedado pelo aplicativo no Azure deve ser diretamente acessível pela Internet usando um endereço IP público (ILPIP) de nível de instância.
  - Para obter e configurar um ILPIP para um serviço de nuvem do Azure, consulte [visão geral de IP público de nível de instância (clássico)](/azure/virtual-network/virtual-networks-instance-level-public-ip).
  - Para configurar um ILPIP para um conjunto de escalas de VM, confira [IPv4 público por máquina virtual](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-networking#public-ipv4-per-virtual-machine).
- O serviço que hospeda um bot de mídia hospedado pelo aplicativo também deve configurar cada instância da VM com uma porta voltada para o público que mapeia para a instância específica.
  - Para um serviço de nuvem do Azure, isso requer um ponto de extremidade de entrada de instância; consulte [habilitar a comunicação para instâncias de função no Azure](/azure/cloud-services/cloud-services-enable-communication-role-instances).
  - Para um conjunto de escala da VM, uma regra NAT no balanceador de carga deve ser configurada; consulte [redes virtuais e máquinas virtuais no Azure](/azure/virtual-machines/windows/network-overview).
- Os bots de mídia hospedados por aplicativos não são suportados pelo emulador da estrutura bot.

## <a name="scalability-and-performance-considerations"></a>Considerações sobre escalabilidade e desempenho

- Os bots de mídia hospedados por aplicativos exigem mais capacidade de computação e de rede (largura de banda) do que os bots de mensagens e podem incorrer em custos operacionais significativamente maiores. Um desenvolvedor de bot de mídia em tempo real deve medir cuidadosamente a escalabilidade do bot e garantir que o bot não aceite mais chamadas simultâneas do que pode gerenciar. Um bot habilitado para vídeo pode ser capaz de sustentar apenas uma ou duas sessões de mídia simultâneas por núcleo de CPU (se estiver usando os formatos de vídeo "RAW" RGB24 ou NV12).
- A plataforma de mídia em tempo real não aproveita atualmente qualquer unidade de processamento de elementos gráficos (GPU) disponível na VM para desativar a codificação/decodificação de vídeo H. 264. Em vez disso, a codificação e a decodificação de vídeo são feitas no software na CPU. Se uma GPU estiver disponível, o bot poderá tirar proveito dela para sua própria renderização gráfica (por exemplo, se o bot estiver usando um mecanismo de gráfico 3D).
- A instância VM que hospeda o bot de mídia em tempo real deve ter pelo menos 2 núcleos de CPU. Para o Azure, uma máquina virtual Dv2 é recomendada. Para outros tipos do Azure VM, um sistema com 4 CPUs virtuais (vCPU) é o tamanho mínimo necessário. Informações detalhadas sobre os tipos do Azure VM estão disponíveis na [documentação do Azure](/azure/virtual-machines/windows/sizes-general).

## <a name="samples-and-additional-resources"></a>Exemplos e recursos adicionais

- [Aplicativos de amostra](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/master/Samples/V1.0Samples/LocalMediaSamples)
- [Documentação do SDK de chamada de gráfico](https://microsoftgraph.github.io/microsoft-graph-comms-samples/docs/)
