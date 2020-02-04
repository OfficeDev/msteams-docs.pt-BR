---
title: Executar e depurar seu aplicativo
description: Descreve as etapas a serem executadas para executar e depurar aplicativos do Microsoft Teams
keywords: Teams executar depurar aplicativos
ms.topic: conceptual
ms.openlocfilehash: f7f49038617e0a6b8729df7fa53b97b63b3b3158
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672818"
---
# <a name="run-and-debug-your-microsoft-teams-app"></a>Executar e depurar seu aplicativo Microsoft Teams

Os aplicativos do Microsoft Teams podem conter um ou mais recursos, e as maneiras de executá-los ou mesmo hospedá-los podem ser diferentes. Quando se trata de depuração, em geral, temos as seguintes maneiras de executar o aplicativo Microsoft Teams:

* **Puramente local**&emsp;para bots, você pode testar sua experiência no emulador de bot. Para outro conteúdo, você pode executar localmente no seu navegador e lidar com o `http://localhost`conteúdo por meio do.
* **Hospedado localmente, no Teams**&emsp;, isso envolve a execução local com o software de encapsulamento e a [criação de um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Microsoft Teams. Isso permite que você execute e depure facilmente o aplicativo no cliente Teams.
* **Hospedado na nuvem, no Teams** Isso verdadeiramente simula (ou é) o suporte de nível de produção para um aplicativo do teams. Ele envolve carregar sua solução para seu servidor acessível externamente ou provedor de nuvem de escolha (recomendamos o Azure, naturalmente) e [criando um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Teams.

Para testes de equipes puramente locais ou locais, você executa a experiência do seu próprio computador. Isso permite que você realmente compile e execute dentro do seu IDE e tire o máximo proveito dessas técnicas como pontos de interrupção e depuração de etapa. Para depuração e teste de escala de produção, recomendamos que você siga as diretrizes de sua empresa para garantir que você possa dar suporte ao teste, preparação e implantação por meio de seus próprios processos.

Em geral, recomendamos que você use vários manifestos e pacotes para permitir que você mantenha a separação entre serviços de produção e desenvolvimento. Por exemplo, você pode optar por registrar bots de desenvolvimento e produção separados e criar pacotes apropriados para carregá-los no seu ambiente de teste. Recomendamos também carregar e testar seu pacote de produção antes de enviar o aplicativo para publicação em nossa loja de aplicativos ou distribuir para os clientes.

## <a name="purely-local"></a>Puramente local

> [!NOTE]
> A execução desse modo não dá acesso à funcionalidade do aplicativo do teams ou às funções de bot específicas da equipe, como chamadas de lista e outros recursos específicos do canal. Além disso, alguns recursos podem ser permitidos pela estrutura de bot no emulador de bot que podem não funcionar durante a execução no Microsoft Teams.

Seu bot pode ser executado no emulador de bot. Isso permite testar algumas das principais lógicas do bot, ver um layout áspero de mensagens e realizar testes simples. Estas são as etapas:

* Executar o código localmente
* Inicie o emulador de bot e defina a URL:
  * Node. js:`http://localhost:3978/api/messages`
  * .NET/C#:`http://localhost:3979/api/messages`
* Deixe em branco a ID do aplicativo Microsoft e a senha do Microsoft App para corresponder às variáveis de ambiente padrão.

## <a name="locally-hosted"></a>Hospedado localmente

Como o Microsoft Teams é um produto totalmente baseado em nuvem, ele exige todos os serviços que ele acessa para estar disponível publicamente usando pontos de extremidade HTTPS. Portanto, para permitir que seu aplicativo funcione no Teams, você precisa publicar o código na nuvem de sua escolha ou tornar nossa instância em execução externamente acessível. Podemos fazer o último com o software de encapsulamento.

Embora você possa usar qualquer ferramenta de escolha, usamos e recomendamos o [ngrok](https://ngrok.com/download), que cria uma URL endereçável externamente para uma porta que você abre localmente no seu computador. Para configurar o ngrok em preparação para executar seu aplicativo do Microsoft Teams localmente:

* Em um aplicativo de terminal, vá para o diretório onde você tem o ngrok. exe instalado. Talvez você queira adicioná-lo como uma variável de caminho para evitar esta etapa.
* Executar, por exemplo, `ngrok http 3978 --host-header=localhost:3978`ou substituir o número da porta, conforme necessário.

Isso inicia o ngrok para escutar na porta que você especificar. Em retorno, ele fornece uma URL endereçável externamente, válida por enquanto o ngrok está em execução.

> [!NOTE]
> Se você parar e reiniciar o ngrok, a URL será alterada.

Para usar o ngrok em seu projeto e dependendo dos recursos que você está usando, você deve substituir todas as referências de URL em seu código, configuração e/ou arquivo manifest. JSON para usar este ponto de extremidade de URL.

Por exemplo, para bots registrados no Microsoft bot Framework, atualize o ponto de extremidade de mensagens do bot para usar esse novo ponto de extremidade do ngrok. Por exemplo, `https://2d1224fb.ngrok.io/api/messages`. Você pode validar que o ngrok está funcionando testando a resposta do bot na janela de chat de teste do portal da estrutura do bot. (Novamente, como o emulador, esse teste não permite acessar a funcionalidade específica da equipe.)

> [!NOTE]
> Para atualizar o ponto de extremidade de mensagens de um bot, você deve usar a estrutura do bot. Clique no bot na [sua lista de bots no bot Framework](https://dev.botframework.com/bots). Você não precisa migrar o bot para o Microsoft Azure. Você também pode atualizar seu ponto de extremidade de mensagens por meio do [app Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="cloud-hosted"></a>Hospedado na nuvem

Você pode usar qualquer serviço endereçável externamente para hospedar seu código de desenvolvimento e de produção e seus pontos de extremidade HTTPS. Não há expectativas de que seus recursos residem no mesmo serviço. Exigimos que todos os domínios que estão sendo acessados a partir de seus aplicativos [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) do Microsoft Teams sejam listados no objeto no arquivo manifest. JSON.

> [!NOTE]
> Para garantir um ambiente seguro, seja explícito sobre o domínio exato e os subdomínios que você referencia, e esses domínios devem estar no seu controle. Por exemplo, `*.azurewebsites.net` não seria recomendável, mas `contoso.azurewebsites.net` Sim.

## <a name="loading-and-running"></a>Carregando e executando

Em geral, para carregar e executar sua experiência no Microsoft Teams, você precisa criar um pacote e carregá-lo no Teams, usando as seguintes orientações:

* [Criar o pacote para seu aplicativo do Microsoft Teams](~/concepts/build-and-test/apps-package.md)
* [Carregar seu aplicativo no Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md)
