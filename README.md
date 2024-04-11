[<-- BACK](https://github.com/bkieselEducational/OAuth-Central)
# OAuth-Related-Terminology
### Back-Channel:
```The secure way to send requests (as they never touch the Browser). A Python example would be to send a request using the requests class! (to be truly secure, we need HTTPS). Ultimately, an HTTP request that never touches the browser. Something sent from your API.```

### Front-Channel:
`The insecure way to send requests. Typing into the browser URL bar or by sending an 'application/x-www-form-urlencoded' request from your client-side code.`

### Nonce:
`Short for “Number used ONCE”. Commonly associated with cryptography, a nonce value is typically a random or semi-random number generated for one time use.`

### Proof Key for Code Exchange (PKCE):
`With this new recommendation from the Oauth Organization, we introduce 3 new parameters into our Oauth flow; two of which are sent with the initial request that begins the flow. These parameters are as follows: 1. code_verifier: This will be the 'seed' for our hash. It will need to be base64URL encoded in order for Google to accept it as a parameter. I like a nice random alphanumeric 64 character string that I THEN base64URL encode and provide to the hashing function. 2. code_challenge: This is our hashed value that we will send in our inital request. Google will save this value and verify it later when we send the code_verifier with the code to redeem an authorization token. Psuedocode for generating this value would look like: base64URLencoder(sha256hasher(code_verifier)) 3. code_challenge_method: For our purposes, this value will be set to the string of 'S256'. This tells Google that we are using a sha256 hashing algorithm to generate our code_challenge. When the user has logged in, and Google has sent a verification code to our redirect_uri and we have generated a request to exchange the code for a token, we will THEN send the code_verifier as a parameter to that request. Google will then take this value, sha256 hash it and if it matches the code_challenge that we sent in the original request, it will send back the token that we desire.`

### Software Development Kit (SDK):
`A set of software tools and programs provided by hardware and software vendors that developers can use to build applications for specific platforms. SDKs help developers easily integrate their apps with a vendor’s services.`
