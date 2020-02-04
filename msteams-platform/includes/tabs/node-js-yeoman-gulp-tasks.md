## <a name="create-the-app-package"></a>Criar o pacote de aplicativos

Você precisará de um pacote de aplicativos para testar sua guia no Microsoft Teams. É uma pasta zip que contém os seguintes arquivos necessários:

- Um **ícone de cor completa** medindo 192 x 192 pixels.
- Um **ícone de contorno transparente** medindo 32 x 32 pixels.
- Um arquivo **manifest. JSON** que especifica os atributos do seu aplicativo.

O pacote é criado por meio de uma tarefa Gulp que valida o arquivo manifest. JSON e gera a pasta zip no `./package directory`. No prompt de comando, digite:

```bash
gulp manifest
```

## <a name="build-your-application"></a>Criar seu aplicativo

O comando Build compila sua solução na pasta *. pasta/dist.* . Em seguida, digite:

```bash
gulp build
```

## <a name="run-your-application-in-localhost"></a>Executar o aplicativo no localhost

Inicie um servidor Web local, inserindo o seguinte:

```bash
gulp serve
```

Insira `http://localhost:3007/<yourDefaultAppNameTab>/` no navegador e exiba a página inicial do aplicativo:

![captura de tela da Home Page](~/assets/images/tab-images/homePage.png)