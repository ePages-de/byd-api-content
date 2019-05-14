#### How to send test requests via the UI

You can easily make test requests via the UI of the Beyond API documentation.

From the sidebar in the area **BEYOND REST API** select **API Reference**. Navigate to **oauth** and select the endpoint [Create a JSON Web Token with a refresh token](https://beyond.docs.stoplight.io/beyond-rest-api/api-reference/oauth/oauth2-token-refresh).
At the bottom of the page you will find the section **Send a Test Request**.

1. Enter your *client_id* in the field **username**, and your *client_secret* in the field **password**.

2. Enter the hostname of your shop in the field **host**.

3. Select the tab **Query** and enter the string *client_credentials* in the field **grant_type**.

4. Select **Send**. Your access token will be displayed in the response body.

All resources that you're allowed to interact with from your granted scopes and that require authentication have a dedicated **oauth_access_token** field in the **Send a Test Request** section.
The token you've received will automatically appear in all these sections for the rest of your session.