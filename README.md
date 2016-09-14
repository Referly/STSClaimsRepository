# STSClaimsRepository
Mattermark's private JWT claims registry

## STS

This is the list of issuers and their public key JWK URIs

* https://sts.mattermark.com
JWK URI: `https://sts.mattermark.com/.well-known/jwks.json`

* https://sts.stagingmark.com
JWK URI: `https://sts.stagingmark.com/.well-known/jwks.json`

* https://dev-sts.mattermark.com
JWK URI: `https://dev-sts.mattermark.com/.well-known/jwks.json`

Publicly defined claims:
* iss - The JWT issuer
* aud - The intended audience(s)(add link to audience section here)
* exp - The token expiration Unix timestamp
* iat - The Unix timestamp when the token was issued
* jti - Unique identifier for the token, can be used to prevent replay attacks for applications needing higher than
normal security levels
* sub - The subject of the token (the unique identifier of the authenticated entity to whom the token refers)


These claims are specific to Mattermark STS token issuers:

* token_use - The permissible use case of the token
* assumed_role - The Access Management Role that the STS has authorized the subject to assume 
* username - The User Pool User's username
* ucd - The User Pool User's create date time
* ulmd - The User Pool User's last modified date time
* enabled - Is the User enabled in the User Pool
* ustatus - The User's status in the User Pool
* email - The User's registered email address
* famname - The User's family name
* givname - The User's given name

### Audience (aud)

Currently the STS will produce tokens with intended audiences that span all of the Mattermark domain namespace
for the environment in which the token was created.

* Production STS will produce `aud` claim with `https://*.mattermark.com`
* Staging STS will produce `aud` claim with `https://*.stagingmark.com`
* Development STS will produce `aud` claim with `https://dev-*.mattermark.com`
* Test STS instances will produce `aud` claim with `https://test-*.mattermark.com`
* CI STS instances will produce `aud` claim with `https://circleci-*.mattermark.com`

### Subject (sub)

For the Mattermark STS the `sub` claim contains the Cognito Identity Id of the authenticated entity to whom the 
STS token refers.

### Token Use (token_use)

For the time being your application should expect and only accept a value of `access` for the `token_use` claim