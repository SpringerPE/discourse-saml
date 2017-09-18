### discourse-saml

A Discourse Plugin to enable authentication via SAML

Setting up your idp:
The entity-id should be: https://discourse.example.com
The consumer assertion service url should be: https://discourse.example.com/auth/saml/callback

For idp-initated SSO, use the following URL: https://discourse.example.com/auth/saml/callback

### Configuration

For Docker based installations:

Add the following settings to your `app.yml` file in the Environment Settings section:
```
FORCE_HTTPS: true
DISCOURE_SAML_FULL_SCREEN_LOGIN: true
DISCOURE_SAML_TARGET_URL: "https://vendor/saml/login/"
DISCOURE_SAML_REQUEST_METHOD: "post"
DISCOURE_SAML_BUTTON_TITLE: "Login with SSO"
DISCOURE_SAML_CERT: "-----BEGIN CERTIFICATE----- ??? -----END CERTIFICATE-----"
DISCOURE_SAML_SP_CERTIFICATE: "-----BEGIN CERTIFICATE----- ??? -----END CERTIFICATE-----"
DISCOURE_SAML_SP_PRIVATE_KEY: "-----BEGIN RSA PRIVATE KEY----- ??? -----END RSA PRIVATE KEY-----"
```

The `DISCOURSE_FULL_SCREEN_LOGIN` option allows the SSO login page to be presented within the main browser window, rather than a popup. If SAML is your only authentication method this can look neater, as when the user clicks the Log In button the login page will follow through within the main browser window rather than opening a pop-up. This setting is commented out by default - if you want full screen login uncomment that line and set the value to true (as per the example above).

For non docker:

Add the following settings to your `discourse.conf` file:

- `saml_target_url`

### Convering an RSA Key to a PEM

If the idp has an RSA key split up as modulus and exponent, this javascript library makes
it easy to convert to pem:

https://www.npmjs.com/package/rsa-pem-from-mod-exp

### License

MIT

