---
title: Criar uma página de detalhes do aplicativo excelente
description: Descreve os requisitos para a página de detalhes do aplicativo
ms.topic: reference
keywords: teams publish store office publishing policy AppSource content Metadata screenshot screenshot logo description app name icons short description
ms.openlocfilehash: e7513fbb4ed2e56844931d1a587b6ee062e014a4
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634541"
---
# <a name="build-a-great-app-details-page"></a>Criar uma página de detalhes do aplicativo excelente

A página de detalhes apresenta a primeira impressão do seu aplicativo aos usuários. Cada elemento da sua página de detalhes pode ser usado para transmitir sua visão e downloads de unidade — considere como você deseja mostrar seu aplicativo em um espaço limitado. Aqui estão algumas dicas e truques para ajudar você a envolver seus usuários antes mesmo de instalar seu aplicativo.

> [!NOTE]
> Certifique-se de que as informações do aplicativo seguem nossas diretrizes do [AppSource para criar uma listagem de loja eficaz.](/office/dev/store/create-effective-office-store-listings)

## <a name="app-name"></a>Nome do aplicativo

> [!div class="checklist"]
>
> * O nome de um aplicativo desempenha uma função crítica na forma como os usuários o descobrem na loja de aplicativos AppSource. O nome curto do aplicativo é exibido na página de detalhes.
>* O nome do aplicativo deve refletir seu aplicativo sem qualquer referência aos produtos Microsoft ou Microsoft.
>

> **Observação**: se seu aplicativo for uma parceria oficial com a Microsoft, o nome do aplicativo de terceiros precisará ser primeiro, por exemplo, *Conector do Salesforce para o Microsoft Teams.*

> [!div class="checklist"]
>
>* Use esses recursos para orientação:

* [Guia de nome do aplicativo](#app-name)
* [Diretrizes de marca e marca da Microsoft](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)

**Do's:**

* Escolha um nome simples e memorável que indica o que seu aplicativo faz.
* Seja distinto.
* Se necessário, use referências do Microsoft 365 em vez do Office 365.

**Não:**

* Não omita espaços, tenha uma ocorrência incorreta ou contenha erros de idioma no nome do aplicativo.
* Não use termos genéricos ou nomes semelhantes aos aplicativos existentes.
* Não use "Teams", "Microsoft", nomes de produtos da Microsoft existentes/futuros ou "aplicativo" no nome do aplicativo.
* Não use parênteses para incluir produtos da Microsoft, por exemplo, Seu Nome do Aplicativo *(para o Microsoft Teams)*.

![Exibição da loja de nomes de aplicativo](../../../../assets/images/store-detail-page/AppName-02.png)

![App name App Studio view](../../../../assets/images/store-detail-page/AppName-01.png)

## <a name="color-icon"></a>Ícone de cor

Este é um dos primeiros elementos que os usuários veem. Ele deve ser atraente e atraente ao rolar pela loja de aplicativos. Certifique-se de que ele dá uma boa primeira impressão e também comunica a imagem e a finalidade da sua marca. AppSource tem mais dicas sobre [como criar uma identidade visual consistente.](/office/dev/store/create-effective-office-store-listings#create-a-consistent-visual-identity)

![Exibição do armazenamento de ícones de aplicativo](~/assets/images/store-detail-page/AppIcon-02.png)

![Ícone do aplicativo Exibição do App Studio](~/assets/images/store-detail-page/AppIcon-01.png)

**Não:**

* Seu ícone não deve imitar produtos protegidos por direitos autorais que você não possui.
* Seu ícone não deve ser semelhante a qualquer produto/marca da Microsoft.

## <a name="outline-icon"></a>Ícone de contorno

Esse ícone é usado para extensões de mensagens fixadas e quando seu aplicativo é exibido à esquerda do Teams. Consulte [diretrizes de design para o ícone de estrutura de estrutura de estrutura.](../../../../concepts/build-and-test/apps-package.md#outline-icon)

![Exibição do armazenamento de contornos do ícone do aplicativo ](../../../../assets/images/store-detail-page/AppIconOutline-02.png)
 ![ Exibição de ícone do aplicativo App Studio](../../../../assets/images/store-detail-page/AppIconOutline-01.png)

**Não:**

* Seu ícone não deve imitar produtos protegidos por direitos autorais que você não possui.
* Seu ícone não deve ser semelhante a qualquer produto/marca da Microsoft.

## <a name="short-description"></a>Descrição breve

Este é um resumo conciso do seu aplicativo. Ela deve ser original, interessante e direcionada ao seu público-alvo. O ideal é tentar descrever sua solução e seu valor para seus usuários em uma frase.

**Do's:**

* Fale primeiro as informações mais importantes.
* Inclua palavras-chave que os clientes provavelmente procurarão.
* Se você precisar mencionar o Microsoft Teams, a primeira menção do Microsoft Teams deve ser escrita na íntegra como *Microsoft Teams*. Se o Teams for mencionado novamente na mesma descrição, o nome poderá ser reduzido para *Teams*.
* Quaisquer referências à Microsoft ou ao Microsoft Teams podem fazer parte da descrição e devem seguir os padrões e diretrizes de marca da Microsoft.
* Todas as descrições devem ser gramaticalmente corretas sem erros de idioma.
* Evite o uso desnecessário de maiúsculas, por exemplo, informando "Usuários" em vez de "usuários".

**Não:**

* Não repita o título.
* Não abreviar a Microsoft para "MS" ou "MSFT".
* Não use jargão ou terminologia especializada — você não pode supor que os usuários saibam o que procurar.
* Evite referências desnecessárias aos nomes de produtos da Microsoft, a menos que seja absolutamente necessário.
* Não indique ou insinue que o aplicativo é uma oferta da Microsoft.
* Não use nomes de marca protegidos por direitos autorais que você não possui.
* Não use "para o Teams" em um nome curto.

![Exibição de armazenamento de Descrição Curta](~/assets/images/store-detail-page/ShortDescription-02.png)

Aqui está uma exibição no [App Studio:](https://aka.ms/InstallTeamsAppStudio)

![Exibição do App Studio de Descrição Curta](~/assets/images/store-detail-page/ShortDescription-01.png)

## <a name="long-description"></a>Descrição longa

> [!div class="checklist"]
>
>* Isso fornece uma interessante narração realçando os principais recursos da sua solução, os problemas que ela resolve e o público-alvo. Desenhe em sua audiência com a primeira frase comunicando os recursos exclusivos do aplicativo. Sua descrição deve ter menos de 4.000 caracteres; a maioria dos usuários só lerá entre 300 e 500 palavras.
>* O que é permitido?

* `<your_app>`  "funciona com o Microsoft Teams"
* `<for users>`  "trabalhando com o Microsoft Teams"
* `<for tasks>`  "dentro do Microsoft Teams"
* `<an app>`  "para o Microsoft Teams"
* `<your_app>`  "integra-se ao Microsoft Teams"
* "... integrado ao Microsoft Teams"
* "... built on..."
* "... é executado em..."
* "... habilitado por..."
* "... desenvolvido para..."
* "... projetado para..."

> **Observação**: Os termos acima também se aplicam ao uso do Microsoft 365. O Office 365 agora é chamado de Microsoft 365. Atualize as descrições do aplicativo para refletir isso.

>[!IMPORTANT]
> Copie com precisão as descrições que você escreveu na entrada do AppSource para o manifesto do aplicativo — os valores devem corresponder. O Microsoft Teams usará apenas as descrições fornecidas no manifesto do aplicativo.

**Do's:**

* Use [a formatação Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) para iluminar sua descrição.  
* List features to aid readers in scanning your description.
* Use voz ativa e fale diretamente com os usuários.
* Use pontos de marcador para listar seus recursos.
* Inclua uma ajuda ou um link de suporte para que os usuários saibam como falar com você se eles têm dúvidas.
* Certifique-se de que a primeira menção do Microsoft Teams seja escrita na íntegra como "*Microsoft Teams*". Se o Teams for mencionado novamente posteriormente na mesma descrição, o nome poderá ser reduzido para "*Teams*".
* Quaisquer referências à Microsoft ou ao Microsoft Teams (somente se necessário) podem fazer parte da descrição longa e devem seguir os padrões de marca e diretrizes da Microsoft.
* Todas as descrições devem ser gramaticalmente corretas sem erros de idioma.
* Evite o uso desnecessário de maiúsculas para termos em sua descrição (exemplo: informando "Usuários" em vez de "usuários".
* Evite acrônimos.
* Certifique-se de chamar limitações, dependência da conta, configuração configurada, atualizações futuras em versões ou quaisquer restrições de uso

>[!NOTE]
> O Microsoft Teams dá suporte à seguinte sintaxe markdown:  
> **Links**. `[title](url/address/here)`.  
>**Imagens** `![alt text](url/address/here)` . .  
> **Negrito**. `**bold text**`   `__bold text__`.  
> **Itálico**. `*italicized text*`  `_italicized text`.  
>**[Listas ordenadas](https://www.markdownguide.org/basic-syntax/#ordered-lists)**<br>
>`1. first` 
<br>` 1. second ` 
<br>`1.third`<br>
>**[Lista semordenagem](https://www.markdownguide.org/basic-syntax/#unordered-lists)**<br>
` - short` <br>`- bulleted` <br>`- list`<br>
>**Newline**. Use um `\n` caractere para designar uma linha nova.
 >**Escape.** Use uma invertida em linha para escapar de caracteres especiais. `\*asterisk`.

**Exemplo no formato Markdown**

|Formato de markdown para |Formato markdown |Texto exibido|
|:---------|:---------------|:-------------|
|Link  |` [App name guide](#app-name)`| [Guia de nome do aplicativo](#app-name) |
|Image |` ![App long description store view](~/assets/images/store-detail-page/LongDescription-02.png)`| ![Exibição do armazenamento de descrição longa do aplicativo](~/assets/images/store-detail-page/LongDescription-02.png)|
|Negrito |` **HR Tools**` | **Ferramentas de RH**  |
|Itálico |`*HR Tools*` |*Ferramentas de RH*|
|Newline |` HR Tools provide wide range of solutions that help your organization to manage day-to-day HR activities effectively. <br> No more flipping through paper records or juggling among 5 different apps.` |As Ferramentas de RH fornecem uma ampla variedade de soluções que ajudam sua organização a gerenciar as atividades diárias de RH de forma eficaz. <br>  Não mais passar pelos registros de papel ou fazer malabarismo entre 5 aplicativos diferentes.|
|Escape|`\*Payroll tools that help you manage your payroll and tax documents.` |\*Ferramentas de folha de pagamento que ajudam você a gerenciar sua folha de pagamento e documentos fiscais. 

**Não:**

* Não coloque muitas palavras-chave em sua descrição — isso distrai e não ajuda na descoberta do aplicativo.
* Não use "*Teams*" ou "*Microsoft Teams*" em um nome curto.
* Evite referências desnecessárias aos nomes de produtos da Microsoft, a menos que seja absolutamente necessário.
* Não indique que o aplicativo é uma oferta da Microsoft.
* Não use nomes de marca protegidos por direitos autorais que você não possui.
* Não use o seguinte idioma, a menos que o aplicativo tenha passado por um processo de certificação oficial:

  * "... certificado para..."
  * "... powered by..."

* Não abreviar "Microsoft" para "MS" ou "MSFT" — escreva a Microsoft na íntegra.
* Nenhuma parte da descrição ou metadados pode indicar o aplicativo como uma oferta oficial da Microsoft.
* Os parceiros não podem usar ou imitar qualquer marca da Microsoft ou usar o nome de qualquer produto ou serviço da Microsoft no lema ou no tagline.
* O logotipo não deve representar o aplicativo incorretamente como um recurso/produto oficial da Microsoft ou imitar qualquer um dos produtos Da Microsoft existentes ou futuros.

![Exibição do armazenamento de descrição longa do aplicativo](~/assets/images/store-detail-page/LongDescription-02.png)

Aqui está uma exibição no [App Studio:](https://aka.ms/InstallTeamsAppStudio)

![App long description App Studio view](~/assets/images/store-detail-page/LongDescription-01.png)

## <a name="screenshots"></a>Capturas de tela

As capturas de tela carregadas no [Partner Center](https://partner.microsoft.com) são exibidas no [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) e na listagem do aplicativo no cliente do Teams. Eles fornecem uma visualização visual do seu aplicativo juntamente com a descrição do aplicativo.
Você pode fornecer de uma a cinco capturas de tela formatadas como arquivos .png, .jpg ou .gif. Screenshots should be 1366 x 768 pixels with a maximum size of 1024 KB.

**Do's:**

* Concentre-se em realçar todos os recursos do aplicativo.
* O conteúdo deve representar com precisão seu aplicativo.
* O texto deve ser bem preenchido sem ser excessivo.
* Você pode cercar suas capturas de tela com uma cor de plano de fundo e adicionar conteúdo de marketing semelhante ao [exemplo do Freshdesk;](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) no entanto, as dimensões não serão apenas da captura de tela, mas incluirão a imagem geral.

<img width="800px" alt="Freshdesk screenshot" src="../../../../assets/images/freshdesk.png" />

**Não:**

* Não mostre dispositivos específicos, como telefones ou laptops.
* Não mostre nenhum cromado/interface do usuário de fora do aplicativo.
* Não capture nenhuma interface do usuário do Teams ou navegador em suas capturas de tela.
* Não inclua mock-ups que reflitam imprecisamente a interface do usuário real de seus aplicativos, como mostrar seu site em vez da guia Do Teams.

Para obter mais práticas recomendadas, *consulte*: Criar imagens efetivas do Armazenamento do [AppSource.](/office/dev/store/craft-effective-appsource-store-images)

## <a name="videos"></a>Vídeos

Se uma imagem vale mil palavras, então um vídeo vale milhares de imagens. Os vídeos são a maneira mais eficaz de comunicar os benefícios de usar seu aplicativo. Ele será colocado na frente de todas as capturas de tela na página de detalhes do aplicativo. Certifique-se de mencionar o seguinte:

* Como seu aplicativo funciona.
* O que pode ser feito com seu aplicativo.
* Os benefícios de usar seu aplicativo.
* Para quem você é.

Lembre-se de manter sua apresentação curta e doce — em algum lugar entre 30 e 90 segundos.

## <a name="learn-more"></a>Saiba mais

[Lista de verificação para envio de aplicativo.](~/concepts/deploy-and-publish/appsource/publish.md)  
[Crie um pacote de aplicativos para seu aplicativo do Microsoft Teams.](~/concepts/build-and-test/apps-package.md)  
[Use o Partner Center para enviar sua solução para AppSource](/office/dev/store/use-partner-center-to-submit-to-appsource).
