# fitbit-api-python
For HR/HRV data extraction

## Preperation
1. create a fitbit account
Create an account at https://accounts.fitbit.com/signup. Most likely you have already created an account since the initial setup of your Fitbit device requires it. Please log in with that account.

2. Register an app that uses the Web API
Register your app at https://dev.fitbit.com/apps. You can check the app information later, so it is a good idea to bookmark it.

Click Register a new app in the upper right corner.

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/8b148f87-8b0f-42bc-9abd-e9d283993122)

There are many fields for entering URLs, but if the program is just using requests to run the API, as in this case, the URL fields other than Redirect URL are fine with `http://localhost`.

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/f02186fd-7fc0-4b67-bdd2-c9d40b29695d)

- Application Name: Any
- Description: Any 10 characters or more.
- Application Website URL: http://localhost
- Organization: Any
- Organization Website URL: http://localhost
- Terms of Service URL: http://localhost
- Privacy Policy URL: http://localhost
- OAuth 2.0 Application Type: Choose "Personal"
- Redirect URL: http://localhost:8000 (Any available port)
- Default Access Type: Choose "Read Only"

After pressing the "Register" button, the following page will be displayed.

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/76ca9c80-8b7a-4f2f-bd5f-0cafdcc36712)

The registered information is displayed, and the Client ID and Client Secret are issued. This screen can be viewed at any time later.

Click "OAuth2.0 Tutorial" in the lower left corner to issue access token.

3. Issuance of access token
