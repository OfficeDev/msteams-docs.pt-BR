### <a name="optional-adjust-your-browser-launch-settings"></a>(Opcional) Ajustar as configurações de início do navegador

Ao desenvolver um Teams, é comum executar seu aplicativo em um locatário de desenvolvedor alternativo ou com credenciais alternativas.  Tanto Microsoft Edge quanto o Google Chrome fornecem instalações para ajustar as configurações de início do navegador.  Por exemplo, para atualizar o projeto para dar suporte ao modo InPrivate (Microsoft Edge), abra o `.vscode/launch.json` arquivo em seu projeto.  Procure as configurações de início apropriadas e adicione o seguinte bloco a cada um:

``` json
"runtimeArgs": [ "--inprivate" ]
```

Por exemplo, a configuração de início para execução local tem a mesma aparência:

``` json
{
   "name": "Start and Attach to Frontend (Edge)",
   "type": "pwa-msedge",
   "request": "launch",
   "url": "https://teams.microsoft.com/_#/l/app/${localTeamsAppId}?installAppPackage=true",
   "preLaunchTask": "Start Frontend",
   "postDebugTask": "Stop All Services",
   "presentation": {
         "group": "all",
         "hidden": true
   },
   "runtimeArgs": [ "--inprivate" ]
},
```

Como alternativa, você pode configurar seu navegador para usar o último perfil conhecido. [Crie um novo perfil em](https://support.microsoft.com/topic/sign-in-and-create-multiple-profiles-in-microsoft-edge-df94e622-2061-49ae-ad1d-6f0e43ce6435) Microsoft Edge.  Em seguida, ajuste as configurações para usar o último perfil conhecido para novos links:

- Em Microsoft Edge, abra `edge://settings/profiles/multiProfileSettings` .
- Desativar **a alternação automática de perfil**.
- Para o **perfil Padrão para links externos,** selecione Último usado **(padrão)**.

Verifique se o navegador está aberto ao perfil correto antes de depurar seu aplicativo.
