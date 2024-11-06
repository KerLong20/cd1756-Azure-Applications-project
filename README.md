Resource Group
Resource Group Name: cms
2. SQL Database
DB name: cms
Server: cms1234.database.windows.net
DB region: us-east
Admin login: cmsadmin
Admin password: CMS4dmin
Resource group: cms
DB workload env: Development
DB compute + storage: DTU - Basic
Press the "Next: Networking" button, then select "Public Endpoint", and set both of the Firewall rules that appear to "Yes".
Set everything else to default
Run SQL queries in sql_scripts/ directory after completion, starting from the users table. Don't forget to take screenshots.
3. Storage Account
Resource group: cms
Storage account name: images12323 (needs to be unique)
Advanced - Allow enabling anonymous access on individual containers: Enable
Advanced - Access tier: Cool
Network access: Enable public access from all networks (the default)
Create container named "images". Set its access level to Container.
From Security + networking > Access keys:
Blob Storage key: MhsilJmue0ciQnD8zVOGZa7i8YlZcknSz3LiF1vf2mNJCChyvJY6yEnCHVKPNUpjAiKPfa+q9k0a+ASt/n+5jQ==

4. Microsoft Entra ID
4.1. App Registration
Name: cmsEntraID
Who can use? "Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)"
4.2. Secret Creation
Secret description: cmsSecret
Secret Key: 3a51cadc-dc5f-4503-959d-d4286f24d7a4
Client Secret: wN48Q~SVo5ecjrNs-Fac1wvs9cRVgXVYPxEmjc.r
Application (client) ID: 1660e7a3-74ae-4945-aea0-5bd962871c33

Application
Name: udacitycms.azurewebsites.net
Runtime stack: Python 3.10
Pricing Plan: Free F1
If you are getting a "Validation failed for a resource" error, pick a different region.
After creation:

Settings -> Environment variables - Add the following variables (sample values are included, replace them with your values):
BLOB_ACCOUNT: image11
BLOB_CONTAINER: images
BLOB_STORAGE_KEY: MhsilJmue0ciQnD8zVOGZa7i8YlZcknSz3LiF1vf2mNJCChyvJY6yEnCHVKPNUpjAiKPfa+q9k0a+ASt/n+5jQ==

SQL_SERVER: cms1234.database.windows.net
SQL_DATABASE: cms
SQL_USER_NAME: cmsadmin
SQL_PASSWORD: CMS4dmin
CLIENT_SECRET: liK8Q~KDwIGaXpH1UaR-RS3W0Bk8-apIqD32ectH
SECRET_KEY: ac2df92a-66cf-4f47-875b-f5d027c33934
CLIENT_ID: 4cec6730-afad-4714-b5bb-9b2c6666eaba
Deployment Center
Source: GitHub
Pick the repo that contains the starter files.
6. Setting up OAuth2
At this point, your application should already be running. You should already be able to log in with username admin and password pass and you can create new posts or update existing ones.

The next part is getting the OAuth2 login to work.

Go to Microsoft Entra ID > App Registrations, click on the App Registration created earlier, and then pick Authentication from the left sidebar.

6.1. Microsoft Entra ID - Authentication - Add a Platform - Web
Redirect URIs: https://[IP ADDRESS FROM VM or WEB APP ADDRESS]/getAToken
logout URL: https://[IP ADDRESS FROM VM or WEB APP ADDRESS]/login
