## <a name="establish-a-secure-tunnel-to-your-tab"></a>Estabelecer um túnel seguro para sua guia

O Microsoft Teams é um produto totalmente baseado em nuvem e exige que o conteúdo da guia esteja disponível na nuvem usando pontos de extremidade HTTPS. O Microsoft Teams não permite hospedagem local. Você precisará publicar sua guia em uma URL pública ou usar um proxy que exporá sua porta local para uma URL voltada para a Internet.

Para testar sua guia, você usará o [ngrok](https://ngrok.com/docs). Os pontos de extremidade da Web do seu servidor estarão disponíveis enquanto o ngrok estiver em execução no computador local. Se você fechar ngrok, as URLs serão diferentes na próxima vez que você iniciá-la.