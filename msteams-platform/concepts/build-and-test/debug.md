---
title: Escolhendo uma configuração para testar e depurar seu aplicativo
description: Neste módulo, conheça as opções para testar e depurar aplicativos do Microsoft Teams no ambiente local e hospedado na nuvem.
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: b064fb4ef06576251a91a4727a84bb4519d4d352
ms.sourcegitcommit: d8183bad448990f7c79b1956a6c9761c27712b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2022
ms.locfileid: "67452350"
---
# <a name="choose-a-test-setup-and-debug-your-teams-app"></a>Escolha uma configuração de teste e depure seu aplicativo teams

Os aplicativos do Microsoft Teams contêm um ou mais recursos e as maneiras de executar ou até mesmo hospedá-los são diferentes. Para depuração, use uma das seguintes maneiras:

* **Puramente local**: para bots, você pode testar sua experiência no Bot Emulator. Para outros conteúdos, você pode executar localmente em seu navegador e endereçar o conteúdo por meio de `http://localhost`.
* **Hospedado localmente no Teams**: envolve executar o aplicativo localmente no software de encapsulamento e [criar um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Teams. Isso permite que você execute e depure facilmente seu aplicativo no cliente do Teams.
* **Hospedado na nuvem no Teams**: simula verdadeiramente o suporte de nível de produção para um aplicativo do Teams. Envolve o upload de sua solução para seu servidor ou provedor de nuvem acessível externamente e [criação de um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Teams.

Execute a experiência em seu próprio computador para testes puramente locais ou locais do Teams. Ao fazer isso, você pode compilar e executar em seu ambiente de desenvolvimento integrado e aproveitar ao máximo as técnicas, como pontos de interrupção e depuração de etapas.

> [!NOTE]
> Para depuração e teste em escala de produção, recomendamos que você siga as diretrizes de sua própria empresa para garantir que possa dar suporte a testes, preparação e implantação por meio de seus próprios processos.

Use vários manifestos e pacotes para manter a separação entre os serviços de produção e desenvolvimento. Por exemplo, você pode optar por registrar bots de desenvolvimento e produção separados e criar pacotes apropriados para carregá-los em seu ambiente de teste. Também recomendamos que você carregue e teste seu pacote de produção antes de enviar seu aplicativo para publicação em nossa loja de aplicativos ou distribuição para clientes.

## <a name="purely-local"></a>Puramente local

> [!NOTE]
> A execução do bot localmente não dá acesso à funcionalidade do aplicativo Teams ou às funções de bot específicas do Teams, como chamadas de lista e outras funcionalidades específicas do canal. Além disso, alguns recursos são permitidos pelo Bot Framework no Bot Emulator que podem não funcionar durante a execução no Teams.

Seu bot pode ser executado no emulador de bot. Isso permite que você teste parte da lógica principal do bot, veja um layout aproximado de mensagens e execute testes simples. Seguem os passos:

1. Execute o código localmente.
2. Inicie o emulador de bot e defina a URL:
   * Node.js: `http://localhost:3978/api/messages`
   * .NET/C#: `http://localhost:3979/api/messages`
3. Deixe a ID do aplicativo Microsoft e a senha do aplicativo Microsoft em branco para corresponder às variáveis ​​de ambiente padrão.

## <a name="locally-hosted"></a>Hospedado localmente

O Teams é um produto totalmente baseado em nuvem, ele exige que todos os serviços que acessam sejam disponibilizados publicamente usando pontos de extremidade HTTPS. Portanto, para permitir que seu aplicativo funcione no Teams, você precisa publicar o código na nuvem de sua escolha ou tornar nossa instância local em execução acessível externamente. Podemos fazer o último com software de tunelamento.

Embora você possa usar qualquer ferramenta de sua escolha, usamos e recomendamos o [ngrok](https://ngrok.com/download), que cria um URL endereçável externamente para uma porta que você abre localmente em seu computador.

Para configurar o ngrok na preparação para executar o aplicativo Teams localmente, siga estas etapas:

1. Acesse o diretório onde você tem o ngrok.exe instalado em um aplicativo de terminal. Você pode querer adicioná-lo como uma variável de caminho para evitar esta etapa.
2. Execute, por exemplo, `ngrok http 3978 --host-header=localhost:3978` ou substitua o número da porta conforme necessário.
   Isso inicia o ngrok para listar na porta que você especificar. Em troca, ele fornece uma URL endereçável externamente válida enquanto o ngrok estiver em execução.

> [!NOTE]
> Se você parar e reiniciar o ngrok, a URL será alterada.

Para usar o ngrok em seu projeto com base nos recursos que você está usando, você deve substituir todas as referências de URL em seu código, configuração e arquivo manifest.json para usar esse ponto de extremidade de URL.

Para bots registrados no Microsoft Bot Framework, atualize o ponto de extremidade de mensagens do bot para usar esse novo ponto de extremidade ngrok. Por exemplo, `https://2d1224fb.ngrok.io/api/messages`. Você pode validar se o ngrok está funcionando testando a resposta do bot na janela de chat de teste do portal do Bot Framework. Novamente, como o emulador, esse teste não permite que você acesse a funcionalidade específica do Teams.

> [!NOTE]
> Para atualizar o ponto de extremidade de mensagens para um bot, você deve usar o Bot Framework. Selecione seu bot em [sua lista de bots no Bot Framework](https://dev.botframework.com/bots). Você não precisa migrar seu bot para o Microsoft Azure. Você também pode atualizar seu ponto de extremidade de mensagens por meio [do Portal do Desenvolvedor para Teams](~/concepts/build-and-test/teams-developer-portal.md).

## <a name="cloud-hosted"></a>Hospedado na nuvem

Você pode usar qualquer serviço endereçável externamente para hospedar seu código de desenvolvimento e produção e seus pontos de externamente HTTPS. Não há nenhuma expectativa de que seus recursos residam no mesmo serviço. Exigimos que todos os domínios sejam acessados de seus aplicativos do Teams listados no [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) objeto no `manifest.json` arquivo.

> [!NOTE]
> Para garantir um ambiente seguro, seja claro sobre o domínio e os subdomínios exatos que você referencia e esses domínios devem estar em seu controle. Por exemplo, `*.azurewebsites.net` não é recomendado, mas `contoso.azurewebsites.net` é recomendado.

## <a name="load-and-run-your-experience"></a>Carregar e executar a experiência

Para carregar e executar sua experiência no Teams, você precisa criar um pacote e carregá-lo no Teams. Para saber mais, confira:

* [Criar o pacote para o aplicativo Microsoft Teams](~/concepts/build-and-test/apps-package.md).
* [Carregar seu aplicativo no Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md).

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Adicione dados de teste ao seu ambiente](~/concepts/build-and-test/test-data.md)

## <a name="see-also"></a>Confira também

* [Testar e depurar seu bot localmente com o IDE](../../bots/how-to/debug/locally-with-an-ide.md#test-and-debug-your-bot-locally-with-ide)
* [Guias do DevTools para o Microsoft Teams](../../tabs/how-to/developer-tools.md)
