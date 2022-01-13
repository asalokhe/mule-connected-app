# mule-connected-app
Application demonstrating the connected app functionality.

mvn clean package deploy -DmuleDeploy -Dapp.runtime=4.4.0 -Dusername="<<username>>" -Dpassword="<<password>>" -Dcloudhub.application.name="<<name>>" -Denvironment=Sandbox


## Pre-req:
- The use of connected apps comes side by side with the last version of Mule Maven Plugin, so you will need to use the version 3.4.0 or higher. 

- Why connected Apps?
    Before Connected Apps, credentials for a service account were stored in the CI/CD pipeline code. With Connected apps, there is no concept of a service account anymore.
    
**Note that the Connected App credentials must have the Design Center Developer access scope.**

|Parameter | Description |	Required |
|----------|-------------|-----------|
| connectedAppClientId | Specifies the Connected App clientID value | Only when using Connected Apps credentials to login.|
| connectedAppClientSecret | Specifies the Connected App secret key. | Only when using Connected Apps credentials to login.|
| connectedAppGrantType | Specifies the only supported connection type: client_credentials. | Only when using Connected Apps credentials to login.|

## References:
- https://help.mulesoft.com/s/article/How-to-use-Connected-Apps-with-CI-CD
- https://docs.mulesoft.com/exchange/to-publish-assets-maven#publish-and-consume-federated-assets