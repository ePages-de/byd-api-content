### Authentication

Your app cannot access merchant data without getting authorisation
first. In this section we will help you through this authorisation
process.

#### Prerequisites

In order to make API calls against the Beyond API, you should have been
through the steps of creating a [custom
app](#authentication-private-apps). Only then, you can go ahead and
implement OAuth 2.0 to issue access tokens on behalf of our merchants.

#### Authorization process

In the below flow chart, we've outlined how we use OAuth 2.0.

![OAuthFlow](https://s3.amazonaws.com/user-content.stoplight.io/7749/1542623280679)

You might want to look at some terms that we've introduced in the chart.

| Name                              | Description                       |
|-----------------------------------|-----------------------------------|
| **Merchant**                      | A shop owner giving permission to an **App** to access their shop's data through the REST API. Within the OAuth 2.0 protocol this is referred to as **resource owner**. |
| **ePages**                        | This is where the **App** can view and modify a shop's data by accessing the REST API. Within the OAuth 2.0 protocol this is referred to as **service provider**. |
| **App**                           | An application that would like to access a shop's data. The **Merchant** must grant permission before the **App** can access any data. Within the OAuth 2.0 protocol this is referred to as **client**.  |


Now, let's go through the authorization process together:

**1. Obtain user's consent**

Once a merchant has decided to install your application, they have to
grant your app the permissions that you've selected during app creation.
ePages will display a user consent form to the merchant, and also prompt
them to either install the app or cancel the process.

**2. Confirm app installation**

If the merchant chose to install your application, they will be
redirected to the app's **Application Callback URL**.

**3. Receive authorization code**

ePages makes a `GET` request to the **Application Callback URL**. The
required query parameters that we've outlined in the table below will be
automatically passed by ePages.

> **Note**
>
> SSL required! All API access is over HTTPS.

    GET/callback?code={code}&signature={signature}&return_url={return_url}&api_url={api_url}&access_token_url={access_token_url} HTTP/1.1
    Host: crazytoppingapp.com

Substitutions would be made as given in this example table:

| Query parameter       | Description           | Example               |
|-----------------------|-----------------------|-----------------------|
| {`code`}              | The authorization code that is required for the app installation process to obtain the `access_token`. | f32ddSbuff2IGAYvtiwYQiyHyuLJWbey |
| {`api_url`}           | The base API URL, that uniquely identifies the merchant. The `api_url` differs for every merchant and has to be stored in the app. | https://api-shop.beyondshop.cloud/api  |
| {`return_url`}        | The URL that the merchant should be redirected to after the app installation.     | https://api-shop.beyondshop.cloud/cockpit   |
| {`access_token_url`}  | The URL to obtain the `access_token`. | https://api-shop.beyondshop.cloud/api/oauth/token  |
| {`signature`}         | The signature is a message authentification code. It is calculated with the `code`, `access_token_url` and `client_secret`.      | jEPRUggebJDBsEnl1%2FpHlMUBxPbsELQihEVzbx2FlM%3D  |


Your app can use the code in combination with your `client_id` and
`client_secret` for obtaining an `access_token`. This code is temporary
and will be obsolete after app installation. Although it is optional to
validate the `signature` query parameter, we highly recommend to do so,
in order to verify that your request was not changed, and for sure has
been provided by ePages and no external, insecure party.

In order to understand how to verify the signature, see the following
Java code example:

    {
    import javax.crypto.Mac;
    import javax.crypto.spec.SecretKeySpec;
    import org.apache.commons.codec.CharEncoding;

    public String calculateSignature(String authCodeValue, String authTokenUrl, String secret) {
        String hmacAlgorithm = ""HmacSHA1"";

        final Mac mac = Mac.getInstance(HmacSHA1);
        mac.init(new SecretKeySpec(secret.getBytes(CharEncoding.UTF_8), HmacSHA1));

        byte[] signature = mac.doFinal((authCodeValue + ":" + authTokenUrl).getBytes());
        return Base64.getEncoder().encodeToString(signature);
    }

**4. Registration (optional)**

If your application requires a registration process, this optional step
can be included before obtaining the `access_token`. Meanwhile, the app
would display the registration or login form to the merchant.

![Registration](https://s3.amazonaws.com/user-content.stoplight.io/7749/1542623509025)

**5. Exchange authorization code for access token**

To receive an `access_token`, make a `POST` request to create a
JsonWebToken using the `authorization_code` grant type:

> **Important**
>
> With this `access_token` you make authenticated requests to the shop's
> data. Store the `access_token` securely. It is only valid for the
> current shop, i.e. you should also store the `api_url` along with the
> `access_token`.

What's more, your `access_token` only has a limited lifetime. The
returned `expires_in` parameter indicates that.

You need to ensure that you obtain a renewed `access_token` when the
current token has expired:

The `refresh_token` from the response has to be stored as well in order
to obtain a renewed `access_token`.

Here's an example of how to manage the data of different merchants:


| `api_url`   | Shop        | `access_token` | `expires_in` | `refresh_token`  |
|-------------|-------------|----------------|--------------|------------------|
| https://api-shop.beyondshop.cloud | API Shop    | eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IjEifQ.eyJzY29wZSI6WyJ1c2VyOnIiXSwidGVuYW50SWQiOjEzNSwiZXhwIjoxNTMwODI1NzIyLCJpYXQiOjE1MzA3ODI1MjIsImp0aSI6IjE5MDE4Mzg0LTNiZTEtNDdhYy1hYTAwLTJjZjNiZWUyYzFlNSIsImNsaWVudF9pZCI6IjJjYjczYzk1LTlmOTEtNDEwNi1iMzdiLWVmN2E2YTBlM2U1ZSJ9.WWgQi7ZGk1ePpvDEhIa7LipkfAN6jwyir1JJrHuxcNVJSIDE63zSBktLCbz_NUAYSommxbMwmWumB5Ah1J51dYNz5UryUagbSMSTI_9pP_WWKMaZ_7E2w4TKjpqSPod8QUUj1RszAGjPseF309st3lrN6xbem6XdGsESIradWrePmcvTovZz8EBoy7GqWZA0Yses_HKfH_Fh3DVOxHavf-iu0m6zm97KBAlWkUXR1HrTG8Q6FFZjPldUg7jBS8wfsmqJTBsGaPfHN5xgLqElBTuGbBBzjG2kae99L8bmPnd00HEG1| 43199       | eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IjEifQ.eyJzY29wZSI6WyJ1c2VyOnIiXSwiYXRpIjoiMTkwMTgzODQtM2JlMS00N2FjLWFhMDAtMmNmM2JlZTJjMWU1IiwidGVuYW50SWQiOjEzNSwiaWF0IjoxNTMwNzgyNTIyLCJqdGkiOiI0YzE4YzQ1My00MDg3LTQ3YmEtYTZjZi0xMTBmYTk3NWI0ZjYiLCJjbGllbnRfaWQiOiIyY2I3M2M5NS05ZjkxLTQxMDYtYjM3Yi1lZjdhNmEwZTNlNWUifQ.SZYnVPCZgUDj1kOu_HWVoYapeIvEB4kbgWs6wMkFaIG9ztARajO7vrdHqKu34LH8nI1WSxAEPuQQzSG8y60B8j8l0jp4tMD-3NGvIpkjh0_90_0SlIJF7g—iBCtLoImVODl562jJTV82OOW5MBo31gF6x_qOwCtKx1WQcjK1xwjxK7FdzZ7spzYYj2uD9ocexRrt462VQDA8IIll79RFEyhdkNT44X_bS7wUU0AswVNJxvOrNeEBSza3G7tBJr5z5jMSY0NFHh41cH2Ix-c0AzC0R6FNK_afSlfr65i7RGTzO14OSWy-tYWbvSSlJ5gcjGpvh_slGUJOW4f60qCrg |
| https://quarkyaustrian.beyondshop.cloud  |QuarkyAustrian|eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IjEifQ.eyJzY29wZSI6WyJ1c2VyOnIiXSwidGVuYW50SWQiOjEzNSwiZXhwIjoxNTMwODI1NzIyLCJpYXQiOjE1MzA3ODI1MjIsImp0aSI6IjE5MDE4Mzg0LTNiZTEtNDdhYy1hYTAwLTJjZjNiZWUyYzFlNSIsImNsaWVudF9pZCI6IjJjYjczYzk1LTlmOTEtNDEwNi1iMzdiLWVmN2E2YTBlM2U1ZSJ9.WWgQi7ZGk1ePpvDEhIa7LipkfAN6jwyir1JJrHuxcNVJSIDE63zSBktLCbz_NUAYSommxbMwmWumB5Ah1J51dYNz5UryUagbSMSTI_9pP_WWKMaZ_7E2w4TKjpqSPod8QUUj1RszAGjPseF309st3lrN6xbem6XdGsESIradWrePmcvTovZz8EBoy7GqWZA0Yses_HKfH_Fh3DVOxHavf-iu0m6zm97KBAlWkUXR1HrTG8Q6FFZjPldUg7jBS8wfsmqJTBsGaPfHN5xgLqElBTuGbBBzjG2kae99L8bmPnd00HEG1eIVyokXy30y1GIo3kd4oONcpZGtBhh-r_FdCg|259199|eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IjEifQ.eyJzY29wZSI6WyJ1c2VyOnIiXSwiYXRpIjoiMTkwMTgzODQtM2JlMS00N2FjLWFhMDAtMmNmM2JlZTJjMWU1IiwidGVuYW50SWQiOjEzNSwiaWF0IjoxNTMwNzgyNTIyLCJqdGkiOiI0YzE4YzQ1My00MDg3LTQ3YmEtYTZjZi0xMTBmYTk3NWI0ZjYiLCJjbGllbnRfaWQiOiIyY2I3M2M5NS05ZjkxLTQxMDYtYjM3Yi1lZjdhNmEwZTNlNWUifQ.SZYnVPCZgUDj1kOu_HWVoYapeIvEB4kbgWs6wMkFaIG9ztARajO7vrdHqKu34LH8nI1WSxAEPuQQzSG8y60B8j8l0jp4tMD-3NGvIpkjh0_90_0SlIJF7g—iBCtLoImVODl562jJTV82OOW5MBo31gF6x_qOwCtKx1WQcjK1xwjxK7FdzZ7spzYYj2uD9ocexRrt462VQDA8IIll79RFEyhdkNT44X_bS7wUU0AswVNJxvOrNeEBSza3G7tBJr5z5jMSY0NFHh41cH2Ix-c0AzC0R6FNK_afSlfr65i7RGTzO14OSWy-tYWbvSSlJ5gcjGpvh_slGUJOW4f60qCrg|
|  https://tastyflummery.beyondshop.cloud   |  TastyFlummery   | eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IjEifQ.eyJzY29wZSI6WyJ1c2VyOnIiXSwidGVuYW50SWQiOjEzNSwiZXhwIjoxNTMwODI1NzIyLCJpYXQiOjE1MzA3ODI1MjIsImp0aSI6IjE5MDE4Mzg0LTNiZTEtNDdhYy1hYTAwLTJjZjNiZWUyYzFlNSIsImNsaWVudF9pZCI6IjJjYjczYzk1LTlmOTEtNDEwNi1iMzdiLWVmN2E2YTBlM2U1ZSJ9.WWgQi7ZGk1ePpvDEhIa7LipkfAN6jwyir1JJrHuxcNVJSIDE63zSBktLCbz_NUAYSommxbMwmWumB5Ah1J51dYNz5UryUagbSMSTI_9pP_WWKMaZ_7E2w4TKjpqSPod8QUUj1RszAGjPseF309st3lrN6xbem6XdGsESIradWrePmcvTovZz8EBoy7GqWZA0Yses_HKfH_Fh3DVOxHavf-iu0m6zm97KBAlWkUXR1HrTG8Q6FFZjPldUg7jBS8wfsmqJTBsGaPfHN5xgLqElBTuGbBBzjG2kae99L8bmPnd00HEG1eIVyokXy30y1GIo3kd4oONcpZGtBhh-r_FdCg  | 604800 | eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IjEifQ.eyJzY29wZSI6WyJ1c2VyOnIiXSwiYXRpIjoiMTkwMTgzODQtM2JlMS00N2FjLWFhMDAtMmNmM2JlZTJjMWU1IiwidGVuYW50SWQiOjEzNSwiaWF0IjoxNTMwNzgyNTIyLCJqdGkiOiI0YzE4YzQ1My00MDg3LTQ3YmEtYTZjZi0xMTBmYTk3NWI0ZjYiLCJjbGllbnRfaWQiOiIyY2I3M2M5NS05ZjkxLTQxMDYtYjM3Yi1lZjdhNmEwZTNlNWUifQ.SZYnVPCZgUDj1kOu_HWVoYapeIvEB4kbgWs6wMkFaIG9ztARajO7vrdHqKu34LH8nI1WSxAEPuQQzSG8y60B8j8l0jp4tMD-3NGvIpkjh0_90_0SlIJF7g—iBCtLoImVODl562jJTV82OOW5MBo31gF6x_qOwCtKx1WQcjK1xwjxK7FdzZ7spzYYj2uD9ocexRrt462VQDA8IIll79RFEyhdkNT44X_bS7wUU0AswVNJxvOrNeEBSza3G7tBJr5z5jMSY0NFHh41cH2Ix-c0AzC0R6FNK_afSlfr65i7RGTzO14OSWy-tYWbvSSlJ5gcjGpvh_slGUJOW4f60qCrg |


**6. Redirect the merchant**

Once you're through this process, your app has to send the merchant back
to the `return_url` the app received before.

**Make authenticated API requests**

Now that your application has received an `access_token`, it can make
authenticated requests to the Beyond API, and thus access the shop's
data as long as the app is installed in the shop.

Example:

**Reinstalling an app**

It might happen that merchants uninstall and re-install your app. A
common action taken by developers is to delete all merchant records
after an app was uninstalled. This is not recommended, since there are
situations where a merchant has uninstalled an app, but realizes that
they need to re-install it. It's better to keep the shop's data than to
duplicate them with app reinstallation. Your app can use the old access
token in order to request the shop's data again. If the access token
expired, use the refresh token to get a new one.

