---
title: Diretrizes de design para guias
description: Descreve as diretrizes para a criação de guias de conteúdo e colaboração
keywords: Diretrizes de design de equipes referência configuração de guias
ms.openlocfilehash: adf86678a42e2267af00734e1ef85efced882488
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672431"
---
# <a name="content-and-conversations-all-at-once-using-tabs"></a>Conteúdo e conversas, todos ao mesmo tempo usando guias

> [!Important]
> **Guias em clientes móveis**
>
> Siga as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias. Se sua guia usa autenticação, você deve atualizar o SDK do JavaScript do Microsoft Teams para a versão 1.4.1 ou posterior, ou a autenticação falhará.
>
> **Guias pessoais (estáticos) no celular:**
>
> * As guias estáticas (aplicativo pessoal) estão disponíveis na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).
> * Ao criar suas guias estáticas, certifique-se de seguir as [orientações para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)
>
> **Guias de canal/grupo (configurável) em dispositivos móveis:**
>
> * Os clientes móveis só mostram guias com um valor para `websiteUrl`. Se quiser que a sua guia apareça nos clientes móveis do Microsoft Teams, você deve definir o `websiteUrl`valor de.
> * O comportamento de abertura padrão no Mobile é abrir fora do navegador usando `websiteUrl`o. Para aplicativos publicados na loja de aplicativos públicos, se você quiser que a guia de canal seja aberta no Teams por padrão, siga as [orientações para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)e entre em seu representante de suporte para solicitar a lista branca.

Guias são Canvases que você pode usar para compartilhar conteúdo, reter conversas e hospedar serviços de terceiros, tudo em um fluxo de trabalho orgânica da equipe. Quando você cria uma guia no Microsoft Teams, ele coloca seu aplicativo Web front e Center onde ele é facilmente acessível contra conversas principais.

## <a name="guidelines"></a>Diretrizes

Uma guia boa deve exibir as seguintes características:

### <a name="focused-functionality"></a>Funcionalidade prioritária

As guias funcionam melhor quando são criadas para atender a uma necessidade específica. Concentre-se em um pequeno conjunto de tarefas ou em um subconjunto de dados que é relevante para o canal em que a guia se encontra.

### <a name="reduced-chrome"></a>Cromo reduzido

Evite criar vários painéis em uma guia, adicionar camadas de navegação ou exigir que os usuários rolem verticalmente e horizontalmente em uma guia. Em outras palavras, tente não ter tabulações na guia.

> [!TIP]
> Evite criar vários painéis em uma guia, adicionar camadas de navegação ou exigir que os usuários rolem verticalmente e horizontalmente em uma guia.

### <a name="integration"></a>Integração

Encontre maneiras de notificar os usuários sobre a atividade da guia postando cartões em uma conversa, por exemplo.

### <a name="conversational"></a>Coloquial

Encontre uma maneira de facilitar a conversa em torno de uma guia. Isso garante que o centro de conversas fique no conteúdo, nos dados ou no processo em mãos.

### <a name="streamlined-access"></a>Acesso simplificado

Certifique-se de que você está concedendo acesso às pessoas certas no momento certo. Manter o processo de entrada simples evitará a criação de barreiras para contribuição e colaboração.

### <a name="personality"></a>Personalidade

A tela da guia apresenta uma boa oportunidade para marcar sua experiência. Incorpore seus próprios logotipos, cores e layouts para comunicar personalidade.

O logotipo é uma parte importante da sua identidade e uma conexão com os usuários. Portanto, certifique-se de incluí-lo.

* Coloque o logotipo no canto esquerdo ou direito ou ao longo da borda inferior
* Mantenha seu logotipo pequeno e discreto

> [!TIP]
> Trabalhe com o nosso estilo visual para que seu serviço se sente como parte do teams.

---

## <a name="tab-layouts"></a>Layouts de guia

[!include[Tab layouts](~/includes/design/tab-layouts.html)]

---

## <a name="types-of-tabs"></a>Tipos de guias

[!include[Tab types](~/includes/design/tab-types.html)]

---

## <a name="configuration-page-height"></a>Altura da página de configuração

>[!NOTE]
>Em setembro de 2018, a altura da [página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md) da guia foi aumentada enquanto a largura permanece inalterada. Se o seu aplicativo for projetado para o tamanho mais antigo, a página de configuração da guia terá uma grande quantidade de espaço em branco vertical. Aplicativos de repositório herdados isentos dessa alteração precisarão entrar em contato com a Microsoft após a atualização para acomodar as novas dimensões.

As dimensões da página de configuração de guia:

<img width="450px" title="Tamanhos de guias de configuração" src="~/assets/images/tabs/config-dialog-Contoso2.png" />

### <a name="guidelines-for-tab-configuration-page-format"></a>Diretrizes para o formato de página de configuração de guia

* Baseie a altura mínima da área de conteúdo da página de configuração da guia em elementos gráficos de altura fixa.
* Calcula o espaço vertical disponível (a altura da área de conteúdo na página de configuração) `window.innerHeight`usando o. Isso retorna o tamanho do `<iframe>` no qual a página de configuração reside, o que pode ser alterado em versões futuras. Usando esse valor, seu conteúdo será ajustado automaticamente para futuras alterações.
* Alocar espaço vertical para os elementos de altura variável menos o que é necessário para os elementos de altura fixa.
* Para o estado de *logon* , centralizar o conteúdo verticalmente e horizontalmente.
* Se você quiser uma imagem de plano de fundo, precisará de uma nova imagem, dimensionada para se ajustar à área (preferencial) ou pode manter a mesma imagem e escolher entre:
  * alinhamento no canto superior esquerdo.
  * dimensionar a imagem para ajustá-la.

Quando dimensionado corretamente, sua página de configuração de guia deve ser semelhante a esta:

<img width="450px" title="Nova guia de configuração" src="~/assets/images/tabs/config-dialog-Contoso.png" />

## <a name="best-practices"></a>Práticas recomendadas

### <a name="always-include-a-default-state"></a>Sempre incluir um estado padrão

Inclua um estado padrão para facilitar a configuração de guias, mesmo que sua guia seja configurável.

### <a name="deep-linking"></a>Vinculação profunda

Sempre que possível, cartões e bots devem se vincular detalhadamente a dados mais ricos em uma guia hospedada. Por exemplo, um cartão pode exibir um resumo dos dados de bug, mas clicar nele pode mostrar o erro inteiro em uma guia.

### <a name="naming"></a>Nomenclatura

Em muitos casos, o nome do seu aplicativo pode criar um ótimo nome de guia. Mas considere nomear suas guias de acordo com a funcionalidade que elas fornecem.
