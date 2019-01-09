#### Custom Apps

Custom apps can interact with the Beyond API on behalf of a single
beyondshop. Once you have [signed up for a
beyondshop](https://signup.beyondshop.cloud/) you can create custom apps
for a specific shop, and only for that shop.

**1. Generate credentials**

Before you can authenticate with a custom app to a beyondshop, you need
to generate the required credentials from the cockpit of the shop you
want to connect with your app.

To generate the required credentials:

1.  From your beyondshop cockpit, select **Custom apps**.

2.  Select **Create custom app**.

3.  Enter your app name, and select the scopes that outline the
    permissions, and access required by your app.

4.  Select **Save**.

You immediately receive your client credentials with a `client_id` and a
`client_secret`. Store the `client_secret` safely, as you will not be
able to see it in the **Custom apps** section again, once you revisit
that page.

**2. Authenticate**

To authenticate with the Beyond API, simply
[Create a JsonWebToken from Client Credentials](#resources-tokens-client). Send a `POST` request to the token
endpoint with the `grant_type` parameter. Pass `client_id` and
`client_secret` (that you've received when generating your credentials
in the beyondshop) as Basic Auth header.

Our authorization server will respond with a JSON object amongst others
containing the `access_token` with the value `bearer` that you can now
use for API requests.

**3. Perform authenticated requests**

Now that your application has an `access_token`, it can make
authenticated requests to the Beyond API.

Example:

```
GET https://yourshop.api.urn/products HTTP/1.1
Host: yourshop.com
Accept: application/hal+json
Authorization: Bearer 4HZ9hriF6J3GOnd10JbFzdVehycOvAZf
```

Happy coding!
