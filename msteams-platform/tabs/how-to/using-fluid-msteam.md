---
title: Usar o Fluid com o Teams
author: timtwang
ms.author: mobajemu
description: Tutorial para integrar recursos de colaboração em tempo real da plataforma Fluid em um aplicativo de guia do Microsoft Teams
ms.localizationpriority: medium
ms.topic: conceptual
ms.openlocfilehash: 620e2150ca6300fb8d37bc7c68b965aacb19700b
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615368"
---
# <a name="use-fluid-with-teams"></a>Usar o Fluid com o Teams

Ao final deste tutorial, você pode integrar qualquer aplicativo baseado em Fluid ao Teams e colaborar com outras pessoas em tempo real.

Nesta seção, você pode aprender os seguintes conceitos:

1. Integre um cliente Fluid ao aplicativo de guia do Teams.
1. Execute e conecte seu aplicativo Teams a um serviço Fluid (Azure Fluid Relay).
1. Crie e obtenha Contêineres Fluidos e passe-os para um React componente.

Para obter mais informações sobre como criar aplicativos complexos, consulte [o Olá, Mundo do Teams Fluid](https://github.com/microsoft/FluidExamples/tree/main/teams-fluid-hello-world) em nosso repositório FluidExamples.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial requer familiaridade com os seguintes conceitos e recursos:

- [Visão geral do Fluid Framework](https://fluidframework.com/docs/)
- [Início Rápido do Fluid Framework](https://fluidframework.com/docs/start/quick-start/)
- Noções básicas [de React](https://reactjs.org/) e [React ganchos](https://reactjs.org/docs/hooks-intro.html)
- Como criar uma guia [do Microsoft Teams](/microsoftteams/platform/tabs/what-are-tabs)

> [!div class="nextstepaction"]
> [Instalar pré-requisitos](tab-requirements.md)

## <a name="create-the-project"></a>Criar o projeto

1. Abra um Prompt de Comando e navegue até a pasta pai onde você deseja criar o projeto, por exemplo, `/My Microsoft Teams Projects`.
1. Crie um aplicativo de guia do Teams executando o seguinte comando e [criando uma guia de canal](create-channel-group-tab.md#create-a-custom-channel-or-group-tab-with-nodejs):

    ```cmd
    yo teams
    ```

1. Depois de criar, navegue até o projeto, com o comando a seguir `cd <your project name>`.
1. O projeto usa as seguintes bibliotecas:

    |Biblioteca |Descrição |
    |---|---|
    | `fluid-framework`    |Contém o IFluidContainer e outras [estruturas de](https://fluidframework.com/docs/build/dds/) dados distribuídas que sincronizam dados entre clientes.|
    | `@fluidframework/azure-client`   |Define o esquema inicial para o [contêiner Fluid](https://fluidframework.com/docs/build/containers/).|
    | `@fluidframework/test-client-utils` |Define o necessário `InsecureTokenProvider` para criar a conexão com um serviço Fluid.|

    Execute o seguinte comando para instalar as bibliotecas:

    ```cmd
    npm install @fluidframework/azure-client fluid-framework @fluidframework/test-client-utils
    ```

## <a name="code-the-project"></a>Codificar o projeto

1. Abra o arquivo `/src/client/<your tab name>` no editor de código.
1. Crie um novo arquivo como e `Util.ts` adicione as seguintes instruções de importação:

    ```ts
    //`Util.ts

    import { IFluidContainer } from "fluid-framework";
    import { AzureClient, AzureClientProps } from "@fluidframework/azure-client";
    import { InsecureTokenProvider } from "@fluidframework/test-client-utils";
    ```

### <a name="defining-fluid-functions-and-parameters"></a>Definindo funções e parâmetros fluid

Esse aplicativo destina-se a ser usado no contexto do Microsoft Teams, com todas as importações, inicializações e funções relacionadas ao Fluid juntas. Isso fornece uma experiência aprimorada e facilita o uso no futuro. Você pode adicionar o seguinte código às instruções de importação:

```ts
// TODO 1: Define the parameter key(s).
// TODO 2: Define container schema.
// TODO 3: Define connectionConfig (AzureClientProps).
// TODO 4: Create Azure client.
// TODO 5: Define create container function.
// TODO 6: Define get container function.
```

> [!NOTE]
> Os comentários definem todas as funções e constantes necessárias para interagir com o serviço e o contêiner do Fluid.

1. Substitua `TODO 1:` pelo código a seguir:

    ```ts
    export const containerIdQueryParamKey = "containerId";
    ```

    A constante está sendo exportada `contentUrl` conforme acrescenta às configurações do Microsoft Teams e posteriormente para analisar a ID do contêiner na página de conteúdo. É um padrão comum armazenar chaves de parâmetro de consulta importantes como constantes, em vez de digitar a cadeia de caracteres bruta a cada vez.

    Antes que o cliente possa criar contêineres, ele precisa de `containerSchema` um que defina os objetos compartilhados usados neste aplicativo. Este exemplo usa um SharedMap como , `initialObjects`mas qualquer objeto compartilhado pode ser usado.

    > [!NOTE]
    > É `map` a ID do objeto `SharedMap` e deve ser exclusiva dentro do contêiner como qualquer outro DDSes.

1. Substitua `TODO: 2` pelo código a seguir:

    ```ts
    const containerSchema = {
        initialObjects: { map: SharedMap }
    };
    ```

1. Substitua `TODO: 3` pelo código a seguir:

    ```ts
    const connectionConfig : AzureClientProps =
    {
        connection: {
            type: "local",
            tokenProvider: new InsecureTokenProvider("foobar", { id: "user" }),
            endpoint: "http://localhost:7070"
        }
    };
    ```

    Antes que o cliente possa ser usado, ele precisa de `AzureClientProps` um que defina o tipo de conexão que o cliente usa. A `connectionConfig` propriedade é necessária para se conectar ao serviço. O modo local do Cliente do Azure é usado. Para habilitar a colaboração em todos os clientes, substitua-a pelas credenciais do Serviço fluid Relay. Para obter mais informações, consulte como [configurar o serviço do Azure Fluid Relay](/azure/azure-fluid-relay/how-tos/provision-fluid-azure-portal).

1. Substitua `TODO: 4` pelo código a seguir:

    ```ts
    const client = new AzureClient(connectionConfig);
    ```

1. Substitua `TODO: 5` pelo código a seguir:

    ```ts
    export async function createContainer() : Promise<string> {
        const { container } = await client.createContainer(containerSchema);
        const containerId = await container.attach();
        return containerId;
    };
    ```

    Ao criar o contêiner na `contentUrl` página de configuração e anexá-lo à configuração no Teams, você deve retornar a ID do contêiner depois de anexar o contêiner.

1. Substitua `TODO: 6` pelo código a seguir:

    ```ts
    export async function getContainer(id : string) : Promise<IFluidContainer> {
        const { container } = await client.getContainer(id, containerSchema);
        return container;
    };
    ```

    Ao buscar o contêiner fluid, você precisa retornar o contêiner, pois seu aplicativo deve interagir com o contêiner e os DDSes dentro dele, na página de conteúdo.

### <a name="create-fluid-container-in-the-configuration-page"></a>Criar contêiner do Fluid na página de configuração

1. Abra o arquivo `src/client/<your tab name>/<your tab name>Config.tsx` no editor de código.

    O fluxo de aplicativo de guia padrão do Teams vai da configuração para a página de conteúdo. Para habilitar a colaboração, manter o contêiner durante o carregamento na página de conteúdo é crucial. A melhor solução para persistir o contêiner é acrescentar a ID `contentUrl` `websiteUrl`do contêiner às URLs da página de conteúdo como um parâmetro de consulta. O botão Salvar na página de configuração do Teams é o gateway entre a página de configuração e a página de conteúdo. É um local para criar o contêiner e acrescentar a ID do contêiner nas configurações.

1. Adicione a seguinte declaração de importação:

    ```ts
    import { createContainer, containerIdQueryParamKey } from "./Util";
    ```

1. Substitua o método `onSaveHandler` com o seguinte código. As únicas linhas adicionadas aqui `Utils.ts` são chamar o método criar contêiner definido anteriormente e, em seguida, acrescentar a ID `contentUrl` de contêiner retornada ao parâmetro e `websiteUrl` como um parâmetro de consulta.

    ```ts {linenos=inline,hl_lines=[134,136,137]}
    const onSaveHandler = async (saveEvent: microsoftTeams.settings.SaveEvent) => {
        const host = "https://" + window.location.host;
        const containerId = await createContainer();
        microsoftTeams.settings.setSettings({
            contentUrl: host + "/<your tab name>/?" + containerIdQueryParamKey + "=" + containerId + "&name={loginHint}&tenant={tid}&group={groupId}&theme={theme}",
            websiteUrl: host + "/<your tab name>/?" + containerIdQueryParamKey + "=" + containerId + "&name={loginHint}&tenant={tid}&group={groupId}&theme={theme}",
            suggestedDisplayName: "<your tab name>",
            removeUrl: host + "/<your tab name>/remove.html?theme={theme}",
            entityId: entityId.current
        });
        saveEvent.notifySuccess();
    };
    ```

    Substitua pelo `<your tab name>` nome da guia do projeto.

    > [!WARNING]
    > Como a URL da página de conteúdo é usada para armazenar a ID do contêiner, esse registro será removido se a guia Teams for excluída.
    > Além disso, cada página de conteúdo só pode dar suporte a uma ID de contêiner.

### <a name="refactor-content-page-to-reflect-fluid-application"></a>Página Refatorar conteúdo para refletir o aplicativo Fluid

1. Abra o arquivo `src/client/<your tab name>/<your tab name>.tsx` no editor de código. Um aplicativo típico da plataforma Fluid consiste em uma exibição e uma estrutura de dados Fluid. Concentre-se em obter/carregar o contêiner Fluid e deixar todas as interações relacionadas ao Fluid em um React componente.

1. Adicione as seguintes instruções de importação na página de conteúdo:

    ```ts
    import { IFluidContainer } from "fluid-framework";
    import { getContainer, containerIdQueryParamKey } from "./Util";
    ```

1. Remova todo o código abaixo das instruções de importação na página de conteúdo e substitua-o pelo seguinte:

    ```ts
    export const <your tab name> = () => {
      // TODO 1: Initialize Microsoft Teams.
      // TODO 2: Initialize inTeams boolean.
      // TODO 3: Define container as a React state.
      // TODO 4: Define a method that gets the Fluid container
      // TODO 5: Get Fluid container on content page startup.
      // TODO 6: Pass the container to the React component as argument.
    }
    ```

    Substitua pelo `<your tab name>` nome da guia definido para seu projeto.

1. Substitua `TODO 1` pelo código a seguir:

    ```ts
    microsoftTeams.initialize();
    ```

    Para exibir a página de conteúdo no Teams, você deve incluir o [SDK do cliente JavaScript do Microsoft Teams](/javascript/api/overview/msteams-client) e incluir uma chamada para inicializá-la após o carregamento da página.

1. Substitua `TODO 2` pelo código a seguir:

    ```ts
    const [{ inTeams }] = useTeams();
    ```

    Como o aplicativo Teams é apenas uma injeção de IFrame de uma página da Web, `inTeams` você precisa inicializar a constante booliana para saber se o aplicativo está dentro do Teams ou não e se os recursos do Teams, `contentUrl`como o , estão disponíveis.

1. Substitua `TODO 3` pelo código a seguir:

    ```ts
    const [fluidContainer, setFluidContainer] = useState<IFluidContainer | undefined>(undefined);
    ```

    Use um React para o contêiner, pois ele fornece a capacidade de atualizar dinamicamente o contêiner e os objetos de dados nele.

1. Substitua `TODO 4` pelo código a seguir:

    ```ts
    const getFluidContainer = async (url : URLSearchParams) => {
        const containerId = url.get(containerIdQueryParamKey);
        if (!containerId) {
            throw Error("containerId not found in the URL");
        }
        const container = await getContainer(containerId);
        setFluidContainer(container);
    };
    ```

    Analise a URL para obter a cadeia de caracteres de parâmetro de consulta, definida por `containerIdQueryParamKey`, e recuperar a ID do contêiner. Com a ID do contêiner, você pode carregar o contêiner. Depois de ter o contêiner, defina o React `fluidContainer` , consulte a etapa anterior.

1. Substitua `TODO 5` pelo código a seguir:

    ```ts
    useEffect(() => {
        if (inTeams === true) {
            microsoftTeams.settings.getSettings(async (instanceSettings) => {
                const url = new URL(instanceSettings.contentUrl);
                getFluidContainer(url.searchParams);
            });
            microsoftTeams.appInitialization.notifySuccess();
        }
    }, [inTeams]);
    ```

    Depois de definir como obter o contêiner do Fluid, `getFluidContainer` você precisará informar React chamada ao carregar e, em seguida, armazenar o resultado no estado com base em se o aplicativo estiver dentro do Teams.
    React de [useState](https://reactjs.org/docs/hooks-state.html) fornece o armazenamento necessário e [useEffect](https://reactjs.org/docs/hooks-effect.html) `getFluidContainer` permite que você chame na renderização, passando o valor retornado para `setFluidContainer`.

    Ao adicionar `inTeams` a matriz de dependência `useEffect`no final do , o aplicativo garante que essa função seja chamada apenas no carregamento da página de conteúdo.

1. Substitua `TODO 6` pelo código a seguir:

    ```ts
    if (inTeams === false) {
      return (
          <div>This application only works in the context of Microsoft Teams</div>
      );
    }

    if (fluidContainer !== undefined) {
      return (
          <FluidComponent fluidContainer={fluidContainer} />
      );
    }

    return (
      <div>Loading FluidComponent...</div>
    );
    ```

    > [!NOTE]
    > É importante garantir que a página de conteúdo seja carregada dentro do Teams e que o contêiner Fluid seja definido antes de passá-lo para o componente React (`FluidComponent`definido como , veja abaixo).

### <a name="create-react-component-for-fluid-view-and-data"></a>Criar React componente para exibição e dados do Fluid

Você integrou o fluxo básico de criação do Teams e do Fluid. Agora você pode criar seu próprio React que lida com as interações entre a exibição do aplicativo e os dados do Fluid. A partir de agora, a lógica e o fluxo se comportam como outros aplicativos baseados em Fluid. Com a estrutura básica configurada, você pode criar qualquer um dos [exemplos do Fluid](https://github.com/microsoft/FluidExamples) como um aplicativo do Teams `ContainerSchema` alterando a interação da exibição do aplicativo com os objetos DDSes/dados na página de conteúdo.

## <a name="start-the-fluid-server-and-run-the-application"></a>Inicie o servidor Fluid e execute o aplicativo

Se você estiver executando o aplicativo Teams localmente com o modo local do Cliente do Azure, execute o seguinte comando no Prompt de Comando para iniciar o serviço Fluid:

```cmd
npx @fluidframework/azure-local-service@latest
```

Para executar e iniciar o aplicativo Teams, abra outro terminal e siga as [instruções para executar o servidor de aplicativos](create-channel-group-tab.md#upload-your-application-to-teams).

> [!WARNING]
> HostNames com `ngrok`túneis livres não são preservados. Cada execução gerará uma URL diferente. Quando um novo `ngrok` túnel é criado, o contêiner mais antigo não estará mais acessível. Para cenários de produção, [consulte usar o AzureClient com o Azure Fluid Relay](#use-azureclient-with-azure-fluid-relay).

> [!NOTE]
> Instale uma dependência adicional para tornar essa demonstração compatível com o Webpack 5. Se você receber um erro de compilação relacionado a um pacote de "buffer", execute e `npm install -D buffer` tente novamente. Isso será resolvido em uma versão futura do Fluid Framework.

## <a name="next-steps"></a>Próximas etapas

### <a name="use-azureclient-with-azure-fluid-relay"></a>Usar o AzureClient com o Azure Fluid Relay

Como esse é um aplicativo de guia do Teams, a colaboração e a interação são o foco principal. Substitua o modo local `AzureClientProps` fornecido anteriormente por credenciais não locais de sua instância de serviço do Azure, para que outras pessoas possam ingressar e interagir com você no aplicativo. Veja [como provisionar seu serviço do Azure Fluid Relay](/azure/azure-fluid-relay/how-tos/provision-fluid-azure-portal).

> [!IMPORTANT]
> É importante ocultar as credenciais que você está passando de serem acidentalmente confirmadas `AzureClientProps` no controle do código-fonte. O projeto do Teams vem com um `.env` arquivo em que você pode armazenar suas credenciais como variáveis de ambiente e o próprio arquivo já está incluído no `.gitignore`. Para usar as variáveis de ambiente no Teams, consulte [Definir e obter a variável de ambiente](#set-and-get-environment-variable).

> [!WARNING]
> `InsecureTokenProvider` é uma maneira conveniente de testar o aplicativo localmente. É sua responsabilidade lidar com qualquer autenticação de usuário e usar um [token seguro](/azure/azure-fluid-relay/how-tos/connect-fluid-azure-service) para qualquer ambiente de produção.

### <a name="set-and-get-environment-variable"></a>Definir e obter variável de ambiente

Para definir uma variável de ambiente e recuperá-la no Teams, você pode aproveitar o arquivo `.env` interno. O código a seguir é usado para definir a variável de ambiente em `.env`:

```
# .env

TENANT_KEY=foobar
```

Para passar o conteúdo do arquivo `.env` para nosso aplicativo do lado do cliente, `webpack.config.js` `webpack` você precisa configurá-lo para que ele possa ser acessado em runtime. Use o código a seguir para adicionar a variável de ambiente de `.env`:

```js
// webpack,config.js

webpack.EnvironmentPlugin({
    PUBLIC_HOSTNAME: undefined,
    TAB_APP_ID: null,
    TAB_APP_URI: null,
    REACT_APP_TENANT_KEY: JSON.stringify(process.env.TENANT_KEY) // Add environment variable here
}),
```

Você pode acessar a variável de ambiente em `Util.ts`

```ts
// Util.ts

tokenProvider: new InsecureTokenProvider(JSON.parse(process.env.REACT_APP_TENANT_KEY!), { id: "user" }),
```

> [!TIP]
> Quando você faz alterações no código, o projeto é recriado automaticamente e o servidor de aplicativos é recarregado. No entanto, se você fizer alterações no esquema de contêiner, elas só entrarão em vigor se você fechar e reiniciar o servidor de aplicativos. Para fazer isso, vá para o Prompt de Comando e pressione Ctrl-C duas vezes. Em seguida, execute `gulp serve` ou `gulp ngrok-serve` novamente.

## <a name="see-also"></a>Confira também

- [Documentação do Azure Fluid Relay](/azure/azure-fluid-relay)

- [Documentação do Fluid Framework](https://fluidframework.com/docs/)
- [Repositório GitHub de exemplos fluidos](https://github.com/microsoft/FluidExamples)
