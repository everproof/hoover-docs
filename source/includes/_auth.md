# Authentication

> To authorize, use this code:

```shell
curl "https://hoover.everproof.com/v1/"
  -H "Authorization: lukeiamnotyourpassword"
```

> Make sure to replace `lukeiamnotyourpassword` with your API key.

Authentication to the API is performed by setting the Authorization header to your API key. Your API key is issued to you by Everproof, please contact info@everproof.com to get one. 

All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail.

`Authorization: lukeiamnotyourpassword`

<aside class="notice">
You must replace <code>lukeiamnotyourpassword</code> with your API key.
</aside>
