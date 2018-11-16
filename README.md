# zendesk

# demo
![alt text](https://raw.githubusercontent.com/pohsiu/zendesk-chat-api/master/ezgif.com-video-to-gif.gif)

# source 
https://support.zendesk.com/hc/en-us/articles/115010760808-Generating-a-REST-API-token-for-integrated-Chat-accounts

# Get Token via curl

1. get token from browser // SUBDOMAIN && CLIENT_ID
```
https://www.zopim.com/oauth2/authorizations/new?response_type=token&
redirect_uri=http%3A%2F%2Flocalhost%3A8080&
client_id=CLIENT_ID&
scope=read%20write%20chat&
subdomain=SUBDOMAIN
```

2. get client ID  // TOKEN

```
curl https://www.zopim.com/api/v2/oauth/clients -H "Authorization: Bearer TOKEN"
```
   response get client's ID
```
[{
  "id": ID,
  "name": {your client name},
  "company": {company name},
  "client_secret": {client_secret},
  "client_identifier": {client_identifier},
  "client_type": "confidential", 
  "redirect_uris": "http://localhost:8080", 
  "scopes": "read write chat",
  "agent_id": {agent_id}, 
  "create_date": "2018-10-17T02:32:45", 
  "update_date": "2018-10-17T10:05:05"
}]
```

3. update client_type as confidential // ID && TOKEN

```
curl https://www.zopim.com/api/v2/oauth/clients/ID -d '{"client_type": "confidential"}' \
 -X PUT -H "Content-Type: application/json" -H "Authorization: Bearer TOKEN"
 ```
4. update scopes

```
curl https://www.zopim.com/api/v2/oauth/clients/ID -d '{"scopes": "read write chat"}' \
 -X PUT -H "Content-Type: application/json" -H "Authorization: Bearer TOKEN"
 ```


5. get token from curl response (the way to refresh token) // CLIENT_ID && CLIENT_SECRET
```
curl https://www.zopim.com/oauth2/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d 'grant_type=client_credentials&client_id=CLIENT_ID&client_secret=CLIENT_SECRET' \
  -X POST
 ```
