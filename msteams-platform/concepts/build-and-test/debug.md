---
title: Escolher uma instalação para testar e depurar seu aplicativo
description: Descreve opções para testar e depurar Microsoft Teams aplicativos
keywords: teams executar aplicativos de depuração
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 5d358e7f37972f1b0954f2c4c5f6a892aeff8d8f4f08b4be22d4ae0215acbebe
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57707313"
---
# <a name="choose-a-setup-to-test-and-debug-your-microsoft-teams-app"></a>Escolha uma instalação para testar e depurar seu Microsoft Teams app

Microsoft Teams aplicativos contêm um ou mais recursos e as maneiras de executar ou mesmo hospedá-los são diferentes. Para depuração, use uma das seguintes maneiras:

* **Puramente local**: para bots, você pode testar sua experiência no bot Emulator. Para outros conteúdos, você pode executar localmente em seu navegador e resolver conteúdo por `http://localhost` meio de .
* **Hospedado localmente** em Teams : isso envolve a execução local do aplicativo no túnel de software e [a](~/concepts/build-and-test/apps-package.md) criação de um pacote para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Teams. Isso permite que você execute e depure facilmente seu aplicativo dentro do Teams cliente.
* **Hospedado na nuvem em Teams**: isso realmente simula o suporte ao nível de produção para um Teams app. Ele envolve carregar sua solução para seu servidor externo acessível ou provedor de nuvem de escolha e [criar](~/concepts/build-and-test/apps-package.md) um pacote para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Teams.

Execute a experiência do seu próprio computador para testes puramente locais ou Teams local. Ao fazer isso, você pode compilar e executar em seu ambiente de desenvolvimento integrado e aproveitar ao máximo as técnicas, como pontos de interrupção e depuração de etapas. 

> [!NOTE]
> Para depuração e teste em escala de produção, recomendamos que você siga suas próprias diretrizes da empresa para garantir que você seja capaz de dar suporte a testes, preparação e implantação por meio de seus próprios processos.

Use vários manifestos e pacotes para manter a separação entre serviços de produção e desenvolvimento. Por exemplo, você pode optar por registrar bots de desenvolvimento e produção separados e criar pacotes apropriados para carregar no seu ambiente de teste. Também recomendamos que você carregue e teste seu pacote de produção antes de enviar seu aplicativo para publicação em nossa loja de aplicativos ou distribuir aos clientes.

## <a name="purely-local"></a>Puramente local

> [!NOTE]
> Executar o bot localmente não lhe dá acesso Teams funcionalidade do aplicativo ou funções de bot específicas Teams como chamadas de lista e outras funcionalidades específicas do canal. Além disso, alguns recursos são permitidos pela Estrutura de Bot no bot Emulator que podem não funcionar durante a execução no Microsoft Teams.

Seu bot pode ser executado no bot Emulator. Isso permite testar algumas das principais lógicas do bot, ver um layout aproximado de mensagens e realizar testes simples. Veja a seguir as etapas:

1. Execute o código localmente.
2. Iniciar o bot Emulator e definir a URL:
   * Node.js: `http://localhost:3978/api/messages`
   * .NET/C#: `http://localhost:3979/api/messages`
3. Deixe a ID do aplicativo Microsoft e a senha do aplicativo Microsoft em branco, para corresponder às variáveis de ambiente padrão.

## <a name="locally-hosted"></a>Hospedado localmente

Microsoft Teams é um produto totalmente baseado em nuvem, exige que todos os serviços que acessa sejam disponibilizados publicamente usando pontos de extremidade HTTPS. Portanto, para permitir que seu aplicativo funcione dentro Teams, você precisa publicar o código na nuvem de sua escolha ou tornar nossa instância de execução local acessível externamente. Podemos fazer o último com o software de tunelamento.

Embora você possa usar qualquer ferramenta de sua escolha, usamos e recomendamos [ngrok](https://ngrok.com/download), que cria uma URL externamente acessível para uma porta que você abre localmente em seu computador. 

**Para configurar o ngrok em preparação para executar seu aplicativo Microsoft Teams localmente**

1. Vá para o diretório onde você ngrok.exe instalado em um aplicativo de terminal. Talvez você queira adicioná-lo como uma variável de caminho para evitar essa etapa.
2. Execute, por exemplo, `ngrok http 3978 --host-header=localhost:3978` ou substitua o número da porta conforme necessário.
   Isso inicia o ngrok para listar na porta especificada. Em troca, ele fornece uma URL de endereço externo válida enquanto o ngrok está em execução.

> [!NOTE]
> Se você parar e reiniciar o ngrok, a URL será mudada.

Para usar o ngrok em seu projeto com base nos recursos que você está usando, você deve substituir todas as referências de URL em seu arquivo de código, configuração e manifest.jsno arquivo para usar esse ponto de extremidade de URL.

Para bots registrados no Microsoft Bot Framework, atualize o ponto de extremidade de mensagens do bot para usar esse novo ponto de extremidade ngrok. Por exemplo, `https://2d1224fb.ngrok.io/api/messages`. Você pode validar que o ngrok está funcionando testando a resposta do bot na janela de chat test do portal da Estrutura de Bot. Novamente, como o emulador, esse teste não permite que você acesse Teams funcionalidade específica.

> [!NOTE]
> Para atualizar o ponto de extremidade de mensagens para um bot, você deve usar a Estrutura de Bot. Selecione seu bot [em sua lista de bots na Estrutura de Bots.](https://dev.botframework.com/bots) Você não precisa migrar seu bot para Microsoft Azure. Você também pode atualizar seu ponto de extremidade de mensagens por meio [do App Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="cloud-hosted"></a>Hospedado na nuvem

Você pode usar qualquer serviço enderecável externamente para hospedar seu código de desenvolvimento e produção e seus pontos de extremidade HTTPS. Não há expectativa de que seus recursos residam no mesmo serviço. Exigimos que todos os domínios sejam acessados Microsoft Teams aplicativos listados no [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) objeto no `manifest.json` arquivo.

> [!NOTE]
> Para garantir um ambiente seguro, seja explícito sobre o domínio exato e os subdomas que você faz referência e esses domínios devem estar em seu controle. Por exemplo, `*.azurewebsites.net` não é recomendável, no `contoso.azurewebsites.net` entanto é recomendável.

## <a name="load-and-run-your-experience"></a>Carregar e executar sua experiência

Para carregar e executar sua experiência em Microsoft Teams, você precisa criar um pacote e carregá-lo em Teams. Para saber mais, confira:

* [Crie o pacote para seu Microsoft Teams app](~/concepts/build-and-test/apps-package.md).
* [Upload seu aplicativo em Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"] 
> [Adicione dados de teste ao seu ambiente](~/concepts/build-and-test/test-data.md)

