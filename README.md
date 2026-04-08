# What is this?

This is a fully client-side utility to generate shareable encrypted content using elliptic curve cryptography (ECIES with P-256 + AES-256-GCM).

It runs in the browser.

It's simple html and javascript.


# How does it work?

There's a public key that is already embedded.

The user writes what they want in the text area.

The user clicks on encrypt.

The text in the text area transforms into Base64 encrypted text.

The encrypt button splits smoothly into two: copy, reset.

Copy copies to the clipboard.

Reset resets the screen.


# How does decrypt work?

Open decrypt.html in a browser.

Upload your private key file (.pem).

Paste the encrypted Base64 text into the text area.

Click decrypt.

The text in the text area transforms into the original plaintext.

Reset clears everything including the key.

The private key never leaves the browser.


# How to generate a key pair

Generate a P-256 private key in PKCS8 format:

```
openssl genpkey -algorithm EC -pkeyopt ec_paramgen_curve:P-256 -out private.pem
```

Extract the public key:

```
openssl pkey -in private.pem -pubout -out public.pem
```

Open public.pem, copy the Base64 lines between the headers, and paste them into the `PUBLIC_KEY_PEM` variable in encrypt.html.

Keep private.pem safe. You'll upload it in decrypt.html when you need to read a message.