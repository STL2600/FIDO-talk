% FIDO and WebAuth and CTAP Oh My!
% Robert Ward <robert@rtward.com> & Joe Cathell <kamikazejoe@gmail.com>
%![](static/qrcode.png)<br/>Talk: [${TALK_URL}](${TALK_URL})<br/>Repo: [${REPO_URL}](${REPO_URL})

# FIDO and WebAuth and CTAP Oh My!

## What the hell does that all mean?

> - Passkeys are WebAuthn
> - CTAP is WebAuthn
> - WebAuthn is U2F
> - U2F is FIDO2

:::

It's really very simple...

:::

## Okay but what _are_ they?

> - Public Key Authentication System
> - Similar to SSH keys
> - You use a private key to prove ownership over a public key.
> - The website has _no_ secrets to keep

:::

If you've ever used SSH keys, FIDO is the same concept but applied to browsers. And all these other technologies are built on top of FIDO

:::

# Technical Details

## FIDO2

> - User's browser asks for an `Authentication Assertion`
>   - Includes as much info as possible
>   - May include a user ID
>   - May include credential type
>   - May not include anything!

## FIDO2

> - The site generates a `challange` which is 29 random bytes and sends it to the browser
>   - The challange payload may also include allowed creds or other info useful to the browser

## FIDO2

```
{
    "publicKey": {
        "timeout": 60000,
        "challenge": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "allowCredentials": [
            {
                "type": "public-key",
                "id": "pub-key-id-1"
            },
            {
                "type": "public-key",
                "id": "pub-key-id-2"
            }
        ],
        "rpId": "github.com"
    }
}
```

## FIDO2

> - The browser passes the `challange` along with the origin to the authenticator
>   - The authenticator could be a hardware token, the browser itself, or another device like a phone
>   - Because the challange includes the origin, phishing sites can't get FIDO creds

## FIDO2

```
{
  "challenge": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "origin": "https://github.com",
  "type": "webauthn.get"
}
```

:::

This is what is actually sent to the authenticator.

It will sign the challange with the corresponding public key and return the signature

:::

## FIDO2

```
{
    "type": "public-key",
    "id": "pub-key-id-1",
    "rawId": "pub-key-id-1",
    "authenticatorAttachment": "cross-platform",
    "response": {
        "clientDataJSON": "eyJjaGFsbGVuZ2UiOiJhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhYWFhIiwib3JpZ2luIjoiaHR0cHM6Ly9naXRodWIuY29tIiwidHlwZSI6IndlYmF1dGhuLmdldCJ9",
        "authenticatorData": "...",
        "signature": "...",
        "userHandle": null
    }
}
```

:::

This is the payload returned to the site. The clientDataJSON and the signature are the important parts

:::

## FIDO2

> - The site will then validate the signature and provide the user with credentials if it's valid

# Next Big Section

## Content Page 2

An important image

![](https://placekitten.com/g/200/300)

# The End

---

Your Name <your@email>

![](static/qrcode.png)

Talk: [${TALK_URL}](${TALK_URL})

Repo: [${REPO_URL}](${REPO_URL})
