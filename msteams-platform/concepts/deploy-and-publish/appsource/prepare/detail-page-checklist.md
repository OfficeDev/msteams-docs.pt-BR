---
title: Criar uma ótima página de detalhes do aplicativo
description: Descreve os requisitos da página de detalhes do aplicativo
ms.topic: reference
keywords: teams publish store office publishing policy AppSource content Metadata screenshot logo name icons short description
ms.openlocfilehash: fa3086c92f69b74f7b0669ea26a6162ac3acc5c2
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014219"
---
# <a name="build-a-great-app-details-page"></a>Criar uma ótima página de detalhes do aplicativo

A página de detalhes apresenta a primeira impressão do seu aplicativo para os usuários. Cada elemento da sua página de detalhes pode ser usado para transmitir sua visão e downloads de unidade — considere como você deseja demonstrar seu aplicativo em um espaço limitado. Aqui estão algumas dicas e truques para ajudá-lo a envolver seus usuários antes mesmo de instalar seu aplicativo.

> [!NOTE]
> Certifique-se de que as informações do seu aplicativo sigam nossas diretrizes do [AppSource para criar uma listagem da Loja eficaz.](/office/dev/store/create-effective-office-store-listings)

## <a name="app-name"></a>Nome do aplicativo

> [!div class="checklist"]
>
> * O nome de um aplicativo desempenha um papel fundamental na forma como os usuários o descobre na app store do AppSource. O nome curto do aplicativo é exibido na página de detalhes.
>* O nome do aplicativo deve refletir seu aplicativo sem qualquer referência aos produtos da Microsoft ou da Microsoft.
>

> **Observação:** se seu aplicativo for uma parceria oficial com a Microsoft, o nome do aplicativo de terceiros precisará ser o primeiro, por exemplo, o Conector salesforce para *o Microsoft Teams.*

> [!div class="checklist"]
>
>* Use estes recursos para obter orientações:

* [Guia de nome do aplicativo](#app-name)
* [Diretrizes de marca e marca da Microsoft](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)

**O que fazer é:**

* Escolha um nome simples e fácil de lembrar que indica o que seu aplicativo faz.
* Seja distinto.
* Se necessário, use as referências do Microsoft 365 em vez do Office 365.

**O que não fazer:**

* Não omita espaços, tenha uma ocorrência incorreta ou contenha erros de idioma no nome do aplicativo.
* Não use termos genéricos ou nomes semelhantes aos aplicativos existentes.
* Não use "Teams", "Microsoft", nomes de produtos da Microsoft existentes/futuros ou "aplicativo" no nome do aplicativo.
* Não use parênteses para incluir produtos da Microsoft, por exemplo, o Nome do Seu *Aplicativo (para o Microsoft Teams).*

![Exibição da loja de nomes de aplicativos](../../../../assets/images/store-detail-page/AppName-02.png)

![App Name App Studio view](../../../../assets/images/store-detail-page/AppName-01.png)

## <a name="color-icon"></a>Ícone de cor

Este é um dos primeiros elementos que os usuários veem. Ele deve ser atraente e atraente ao rolar pela loja de aplicativos. Certifique-se de que isso seja uma boa primeira impressão e também comunique a imagem e a finalidade da sua marca. O AppSource tem mais dicas sobre [como criar uma identidade visual consistente.](/office/dev/store/create-effective-office-store-listings#create-a-consistent-visual-identity)

![Exibição da loja de ícones do aplicativo](~/assets/images/store-detail-page/AppIcon-02.png)

![App icon App Studio view](~/assets/images/store-detail-page/AppIcon-01.png)

**O que não fazer:**

* Seu ícone não deve imitar nenhum produto protegido por direitos autorais que você não possui.
* Seu ícone não deve ser semelhante a qualquer produto/marca da Microsoft.

## <a name="outline-icon"></a>Ícone de contorno

Esse ícone é usado para extensões de mensagens fixadas e quando seu aplicativo é exibido à esquerda do Teams. Consulte [as diretrizes de design para o ícone de estrutura de estrutura de estrutura.](../../../../concepts/build-and-test/apps-package.md#outline-icon)

![App icon outline store view ](../../../../assets/images/store-detail-page/AppIconOutline-02.png)
 ![ App icon outline App Studio view](../../../../assets/images/store-detail-page/AppIconOutline-01.png)

**O que não fazer:**

* Seu ícone não deve imitar nenhum produto protegido por direitos autorais que você não possui.
* Seu ícone não deve ser semelhante a qualquer produto/marca da Microsoft.

## <a name="short-description"></a>Descrição breve

Este é um resumo conciso do seu aplicativo. Ela deve ser original, interessante e direcionada ao seu público-alvo. O ideal é tentar descrever sua solução e seu valor para os usuários em uma única frase.

**O que fazer é:**

* Fale primeiro as informações mais importantes.
* Inclua palavras-chave que os clientes provavelmente pesquisarão.
* Se você precisar mencionar o Microsoft Teams, a primeira menção do Microsoft Teams deve ser escrita na íntegra como *Microsoft Teams.* Se o Teams for mencionado novamente na mesma descrição, o nome poderá ser encurtado para o *Teams.*
* Todas as referências à Microsoft ou ao Microsoft Teams podem fazer parte da descrição e devem seguir os padrões e diretrizes da marca da Microsoft.
* Todas as descrições devem ser gramaticalmente corretas sem erros de idioma.
* Evite o uso desnecessário de maiúsculas, por exemplo, informando "Usuários" em vez de "usuários".

**O que não fazer:**

* Não repita o título.
* Não abreviar a Microsoft como "MS" ou "MSFT".
* Não use jargão ou terminologia especializada — você não pode presumir que os usuários saibam o que procurar.
* Evite referências desnecessárias a nomes de produtos da Microsoft, a menos que seja absolutamente necessário.
* Não indique ou indique que o aplicativo é uma oferta da Microsoft.
* Não use nomes de marca protegidos por direitos autorais que você não possui.
* Não use "para o Teams" em um nome curto.

![Exibição de armazenamento de Descrição Curta](~/assets/images/store-detail-page/ShortDescription-02.png)

Aqui está uma exibição no [App Studio:](https://aka.ms/InstallTeamsAppStudio)

![Exibição do App Studio de Descrição Curta](~/assets/images/store-detail-page/ShortDescription-01.png)

## <a name="long-description"></a>Descrição longa

> [!div class="checklist"]
>
>* Isso fornece uma história envolvente que destaca os principais recursos da sua solução, os problemas que ela resolve e o público-alvo. Desenque seu público com a primeira frase comunicando os recursos exclusivos do seu aplicativo. Sua descrição deve ter menos de 4.000 caracteres; a maioria dos usuários só lerá entre 300 e 500 palavras.
>* O que é permitido?

* `<your_app>`  "funciona com o Microsoft Teams"
* `<for users>`  "trabalhando com o Microsoft Teams"
* `<for tasks>`  "no Microsoft Teams"
* `<an app>`  "para o Microsoft Teams"
* `<your_app>`  "integra-se ao Microsoft Teams"
* "... integrado ao Microsoft Teams"
* "... criado em..."
* "... é executado em..."
* "... habilitado por..."
* "... desenvolvido para..."
* "... projetado para..."

> **Observação:** os termos acima também se aplicam ao uso do Microsoft 365. O Office 365 agora é chamado de Microsoft 365. Atualize as descrições do aplicativo para refletir isso.

>[!IMPORTANT]
> Copie com precisão as descrições que você escreveu na entrada do AppSource no manifesto do aplicativo — os valores devem corresponder. O Microsoft Teams usará apenas as descrições fornecidas no manifesto do aplicativo.

**O que fazer é:**

* Use [a formatação Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) para iluminar sua descrição.  
* Listar recursos para auxiliar os leitores na verificação de sua descrição.
* Use a voz ativa e fale diretamente com os usuários.
* Use pontos de marcador para listar seus recursos.
* Inclua um link de ajuda ou suporte para que os usuários saibam como falar com você se eles têm dúvidas.
* Certifique-se de que a primeira menção do Microsoft Teams seja escrita na íntegra como "*Microsoft Teams*". Se o Teams for mencionado novamente mais tarde na mesma descrição, o nome poderá ser reduzido para "*Teams*".
* Quaisquer referências à Microsoft ou ao Microsoft Teams (somente se necessário) podem fazer parte da descrição longa e devem seguir os padrões e diretrizes da marca da Microsoft.
* Todas as descrições devem estar gramaticalmente corretas sem erros de idioma.
* Evite o uso desnecessário de maiúsculas em termos em sua descrição (exemplo: declarando "Usuários" em vez de "usuários".
* Evite acrônimos.
* Certifique-se de chamar limitações, dependência de conta, configuração definida, atualizações futuras em versões ou quaisquer restrições de uso

>[!NOTE]
> O Microsoft Teams dá suporte à seguinte sintaxe de Markdown:  
> **Links**. `[title](url/address/here)`.  
>**Imagens** `![alt text](url/address/here)` ...  
> **Negrito**. `**bold text**`   `__bold text__`.  
> **Itálico .** `*italicized text*`  `_italicized text`.  
>**[Listas ordenadas](https://www.markdownguide.org/basic-syntax/#ordered-lists)**<br>
>`1. first` 
<br>` 1. second ` 
<br>`1.third`<br>
>**[Unordered List](https://www.markdownguide.org/basic-syntax/#unordered-lists)**<br>
` - short` <br>`- bulleted` <br>`- list`<br>
>**Newline**. `Place <br> at the end of a line.` <br> 
 >**Escape.** Use uma inline backslash para escapar caracteres especiais. `\*asterisk`.

**Exemplo no formato Markdown**

|Formato de markdown para |Formato markdown |Texto exibido|
|:---------|:---------------|:-------------|
|Link  |` [App name guide](#app-name)`| [Guia de nome do aplicativo](#app-name) |
|Image |` ![App long description store view](~/assets/images/store-detail-page/LongDescription-02.png)`| ![Exibição do armazenamento de descrição longa do aplicativo](~/assets/images/store-detail-page/LongDescription-02.png)|
|Negrito |` **HR Tools**` | **Ferramentas de RH**  |
|Itálico |`*HR Tools*` |*Ferramentas de RH*|
|Newline |` HR Tools provide wide range of solutions that help your organization to manage day-to-day HR activities effectively. <br> No more flipping through paper records or juggling among 5 different apps.` |As Ferramentas de RH fornecem uma ampla variedade de soluções que ajudam sua organização a gerenciar as atividades diárias de RH com eficiência. <br>  Não há mais inverta registros de papel ou manipulando entre cinco aplicativos diferentes.|
|Escape|`\*Payroll tools that help you manage your payroll and tax documents.` |\*Ferramentas de folha de pagamento que ajudam você a gerenciar sua folha de pagamento e documentos fiscais. 

**O que não fazer:**

* Não coloque muitas palavras-chave em sua descrição. Isso desvia a atenção e não ajuda a descoberta do seu aplicativo.
* Não use "*Teams*" ou "*Microsoft Teams*" em um nome curto.
* Evite referências desnecessárias a nomes de produtos da Microsoft, a menos que seja absolutamente necessário.
* Não indique que o aplicativo é uma oferta da Microsoft.
* Não use nomes de marca protegidos por direitos autorais que você não possui.
* Não use o seguinte idioma, a menos que o aplicativo tenha passado por um processo de certificação oficial:

  * "... certificado para..."
  * "... da tecnologia..."

* Não abreviar "Microsoft" para "MS" ou "MSFT" — escreva a Microsoft na íntegra.
* Nenhuma parte da descrição ou dos metadados pode indicar o aplicativo como uma oferta oficial da Microsoft.
* Os parceiros não podem usar ou imitar qualquer marca da Microsoft ou usar o nome de qualquer produto ou serviço da Microsoft no tagline ou no tagline.
* O logotipo não deve representar incorretamente o aplicativo como um produto/recurso oficial da Microsoft ou imitar qualquer um dos produtos da Microsoft existentes ou futuros.

![Exibição do armazenamento de descrição longa do aplicativo](~/assets/images/store-detail-page/LongDescription-02.png)

Aqui está uma exibição no [App Studio:](https://aka.ms/InstallTeamsAppStudio)

![Exibição do App Studio de descrição longa do aplicativo](~/assets/images/store-detail-page/LongDescription-01.png)

## <a name="screenshots"></a>Capturas de tela

As capturas de tela carregadas no [Partner Center](https://partner.microsoft.com) são exibidas no [AppSource](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) e na listagem do aplicativo no cliente do Teams. Eles fornecem uma visualização visual do seu aplicativo juntamente com a descrição do aplicativo.
Você pode fornecer de uma a cinco capturas de tela formatadas como arquivos .png, .jpg ou .gif. Screenshots should be 1366 x 768 pixels with a maximum size of 1024 KB.

**O que fazer é:**

* Concentre-se em realçar todos os recursos do seu aplicativo.
* O conteúdo deve representar seu aplicativo com precisão.
* O texto deve ser bem preenchido sem ser excessivo.
* Você pode colocar suas capturas de tela com uma cor de fundo e adicionar conteúdo de marketing semelhante ao [exemplo do Freshdesk;](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) no entanto, as dimensões não serão apenas da captura de tela, mas incluirão a imagem geral.

<img width="800px" alt="Freshdesk screenshot" src="../../../../assets/images/freshdesk.png" />

**O que não fazer:**

* Não mostre dispositivos específicos, como telefones ou laptops.
* Não mostre chrome/interface do usuário de fora do seu aplicativo.
* Não capture nenhuma interface do usuário do navegador ou do Teams nas capturas de tela.
* Não inclua modelos que reflitam imprecisamente a interface do usuário real de seus aplicativos, como mostrar seu site em vez da guia do Teams.

Para obter mais práticas *recomendadas, consulte:* [Criação de imagens efetivas da loja do AppSource.](/office/dev/store/craft-effective-appsource-store-images)

## <a name="videos"></a>Vídeos

Se uma imagem vale milhares de palavras, então um vídeo vale milhares de imagens. Os vídeos são a maneira mais eficaz de comunicar os benefícios de usar seu aplicativo. Ele será colocado na frente de todas as capturas de tela na página de detalhes do aplicativo. Certifique-se de mencionar o seguinte:

* Como seu aplicativo funciona.
* O que pode ser feito com seu aplicativo.
* Os benefícios de usar seu aplicativo.
* Para quem você é.

Lembre-se de manter sua apresentação curta e meiga — em algum lugar entre 30 e 90 segundos.

## <a name="learn-more"></a>Saiba mais

[Lista de verificação para envio de aplicativo.](~/concepts/deploy-and-publish/appsource/publish.md)  
[Crie um pacote do aplicativo para o aplicativo Microsoft Teams.](~/concepts/build-and-test/apps-package.md)  
[Use o Partner Center para enviar sua solução ao AppSource.](/office/dev/store/use-partner-center-to-submit-to-appsource)
