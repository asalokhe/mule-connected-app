# mule-connected-app
  Application demonstrating the connected app functionality.

- The use of connected apps comes side by side with the last version of Mule Maven Plugin, so you will need to use the version 3.4.0 or higher. 

- Why connected Apps?

Before Connected Apps, credentials for a service account were stored in the CI/CD pipeline code. With Connected apps, there is no concept of a service account anymore.


| Parameter | Description |	Required |
|----------|-------------|-----------|
| connectedAppClientId | Specifies the Connected App clientID value | Only when using Connected Apps credentials to login.|
| connectedAppClientSecret | Specifies the Connected App secret key. | Only when using Connected Apps credentials to login.|
| connectedAppGrantType | Specifies the only supported connection type: client_credentials. | Only when using Connected Apps credentials to login.|

## Prerequisite:
1. Create a connected app with required scope.

   Note that the connected App credentials must have the **Design Center Developer** access scope.
2. Mule application cloudHubDeployment configuration with connectedApp settings. 
```sh
    <configuration>
        <cloudHubDeployment>
            <uri>https://anypoint.mulesoft.com</uri>
            <muleVersion>${app.runtime}</muleVersion>
            <connectedAppClientId>${client.id}</connectedAppClientId>
            <connectedAppClientSecret>${client.secret}</connectedAppClientSecret>
            <connectedAppGrantType>${grant.type}</connectedAppGrantType>
            <environment>${environment}</environment>
            <objectStoreV2>true</objectStoreV2>
            <properties>
            <key>value</key>
            </properties>
        </cloudHubDeployment>
    </configuration>
```

### Deploy application to cloudhub by using Connected App. 
```sh
    mvn clean package deploy -DmuleDeploy 
        -Dapp.runtime=<<Runtime-Version>> \
        -Dclient.id="<connected-app-client-id>" \
        -Dclient.secret="<connected-app-client-secret>" \
        -Dgrant.type="client_credentials" \
        -Dcloudhub.application.name="<<Unique-app-Name>>" \
        -Denvironment=<<Environment>>
```

## References:
-   https://docs.mulesoft.com/access-management/connected-apps-overview
-   https://help.mulesoft.com/s/article/How-to-use-Connected-Apps-with-CI-CD
-   https://docs.mulesoft.com/exchange/to-publish-assets-maven#publish-and-consume-federated-assets
-   https://docs.mulesoft.com/mule-runtime/4.4/deploy-to-cloudhub

