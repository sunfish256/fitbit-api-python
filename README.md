# fitbit-api-python
For HR/HRV data extraction

## Preperation
### 1. create a fitbit account
Create an account at https://accounts.fitbit.com/signup  
Most likely you have already created an account since the initial setup of your Fitbit device requires it. Please log in with that account.  

### 2. Register an app that uses the Web API
Register your app at https://dev.fitbit.com/apps  
You can check the app information later, so it is a good idea to bookmark it.  

Click Register a new app in the upper right corner.

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/8b148f87-8b0f-42bc-9abd-e9d283993122)

There are many fields for entering URLs, but if the program is just using requests to run the API, as in this case, the URL fields other than Redirect URL are fine with `http://localhost`.

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/f02186fd-7fc0-4b67-bdd2-c9d40b29695d)

- Application Name: Any
- Description: Any 10 characters or more.
- Application Website URL: `http://localhost`
- Organization: Any
- Organization Website URL: `http://localhost`
- Terms of Service URL: `http://localhost`
- Privacy Policy URL: `http://localhost`
- OAuth 2.0 Application Type: Choose "Personal"
- Redirect URL: `http://localhost:8000` (Any available port)
- Default Access Type: Choose "Read Only"

After pressing the "Register" button, the following page will be displayed.  

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/76ca9c80-8b7a-4f2f-bd5f-0cafdcc36712)

The registered information is displayed, and the Client ID and Client Secret are issued.  
This screen can be viewed at any time later.  

Click "OAuth2.0 Tutorial" in the lower left corner to issue access token.  

### 3. Issuance of access token
Issue an access token by following the instructions on the tutorial's web screen.  
Note the two "Access Token" and "Refresh Token" that appear at the end.  

Select "Client (for client-side access)" for Application Type.  

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/7285adad-6449-4b73-829a-5c11cbd6f4b6)

Generate the information needed to issue an access token. Press the green Generate button in two places.  
Two strings will be generated, but they are temporary and do not need to be kept.  

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/5c5102ea-fb78-42a6-8feb-ec83c1b42009)

Uncheck the items you do not allow to be retrieved from the API (optional).  
Then click on Authorization URL.  

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/a9cf2f71-de88-4dc1-a39c-0f934fc88911)

The authorization page will open automatically.  
Make sure there are no items you excluded earlier, check "Allow all" and press "Permission" button.  

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/32870d2f-f4d5-448b-90b7-a6991b1ab66d)

Then, `http://localhost:8000/` specified in the Redirect URL will open.  
You will see the message "This site cannot be accessed." Please copy the URL without closing it.  

Paste the URL you have just entered in the red frame of the image below.  
Then, the "Authorization Code" and "State" will be extracted from the URL and displayed.  
There is no need to write down either of these values.  

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/ff822549-88a8-4451-b328-876d91dcf6e7)

The request is automatically generated based on the URL above. Press the green button.  
If no errors are displayed in the text area below, you are OK.  

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/860e6ba0-b52f-498b-b5fa-bfba09fcea7a)

**Be sure to note the Access Token and Refresh Token.**  
The Access Token is used to run the API. This Token has a lifespan of 8 hours, so when it expires, the Access Token is reissued using Refresh Token.

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/ad226a3d-94df-42b8-92a1-e11ffc4c6aae)

## Running Web APIs in Python
Save it under the name `fb_conf.json`.
```
{
  "client_id": "YOUR_CLIENT_ID",
  "access_token": "YOUR_ACCESS_TOKEN",
  "refresh_token": "YOUR_REFRESH_TOKEN"
}
```
Fill in the token obtained in [3. Issuance of access token](#3-issuance-of-access-token).  
"client_id" can be found on the https://dev.fitbit.com/apps by clicking on the registered app.  
Since the access token is automatically renewed by the application, it does not matter if it has expired.  

![image](https://github.com/sunfish256/fitbit-api-python/assets/84883098/2ea8e312-0c8b-47e5-8643-57734b2753bb)

