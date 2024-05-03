% FIDO and WebAuth and CTAP Oh My!
% Robert Ward <robert@rtward.com> & Joe Cathell <kamikazejoe@gmail.com>
%![](static/qrcode.png)<br/>Talk: [${TALK_URL}](${TALK_URL})<br/>Repo: [${REPO_URL}](${REPO_URL})

# FIDO and WebAuth and CTAP Oh My!

## What the hell does that all mean?

> - Passkeys are WebAuthn
> - CTAP is WebAuthn
> - WebAuthn is U2F
> - U2F is FIDO2

## Okay but what _are_ they?

> - Public Key Authentication System
> - Similar to SSH keys
> - You use a private key to prove ownership over a public key.
> - The website has _no_ secrets to keep

# Technical Details

## FIDO2

- User's browser asks for an `Authentication Assertion`
  - Includes as much info as possible
  - May include a user ID
  - May include credential type
  - May not include anything!
- The site generates a `challange` which is 29 random bytes and sends it to the browser
- The

Some important info

::: notes

Some speaker notes here

:::

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
