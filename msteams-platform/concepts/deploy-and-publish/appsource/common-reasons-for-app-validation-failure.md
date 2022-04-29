---
title: Motivos comuns para falhas na validação do aplicativo
description: Saiba os motivos mais comuns para que seu aplicativo falhe na validação do aplicativo e aumente a probabilidade do seu aplicativo ser aprovado no processo de envio da loja do Teams.
ms.topic: overview
author: v-ypalikila
ms.author: v-ypalikila
ms.localizationpriority: high
ms.openlocfilehash: b8d0b0eb44a3071a6831500cfae41952e520399e
ms.sourcegitcommit: 6d87e131eeae6846cadecf6ba775cecd010b4ffc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65132723"
---
# <a name="common-reasons-for-app-validation-failure"></a>Motivos comuns para falhas na validação do aplicativo

A maioria dos aplicativos não é aprovado no processo de envio da loja devido a problemas durante o desenvolvimento do aplicativo. Os problemas ou motivos mais comuns são abordados neste artigo para ajudar você a preparar melhor seu aplicativo antes de [enviar para análise](/office/dev/store/add-in-submission-guide?toc=/microsoftteams/platform/toc.json&bc=/microsoftteams/platform/breadcrumb/toc.json). Evite essas falhas comuns e siga as [Diretrizes de validação da loja do Microsoft Teams](prepare/teams-store-validation-guidelines.md) e as [Políticas de Certificação do Marketplace Comercial](/legal/marketplace/certification-policies) para aumentar a probabilidade do seu aplicativo ser aprovado no processo de envio da loja do Microsoft Teams.

A seguir estão os motivos mais comuns para que seu aplicativo seja rejeitado:

:::row:::
   :::column:::
      :::image type="icon" source="../../../assets/icons/broken-links-errors-icon-1.png" link="#broken-links-functional-bugs-app-crashes-and-unexpected-errors":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../assets/icons/app-description-icon.png" link="#app-description":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/trademark-icon.png" link="#violation-of-microsoft-trademark-and-brand-guidelines":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/testability-icon.png" link="#testability":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/compliance-icon.png" link="#microsoft-365-app-compliance-program":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column:::
      :::image type="icon" source="../../../assets/icons/app-guideline-icon.png" link="#violation-of-app-icon-guidelines":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../assets/icons/app-name-icon.png" link="#app-name":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/support-link-icon.png" link="#support-link":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/schema-icon.png" link="#manifest-schema":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/app-ui-icon.png" link="#app-ui":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column:::
      :::image type="icon" source="../../../assets/icons/domain-icon.png" link="#valid-domains":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/localization-icon.png" link="#localization-information":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../assets/icons/developer-name-icon.png" link="#provider-or-developer-name-mismatch":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/privacy-policy-icon.png" link="#privacy-policy":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/terms-of-use-icon.png" link="#terms-of-use":::
   :::column-end:::
:::row-end:::

## <a name="broken-links-functional-bugs-app-crashes-and-unexpected-errors"></a>Links quebrados, bugs funcionais, falhas do aplicativo e erros inesperados

Teste seu aplicativo para verificar a exatidão, funcionalidade e uso do aplicativo. Certifique-se de testar seu aplicativo completamente, verificar todos os fluxos de trabalho de ponta a ponta que seu aplicativo suporta, testar a compatibilidade do aplicativo nos sistemas operacionais e navegadores de acordo com a  [Política de Certificação do Marketplace Comercial](/legal/marketplace/certification-policies) e corrigir todos os bugs. Você deve evitar os seguintes erros no seu aplicativo antes de enviar para análise:

* Links quebrados em um aplicativo.

* Bugs funcionais que bloqueiam o uso do aplicativo.

* Falhas do aplicativo.

* Carregamento contínuo de superfícies de aplicativos que impedem a conclusão dos fluxos de trabalho declarados que o aplicativo suporta.

* Mensagens de erro inesperadas durante a experiência de uso, entrada e inscrição do aplicativo e para cenários em que o recurso do aplicativo não funciona conforme o esperado.

* Certifique-se de que seu aplicativo esteja completo e pronto para publicação antes de enviar para análise.

## <a name="app-description"></a>Descrição do aplicativo

Uma ótima descrição pode fazer com que seu aplicativo se destaque na loja do Microsoft Teams e ajudar a incentivar os clientes a baixá-lo. Você deve evitar os seguintes erros na descrição do seu aplicativo:

* Informações de encaminhamento para novos usuários tais como, Inscreva-se ou Começar, ou Links de Ajuda e Fale Conosco não estão incluídos no manifesto e a descrição completa do AppSource.

* O nome ou a funcionalidade do aplicativo específico da região não são mencionados no manifesto e nas descrições do aplicativo do Partner Center.

* As limitações ou a dependência da conta de contas ou serviços externos para concluir a experiência de Entrada, Saída e Inscrição não são chamadas na descrição longa e no manifesto do aplicativo.

* A descrição curta e completa no manifesto do aplicativo não realça a proposta de valor do aplicativo.

* Os recursos do aplicativo suportados não estão atualizados.

* Comparação do aplicativo com outro aplicativo.

* Referências às integrações, que não fazem parte da funcionalidade do aplicativo.

* Erros gramaticais.

* A descrição curta e completa do aplicativo é a mesma.

## <a name="violation-of-microsoft-trademark-and-brand-guidelines"></a>Violação das diretrizes de marca e marca comercial da Microsoft

Os ativos de marca da Microsoft, incluindo logotipos, ícones, designs, imagem comercial, fontes, nomes de produtos, serviços, sons, emojis e quaisquer outros recursos e elementos da marca, registrados ou não, são ativos proprietários pertencentes à Microsoft e seu grupo de empresas.

Ao se referir às marcas comerciais, nomes de produtos e serviços da Microsoft, você deve seguir as [Diretrizes de Marca e de Marca Comercial da Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks). Você deve evitar as seguintes violações comuns que levam à rejeição do aplicativo:

* Abreviando a Microsoft como MS ou MSFT na listagem de ofertas, referenciando a primeira instância do Microsoft Teams na listagem de ofertas como **Teams** em vez de **Microsoft Teams**.

* Usar ativos da marca Microsoft no conteúdo da oferta sem uma licença expressa da Microsoft.

* Criando uma listagem de ofertas (incluindo a descrição da oferta, título, ícone, capturas de tela e vídeos) que represente ou dê a impressão de que é um aplicativo oficial da Microsoft para a loja do Microsoft Teams.

## <a name="testability"></a>Testabilidade  

 [Instruções de teste detalhadas](prepare/teams-store-validation-guidelines.md#app-package-and-store-listing) e credenciais ajudam você com uma análise bem-sucedida do seu aplicativo.

Certifique-se de fornecer todos os detalhes exigidos para a análise do seu aplicativo na seção Notas para Informações de Certificação do Partner Center, credenciais de demonstração válidas para funcionalidades que exigem a entrada e instruções para definir qualquer configuração especial, um vídeo de demonstração ou hardware para funcionalidades que exigem um ambiente difícil de replicar e concluir. Além disso, certifique-se de fornecer as informações de contato mais recentes.

Você deve evitar os seguintes problemas que ocorrem em 20% dos aplicativos que são rejeitados durante a análise do aplicativo:

* Sem instruções de teste ou credenciais para testar o aplicativo.

* Apenas uma conta de teste é fornecida quando há uma dependência com duas contas de teste para testar cenários de colaboração.

* As instruções e credenciais de teste fornecidas não são suficientes para concluir o teste funcional do aplicativo.

## <a name="microsoft-365-app-compliance-program"></a>Programa de Conformidade do Aplicativo do Microsoft 365  

O Programa de Conformidade de Aplicativos do Microsoft 365 ajuda as organizações a avaliar e gerenciar riscos, avaliando informações de segurança e conformidade sobre um aplicativo. Você **deve concluir a** [Verificação do Editor](/azure/active-directory/develop/mark-app-as-publisher-verified) antes de enviar seu aplicativo para análise para publicação na loja do Microsoft Teams.

## <a name="violation-of-app-icon-guidelines"></a>Violação das diretrizes de ícone do aplicativo

Os ícones são um dos principais elementos que as pessoas veem ao navegar na loja do Microsoft Teams. Seus ícones devem comunicar a marca e a finalidade do seu aplicativo e, ao mesmo tempo, seguir as [Diretrizes do Ícone do aplicativo](../../build-and-test/apps-package.md#app-icons). Você deve evitar as seguintes violações que resultam na rejeição do aplicativo:

* Envios de aplicativos que contêm pacotes de aplicativos com diferentes ícones coloridos e de contorno ou ícones de contorno não-brancos e não-transparentes.

* Envios de aplicativos com diferentes logotipos no Partner Center e o pacote do aplicativo enviado para análise.

## <a name="app-name"></a>Nome do aplicativo

O nome do aplicativo desempenha uma função fundamental para que os usuários descubram seu aplicativo na loja do Microsoft Teams. Certifique-se de que o nome do aplicativo atenda às [diretrizes de nome do aplicativo](prepare/teams-store-validation-guidelines.md#app-name) e não viole as [Diretrizes de Marca e Marca Comercial da Microsoft](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks). Você deve evitar as seguintes violações que resultam na rejeição do aplicativo:

* Uso inconsistente do nome do aplicativo em toda a funcionalidade do aplicativo.
* Incompatibilidade entre o nome do aplicativo mencionado no manifesto do aplicativo enviado como parte do pacote do aplicativo e o Partner Center.
* Nomes de aplicativos anexados com *Beta*, *Dev* e *Prod* para indicar que o aplicativo não está pronto para produção.
* Envios de plicativos em que o desenvolvedor alterou o nome do aplicativo, mas o antigo nome do aplicativo ainda é usado dentro do aplicativo.

## <a name="support-link"></a>Link de suporte

 Os links de suporte não devem solicitar autenticação aos usuários e devem levar diretamente às informações de suporte apropriadas. Você deve garantir que seu aplicativo inclua um link de suporte válido para que os usuários entrem em contato.

## <a name="manifest-schema"></a>Esquema de manifesto

O manifesto do Teams descreve como o aplicativo se integra ao produto Microsoft Teams. Seu manifesto do aplicativo deve estar em conformidade com um [esquema de manifesto](../../../resources/schema/manifest-schema.md) lançado publicamente. Se seu aplicativo suportar localização, certifique-se de utilizar um esquema de manifesto de localização versão 1.5 ou posterior. Pacotes de aplicativos que contêm esquemas de pré-visualização (não lançados publicamente) são reprovados na análise do aplicativo.

Você deve atualizar a versão do aplicativo declarada no manifesto se estiver enviando uma atualização do aplicativo. Recomendamos que você sempre use o esquema de manifesto mais recente lançado publicamente ao enviar um novo aplicativo ou uma atualização de aplicativo e se certificar de que a versão do esquema de manifesto na Loja do Microsoft Teams e na Microsoft AppSource é a mesma.

O pacote do aplicativo deve conter apenas o manifesto, o ícone colorido e o ícone de contorno do aplicativo. Pacotes de aplicativos que contêm quaisquer outros arquivos ou pastas adicionais são reprovados na análise do aplicativo.

## <a name="app-ui"></a>Interface do Usuário do Aplicativo

A interface do usuário do seu aplicativo não deve parecer incompleta e deve ser intuitiva. Certifique-se de que os usuários não recebam uma tela em branco ao executar uma ação na interface do usuário do aplicativo. Os aplicativos que têm conteúdo truncado ou sobreposto e os aplicativos que exibem imagens quebradas são reprovados na análise do aplicativo.

## <a name="valid-domains"></a>Domínios válidos

O envio do seu aplicativo deve seguir as diretrizes de [domínios externos](/legal/marketplace/certification-policies) da Política de Certificação do Marketplace Comercial da Microsoft. Para que seu aplicativo seja aprovado na análise, certifique-se de que os domínios válido listados no manifesto do aplicativo estejam sob controle direto da sua organização.

## <a name="localization-information"></a>Informações de localização

É necessário incluir os arquivos de idioma localizado no pacote do aplicativo se seu aplicativo der suporte à localização. Os arquivos de localização devem estar de acordo com o [esquema de localização do Teams](../../build-and-test/apps-localization.md). Aplicativos que suportam localização, mas que não possuem informações de localização no manifesto do aplicativo, são reprovados na análise do aplicativo.

## <a name="provider-or-developer-name-mismatch"></a>Incompatibilidade de nome do provedor ou desenvolvedor

Você deve fornecer o mesmo nome de desenvolvedor na sua listagem de ofertas em ambas as vitrines para evitar a confusão do usuário final durante a aquisição do aplicativo na loja do Microsoft Teams ou na Microsoft AppSource. Ofertas com incompatibilidade no nome do desenvolvedor frequentemente são reprovadas na análise do aplicativo.

## <a name="privacy-policy"></a>Política de privacidade

Sua listagem de ofertas deve incluir um link de política de privacidade válido. Ofertas com links de política de privacidade inválidos, inseguros e quebrados são reprovadas na análise do aplicativo. Sua política de privacidade deve seguir as [diretrizes da política de privacidade](prepare/teams-store-validation-guidelines.md#privacy-policy).

## <a name="terms-of-use"></a>Termos de uso

Sua listagem de ofertas deve incluir um link de Termos de uso válido. Ofertas com Termos de uso inválidos, inseguros e quebrados são reprovadas na análise do aplicativo. Você deve seguir as [Diretrizes dos Termos de Uso](prepare/teams-store-validation-guidelines.md#terms-of-use).

## <a name="see-also"></a>Confira também

* [Diretrizes de validação da loja do Microsoft Teams](prepare/teams-store-validation-guidelines.md)
* [Políticas de Certificação do Marketplace Comercial](/legal/marketplace/certification-policies)
* [Diretrizes de Marca e Marca Comercial da Microsoft](https://www.microsoft.com/legal/intellectualproperty/trademarks)
