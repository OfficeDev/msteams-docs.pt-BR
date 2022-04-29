---
title: Escolhendo uma configuração para testar e depurar seu aplicativo
description: Descreve opções para testar e depurar aplicativos do Microsoft Teams no ambiente local e hospedado na nuvem.
keywords: as equipes executam aplicativos de depuração host hospedado na nuvem local
ms.localizationpriority: high
ms.topic: conceptual
ms.openlocfilehash: 957d673bfd3f7bbfaab05fd035e8de809fd66983
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111532"
---
# <a name="choose-a-setup-to-test-and-debug-your-microsoft-teams-app"></a>Escolher uma configuração para testar e depurar seu aplicativo Microsoft Teams

Os aplicativos do Microsoft Teams contêm um ou mais recursos e as maneiras de executá-los ou até mesmo hospedá-los são diferentes. Para depuração, use uma das seguintes maneiras:

* **Puramente local**: para bots, você pode testar sua experiência no Bot Emulator. Para outros conteúdos, você pode executar localmente em seu navegador e endereçar o conteúdo por meio de `http://localhost`.
* **Hospedado localmente no Teams**: envolve executar o aplicativo localmente no software de encapsulamento e [criar um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Teams. Isso permite que você execute e depure facilmente seu aplicativo no cliente do Teams.
* **Hospedado na nuvem no Teams**: simula verdadeiramente o suporte de nível de produção para um aplicativo do Teams. Envolve o upload de sua solução para seu servidor ou provedor de nuvem acessível externamente e [criação de um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Teams.

Execute a experiência em seu próprio computador para testes puramente locais ou locais do Teams. Ao fazer isso, você pode compilar e executar em seu ambiente de desenvolvimento integrado e aproveitar ao máximo as técnicas, como pontos de interrupção e depuração de etapas.

> [!NOTE]
> Para depuração e teste em escala de produção, recomendamos que você siga as diretrizes de sua própria empresa para garantir que possa dar suporte a testes, preparação e implantação por meio de seus próprios processos.

Use vários manifestos e pacotes para manter a separação entre os serviços de produção e desenvolvimento. Por exemplo, você pode optar por registrar bots de desenvolvimento e produção separados e criar pacotes apropriados para carregá-los em seu ambiente de teste. Também recomendamos que você carregue e teste seu pacote de produção antes de enviar seu aplicativo para publicação em nossa loja de aplicativos ou distribuição para clientes.

## <a name="purely-local"></a>Puramente local

> [!NOTE]
> A execução do bot localmente não dá acesso à funcionalidade do aplicativo Teams ou às funções de bot específicas do Teams, como chamadas de lista e outras funcionalidades específicas do canal. Além disso, alguns recursos são permitidos pelo Bot Framework no Bot Emulator que podem não funcionar ao serem executados no Microsoft Teams.

Seu bot pode ser executado no emulador de bot. Isso permite que você teste parte da lógica principal do bot, veja um layout aproximado de mensagens e execute testes simples. Seguem os passos:

1. Execute o código localmente.
2. Inicie o emulador de bot e defina a URL:
   * Node.js: `http://localhost:3978/api/messages`
   * .NET/C#: `http://localhost:3979/api/messages`
3. Deixe a ID do aplicativo Microsoft e a senha do aplicativo Microsoft em branco para corresponder às variáveis ​​de ambiente padrão.

## <a name="locally-hosted"></a>Hospedado localmente

O Microsoft Teams é um produto totalmente baseado em nuvem, que exige que todos os serviços acessados ​​estejam disponíveis publicamente usando pontos de extremidade HTTPS. Portanto, para permitir que seu aplicativo funcione no Teams, você precisa publicar o código na nuvem de sua escolha ou tornar nossa instância local em execução acessível externamente. Podemos fazer o último com software de tunelamento.

Embora você possa usar qualquer ferramenta de sua escolha, usamos e recomendamos o [ngrok](https://ngrok.com/download), que cria um URL endereçável externamente para uma porta que você abre localmente em seu computador.

Para configurar o ngrok em preparação para executar seu aplicativo Microsoft Teams localmente, siga estas etapas:

1. Acesse o diretório onde você tem o ngrok.exe instalado em um aplicativo de terminal. Você pode querer adicioná-lo como uma variável de caminho para evitar esta etapa.
2. Execute, por exemplo, `ngrok http 3978 --host-header=localhost:3978` ou substitua o número da porta conforme necessário.
   Isso inicia o ngrok para listar na porta que você especificar. Em troca, ele fornece uma URL endereçável externamente válida enquanto o ngrok estiver em execução.

> [!NOTE]
> Se você parar e reiniciar o ngrok, a URL será alterada.

Para usar o ngrok em seu projeto com base nos recursos que você está usando, você deve substituir todas as referências de URL em seu código, configuração e arquivo manifest.json para usar esse ponto de extremidade de URL.

Para bots registrados no Microsoft Bot Framework, atualize o ponto de extremidade de mensagens do bot para usar esse novo ponto de extremidade ngrok. Por exemplo, `https://2d1224fb.ngrok.io/api/messages`. Você pode validar se o ngrok está funcionando testando a resposta do bot na janela de chat de teste do portal do Bot Framework. Novamente, como o emulador, este teste não permite que você acesse a funcionalidade específica do Teams.

> [!NOTE]
> Para atualizar o ponto de extremidade de mensagens para um bot, você deve usar o Bot Framework. Selecione seu bot em [sua lista de bots no Bot Framework](https://dev.botframework.com/bots). Você não precisa migrar seu bot para o Microsoft Azure. Você também pode atualizar seu ponto de extremidade de mensagens por meio [App Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="cloud-hosted"></a>Hospedado na nuvem

Você pode usar qualquer serviço endereçável externamente para hospedar seu código de desenvolvimento e produção e seus pontos de externamente HTTPS. Não há expectativa de que seus recursos residam no mesmo serviço. Exigimos que todos os domínios sejam acessados ​​de seus aplicativos do Microsoft Teams listados no objeto [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) no arquivo `manifest.json`.

> [!NOTE]
> Para garantir um ambiente seguro, seja explícito sobre o domínio e os subdomínios exatos aos quais você faz referência e esses domínios devem estar sob seu controle. Por exemplo, `*.azurewebsites.net` não é recomendado, mas `contoso.azurewebsites.net` é recomendado.

## <a name="load-and-run-your-experience"></a>Carregar e executar a experiência

Para carregar e executar sua experiência no Microsoft Teams, você precisa criar um pacote e carregá-lo no Teams. Para saber mais, confira:

* [Criar o pacote para o aplicativo Microsoft Teams](~/concepts/build-and-test/apps-package.md).
* [Carregar seu aplicativo no Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Adicione dados de teste ao seu ambiente](~/concepts/build-and-test/test-data.md)

## <a name="see-also"></a>Confira também

[Testar e depurar seu bot localmente](../../bots/how-to/debug/locally-with-an-ide.md#test-and-debug-your-bot-locally)
