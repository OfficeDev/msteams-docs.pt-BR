## <a name="prerequisites"></a>Pré-requisitos

- Para concluir este QuickStart, você precisará de um locatário do Office 365 e de uma equipe configurada para *permitir o carregamento de aplicativos personalizados* habilitados. Para saber mais, confira [preparar seu locatário do Office 365](~/concepts/build-and-test/prepare-your-o365-tenant.md).
  - Se você não tiver uma conta do Office 365, você poderá inscrever-se em uma assinatura gratuita por meio do [programa de desenvolvedor do Office 365](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program). A assinatura permanecerá ativa, contanto que você esteja usando-a para desenvolvimento contínuo.

- Você usará o app Studio para importar o aplicativo para o Microsoft Teams. Para instalar o app Studio **** ![selecionar aplicativo](~/assets/images/tab-images/storeApp.png) da loja de aplicativos no canto inferior esquerdo do aplicativo Teams e pesquise o app Studio. Depois de localizar o bloco, selecione-o e escolha instalar na caixa de diálogo janela pop-up.

Além disso, este projeto requer que você tenha o seguinte instalado em seu ambiente de desenvolvimento:

- A versão atual do Visual Studio IDE com a carga de trabalho de **desenvolvimento entre plataformas do .NET Core** instalada. Se você ainda não tem o Visual Studio, é possível baixar e instalar a versão mais recente [da comunidade Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads) gratuitamente.

- A ferramenta de proxy reverso do [ngrok](https://ngrok.com) . Você usará o ngrok para criar um encapsulamento para os pontos de extremidade HTTPS disponíveis publicamente do servidor Web em execução. Você pode [baixá-lo aqui](https://ngrok.com/download).
