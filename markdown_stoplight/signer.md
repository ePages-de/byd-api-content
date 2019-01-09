### Signers

Signers enable your app to verify that requests to your app are
originating from ePages.

Signers are created for a specific client and shop. If your app created
at least one signer for a shop, the header `X-EPAGES-SIGNATURE` will be
added to all requests that ePages executes towards your app for that
shop, e.g. triggering webhook callbacks or initiating payment flows.

The format of the signature header is as follows:

``` {.bash}
X-EPAGES-SIGNATURE: $signature
```

Where `$signature` is the calculated signature. A request can be
considered originated from ePages, when at least one of the header
signatures matches any of the signatures your app calculated with the
shared secrets. If multiple signers exist, one `X-EPAGES-SIGNATURE`
header is set per signer, e.g.:

``` {.bash}
X-EPAGES-SIGNATURE: Lg2rSDBBUVG9yDNQR5++Dz++esE=
X-EPAGES-SIGNATURE: f31fyeVnbmdIpb8hJzdJJ2UA92M=
```

Java example code to calculate the signature:

``` {.java}
import static java.nio.charset.StandardCharsets.UTF_8;
import java.util.Base64;
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;

String ALGORITHM = "HmacSHA1";

String calculateSignature(String data, String sharedSecret) {

    SecretKeySpec keySpec = new SecretKeySpec(sharedSecret.getBytes(UTF_8),
                                              ALGORITHM);
    Mac mac = Mac.getInstance(ALGORITHM);
    mac.init(keySpec);

    return Base64.getEncoder().encodeToString(mac.doFinal(data.getBytes(UTF_8)));
}
```

For requests that have a request body, the data to be signed is the
request URI and request body concatenated with a colon. For requests
that do not have a request body, the data to be signed is just the
request URI.

``` {.java}
String data = requestUri + ":" + requestBody;
String signature = calculateSignature(data, sharedSecret);
```

#### List signers

A `GET` request is used to list all signers.

#### Create signer

A `POST` request is used to create a signer. You cannot create more than
two signers at once.

#### Delete signer

A `DELETE` request is used to delete a signer. If at least one signer
has been created, you cannot delete the last signer.

