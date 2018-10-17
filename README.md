# zendesk


# Get Token via curl

1. get token from browser // SUBDOMAIN && CLIENT_ID
https://www.zopim.com/oauth2/authorizations/new?response_type=token&redirect_uri=http%3A%2F%2Flocalhost%3A8080&client_id=CLIENT_ID&scope=read%20write%20chat&subdomain=SUBDOMAIN

2. get client ID  // TOKEN

```
curl https://www.zopim.com/api/v2/oauth/clients -H "Authorization: Bearer TOKEN"
```
   response get client's ID

3. update client_type as confidential // ID && TOKEN

```
curl https://www.zopim.com/api/v2/oauth/clients/ID 3 -d '{"client_type": "confidential"}' \
 -X PUT -H "Content-Type: application/json" -H "Authorization: Bearer TOKEN"
 ```

4. get token from curl response (the way to refresh token) // CLIENT_ID && CLIENT_SECRET
```
curl https://www.zopim.com/oauth2/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d 'grant_type=client_credentials&client_id=CLIENT_ID&client_secret=CLIENT_SECRET' \
  -X POST
 ```
