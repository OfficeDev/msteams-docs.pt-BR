---
title: Escolhendo uma configuração para testar e depurar seu aplicativo
description: Descreve opções para testar e depurar aplicativos Microsoft Teams
keywords: equipes executar aplicativos de depuração
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 1f11834ad83e8bea7e4114d25d022df2f62c1700
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565155"
---
# <a name="choose-a-setup-to-test-and-debug-your-microsoft-teams-app"></a>Escolha uma configuração para testar e depurar seu aplicativo de Microsoft Teams

Microsoft Teams aplicativos contêm um ou mais recursos e as maneiras de executá-los ou até mesmo hospedá-los são diferentes. Para depuração, use uma das seguintes maneiras:

* **Puramente local**: Para bots, você pode testar sua experiência no Bot Emulator. Para outros conteúdos, você pode executar localmente em seu navegador e abordar conteúdo através `http://localhost` de .
* **Hospedado localmente em Teams**: Isso envolve executar o aplicativo localmente em software de tunelamento e [criar um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) em Teams. Isso permite que você execute e depure seu aplicativo facilmente dentro do Teams cliente.
* **Hospedado em nuvem em Teams**: Isso realmente simula o suporte ao nível de produção de um aplicativo Teams. Ele envolve o upload de sua solução para o seu servidor ou provedor de nuvem de acesso externo e a criação de [um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) em Teams.

Execute a experiência a partir do seu próprio computador para testes de Teams puramente locais ou locais. Ao fazer isso, você pode compilar e executar dentro do seu ambiente de desenvolvimento integrado e aproveitar ao máximo técnicas, como pontos de interrupção e depuração de passos. 

> [!NOTE]
> Para depuração e teste em escala de produção, recomendamos que você siga as diretrizes da sua própria empresa para garantir que você seja capaz de suportar testes, estadiamento e implantação através de seus próprios processos.

Use vários manifestos e pacotes para manter a separação entre os serviços de produção e desenvolvimento. Por exemplo, você pode optar por registrar bots separados de desenvolvimento e produção e criar pacotes apropriados para carregá-los em seu ambiente de teste. Também recomendamos que você carregue e teste seu pacote de produção antes de enviar seu aplicativo para publicar em nossa loja de aplicativos ou distribuir aos clientes.

## <a name="purely-local"></a>Puramente local

> [!NOTE]
> Executar o bot localmente não lhe dá acesso a Teams funcionalidade do aplicativo ou funções de bot específicas Teams, como chamadas de lista e outras funcionalidades específicas do canal. Além disso, alguns recursos são permitidos pelo Bot Framework no Bot Emulator que pode não funcionar ao ser executado em Microsoft Teams.

Seu bot pode ser executado dentro do Bot Emulator. Isso permite testar parte da lógica central do bot, ver um layout áspero de mensagens e realizar testes simples. A seguir estão as etapas:

1. Execute o código localmente.
2. Inicie o Emulador de Bot e defina a URL:
   * Node.js: `http://localhost:3978/api/messages`
   * .NET/C#: `http://localhost:3979/api/messages`
3. Deixe o ID do aplicativo da Microsoft e a senha do aplicativo da Microsoft em branco, para corresponder às variáveis de ambiente padrão.

## <a name="locally-hosted"></a>Hospedado localmente

Microsoft Teams é um produto inteiramente baseado em nuvem, requer que todos os serviços que acessa estejam disponíveis publicamente usando pontos finais HTTPS. Portanto, para permitir que seu aplicativo funcione dentro de Teams, você precisa publicar o código na nuvem de sua escolha ou tornar nossa instância de execução local acessível externamente. Podemos fazer o último com software de tunelamento.

Embora você possa usar qualquer ferramenta de sua escolha, usamos e recomendamos [ngrok](https://ngrok.com/download), que cria uma URL externamente endereçada para uma porta que você abre localmente em sua máquina. 

**Para configurar ngrok em preparação para executar seu aplicativo de Microsoft Teams localmente**

1. Vá para o diretório onde você ngrok.exe instalado em um aplicativo de terminal. Você pode querer adicioná-lo como uma variável de caminho para evitar este passo.
2. Execute, por `ngrok http 3978 --host-header=localhost:3978` exemplo, ou substitua o número da porta conforme necessário.
   Isso lança ngrok para listar na porta que você especificar. Em troca, ele lhe dá uma URL externamente endereçada válida enquanto ngrok estiver sendo executado.

> [!NOTE]
> Se você parar e reiniciar ngrok, a URL será alterado.

Para usar o ngrok em seu projeto com base nos recursos que você está usando, você deve substituir todas as referências de URL em seu código, configuração e manifest.jsno arquivo para usar este ponto final de URL.

Para bots registrados no Microsoft Bot Framework, atualize o ponto final de mensagens do bot para usar este novo ponto final ngrok. Por exemplo, `https://2d1224fb.ngrok.io/api/messages`. Você pode validar que o ngrok está trabalhando testando a resposta do bot na janela de bate-papo do portal Bot Framework. Novamente, como o emulador, este teste não permite que você acesse Teams funcionalidade específica.

> [!NOTE]
> Para atualizar o ponto final de mensagens para um bot, você deve usar o Bot Framework. Selecione seu bot na [sua lista de bots no Bot Framework](https://dev.botframework.com/bots). Você não precisa migrar seu bot para Microsoft Azure. Você também pode atualizar seu ponto final de mensagens através [do App Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="cloud-hosted"></a>Hospedado na nuvem

Você pode usar qualquer serviço endereçado externamente para hospedar seu código de desenvolvimento e produção e seus pontos finais HTTPS. Não há expectativa de que suas capacidades residam no mesmo serviço. Exigimos que todos os domínios sejam acessados a partir de seus aplicativos de Microsoft Teams listados no [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) objeto no `manifest.json` arquivo.

> [!NOTE]
> Para garantir um ambiente seguro, seja explícito sobre o domínio exato e os subdomínios que você faz referência e esses domínios devem estar em seu controle. Por exemplo, `*.azurewebsites.net` não é recomendado, no entanto `contoso.azurewebsites.net` é recomendado.

## <a name="load-and-run-your-experience"></a>Carregue e execute sua experiência

Para carregar e executar sua experiência dentro de Microsoft Teams, você precisa criar um pacote e carregá-lo em Teams. Para mais informações, confira:

* [Crie o pacote para o seu aplicativo Microsoft Teams](~/concepts/build-and-test/apps-package.md).
* [Upload seu aplicativo em Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"] 
> [Adicione dados de teste ao seu ambiente](~/concepts/build-and-test/test-data.md)

