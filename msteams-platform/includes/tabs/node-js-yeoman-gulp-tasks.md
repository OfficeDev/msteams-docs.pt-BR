## <a name="create-the-app-package"></a>Criar o pacote do aplicativo

Você precisará de um pacote de aplicativos para testar sua guia Teams. É uma pasta zip que contém os seguintes arquivos necessários:

- Um **ícone de cor completo** medindo 192 x 192 pixels.
- Um **ícone de contorno transparente** medindo 32 x 32 pixels.
- Um **manifest.json** que especifica os atributos do seu aplicativo.

O pacote é criado por meio de uma tarefa gulp que valida o manifest.jsno arquivo on e gera a pasta zip no `./package directory` arquivo . No prompt de comando, digite:

```bash
gulp manifest
```

## <a name="build-your-application"></a>Criar seu aplicativo

O comando build transpila sua solução para a *pasta ./dist.* Em seguida, digite:

```bash
gulp build
```

## <a name="run-your-application-in-localhost"></a>Executar seu aplicativo no localhost

Inicie um servidor Web local inserindo o seguinte:

```bash
gulp serve
```

Insira `http://localhost:3007/<yourDefaultAppNameTab>/` no navegador e veja a home page do aplicativo:

![captura de tela da home page](~/assets/images/tab-images/homePage.png)