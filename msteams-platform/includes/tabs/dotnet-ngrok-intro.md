## <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

Microsoft Teams é um produto baseado em nuvem e exige que o conteúdo da guia seja disponibilizado na nuvem usando pontos de extremidade HTTPS. Teams não permite hospedagem local. Você deve publicar sua guia em uma URL pública ou usar um proxy que exponha sua porta local a uma URL voltada para a Internet.

Para testar sua guia, use [ngrok](https://ngrok.com/docs). Os pontos de extremidade da Web do seu servidor estão disponíveis enquanto o ngrok está em execução no computador. Na versão gratuita do ngrok, se você fechar o ngrok, as URLs serão diferentes na próxima vez em que você a iniciar.