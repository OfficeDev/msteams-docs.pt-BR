## <a name="prerequisites"></a>Pré-requisitos

- Para concluir esse início rápido, você precisará de um locatário Microsoft 365 e uma equipe configurada com Permitir o carregamento de aplicativos *personalizados* habilitados. Para saber mais, consulte [Prepare your Microsoft 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).
  - Se você não tiver uma conta Microsoft 365, poderá inscrever-se para uma assinatura gratuita por meio do [Programa de Desenvolvedores da Microsoft.](https://developer.microsoft.com/en-us/microsoft-365/dev-program) A assinatura permanecerá ativa enquanto você a estiver usando para desenvolvimento contínuo.

- Você usará o App Studio para importar seu aplicativo para Teams. Para instalar o App Studio, selecione **Aplicativo** da Loja de Aplicativos no canto inferior esquerdo do aplicativo ![ Teams e ](~/assets/images/tab-images/storeApp.png) pesquise por App Studio. Depois de encontrar o azulejo, selecione-o e escolha instalar na caixa de diálogo janela pop-up.

Além disso, este projeto exige que você tenha o seguinte instalado em seu ambiente de desenvolvimento:

- A versão atual do Visual Studio IDE com a carga de trabalho de desenvolvimento entre **plataformas .NET CORE** instalada. Se você ainda não tiver uma Visual Studio, poderá baixar e instalar a versão Microsoft Visual Studio Community [versão](https://visualstudio.microsoft.com/downloads) mais recente gratuitamente.

- A [ferramenta proxy reverso ngrok.](https://ngrok.com) Você usará o ngrok para criar um túnel para os pontos de extremidade HTTPS do servidor Web em execução localmente. Você pode [baixá-lo aqui](https://ngrok.com/download).
