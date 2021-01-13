---
title: Escolhendo uma configuração para testar e depurar seu aplicativo
description: Descreve as opções para testar e depurar aplicativos do Microsoft Teams
keywords: equipes executar aplicativos de depuração
ms.topic: conceptual
ms.openlocfilehash: ea851a0d3ecf3ec87093bcc095050190a282c25e
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797796"
---
# <a name="choosing-a-setup-to-test-and-debug-your-microsoft-teams-app"></a>Escolher uma configuração para testar e depurar seu aplicativo microsoft Teams

Os aplicativos do Microsoft Teams podem conter um ou mais recursos, e as maneiras de executar ou até mesmo hospedá-los podem ser diferentes. Quando se trata de depuração, em geral, temos as seguintes maneiras de executar seu aplicativo microsoft Teams:

* **Puramente local** &emsp; Para bots, você pode testar sua experiência no Emulador de Bot. Para outros conteúdos, você pode executar localmente em seu navegador e endereço conteúdo por meio de `http://localhost` .
* **Hospedado localmente, no Teams** &emsp; Isso envolve a execução local com o tunelamento de software [e a criação de um pacote](~/concepts/build-and-test/apps-package.md) para [carregar](~/concepts/deploy-and-publish/apps-upload.md) no Teams. Isso permite que você execute e depure facilmente seu aplicativo no cliente do Teams.
* **Hospedado na nuvem, no Teams** Isso realmente simula (ou é) o suporte no nível de produção para um aplicativo do Teams. Isso envolve carregar [sua](~/concepts/build-and-test/apps-package.md) solução para seu servidor acessível externamente ou provedor de nuvem de escolha (recomendamos o Azure, claro) e criar um pacote para carregar [no](~/concepts/deploy-and-publish/apps-upload.md) Teams.

Para testes puramente locais ou locais do Teams, execute a experiência em seu próprio computador. Isso permite que você realmente compile e execute em seu IDE e aproveite ao máximo essas técnicas como pontos de interrupção e depuração de etapas. Para depuração e teste em escala de produção, recomendamos que você siga suas próprias diretrizes da empresa para garantir que você seja capaz de dar suporte a testes, preparação e implantação por meio de seus próprios processos.

Em geral, recomendamos que você use vários manifestos e pacotes para permitir que você mantenha a separação entre serviços de produção e desenvolvimento. Por exemplo, você pode optar por registrar bots de desenvolvimento e produção separados e criar pacotes apropriados para carregar em seu ambiente de teste. Também recomendamos que você carregue e teste seu pacote de produção antes de enviar seu aplicativo para publicação na loja de aplicativos ou distribuir aos clientes.

## <a name="purely-local"></a>Puramente local

> [!NOTE]
> Executar dessa forma não lhe dá acesso à funcionalidade do aplicativo Teams ou a funções de bot específicas do Teams, como chamadas de lista de participantes e outras funcionalidades específicas do canal. Além disso, alguns recursos podem ser permitidos pela Estrutura de Bot no Emulador de Bot que pode não funcionar durante a execução no Microsoft Teams.

Seu bot pode ser executado no Emulador de Bot. Isso permite que você teste parte da lógica principal do bot, veja um layout aproximado das mensagens e realize testes simples. Estas são as etapas:

* Executar o código localmente
* Iniciar o Emulador de Bot e definir a URL:
  * Node.js: `http://localhost:3978/api/messages`
  * .NET/C#: `http://localhost:3979/api/messages`
* Deixe a ID do aplicativo da Microsoft e a senha do aplicativo da Microsoft em branco para corresponder às variáveis de ambiente padrão.

## <a name="locally-hosted"></a>Hospedado localmente

Como o Microsoft Teams é um produto totalmente baseado em nuvem, ele exige que todos os serviços que ele acessa sejam disponibilizados publicamente usando pontos de extremidade HTTPS. Portanto, para permitir que seu aplicativo funcione no Teams, você precisa publicar o código na nuvem de sua escolha ou tornar nossa instância de execução local externamente acessível. Podemos fazer o último com o software de túnel.

Embora você possa usar qualquer ferramenta de escolha, usamos e recomendamos [ngrok](https://ngrok.com/download), que cria uma URL externamente acessível para uma porta que você abre localmente em seu computador. Para configurar o ngrok em preparação para executar seu aplicativo Microsoft Teams localmente:

* Em um aplicativo de terminal, vá para o diretório onde você ngrok.exe instalado. Talvez você queira adicioná-lo como uma variável de caminho para evitar esta etapa.
* Execute, por exemplo, `ngrok http 3978 --host-header=localhost:3978` ou substitua o número da porta conforme necessário.

Isso inicia o ngrok para ouvir a porta que você especificar. Em troca, ele oferece uma URL externamente acessível, válida enquanto o ngrok está em execução.

> [!NOTE]
> Se você parar e reiniciar o ngrok, a URL será mudada.

Para usar o ngrok em seu projeto e, dependendo dos recursos que você está usando, você deve substituir todas as referências de URL em seu código, configuração e/ou manifest.jsno arquivo para usar esse ponto de extremidade de URL.

Por exemplo, para bots registrados no Microsoft Bot Framework, atualize o ponto de extremidade de mensagens do bot para usar esse novo ponto de extremidade ngrok. Por exemplo, `https://2d1224fb.ngrok.io/api/messages`. Você pode validar se o ngrok está funcionando testando a resposta de bot na janela de bate-papo de teste do portal do Bot Framework. (Novamente, como o emulador, esse teste não permite que você acesse a funcionalidade específica do Teams.)

> [!NOTE]
> Para atualizar o ponto de extremidade de mensagens para um bot, você deve usar o Bot Framework. Clique em seu bot em [sua lista de bots no Bot Framework.](https://dev.botframework.com/bots) Você não precisa migrar seu bot para o Microsoft Azure. Você também pode atualizar o ponto de extremidade de mensagens por meio [do App Studio.](~/concepts/build-and-test/app-studio-overview.md)

## <a name="cloud-hosted"></a>Hospedado na nuvem

Você pode usar qualquer serviço enderecável externamente para hospedar seu código de desenvolvimento e produção e seus pontos de extremidade HTTPS. Não há expectativa de que seus recursos residam no mesmo serviço. Exigimos que todos os domínios que estão sendo acessados a partir de seus aplicativos do Microsoft Teams sejam listados no objeto [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) no manifest.jsno arquivo.

> [!NOTE]
> Para garantir um ambiente seguro, seja explícito sobre o domínio e os sub-domínios exatos que você referencia, e esses domínios devem estar no seu controle. Por exemplo, `*.azurewebsites.net` não seria recomendável, `contoso.azurewebsites.net` mas seria.

## <a name="loading-and-running"></a>Carregando e executando

Em geral, para carregar e executar sua experiência no Microsoft Teams, você precisa criar um pacote e carregá-lo no Teams, usando as seguintes diretrizes:

* [Criar o pacote para o aplicativo Microsoft Teams](~/concepts/build-and-test/apps-package.md)
* [Carregar seu aplicativo no Microsoft Teams](~/concepts/deploy-and-publish/apps-upload.md)
