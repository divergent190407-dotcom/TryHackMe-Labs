- Cryptographic failures happen when sensitive data isn't adequately protected due to lack of encryption, faulty implementation, or insufficient security measures. This includes storing passwords without hashing, using outdated or weak algorithms (such as , SHA1, or), exposing encryption keys, or failing to secure data during transmission.

- An incredible example of this is an application or service "rolling their own cryptography", rather than using well-established, vetted, and verifiably secure encryption algorithms.
- command:
- cipher="GAAaYw4RYxEfDRRKHAAYehQGC2gbERZuDQkYdjZldBEPKnlfJDF5QiMkK1RrMTFYOGUuWD8teUQlJCxFIyorWDEgPRE7ICtCJCs3VCdr"

- for c in {A..Z} {0..9}; do     echo "===== KEY$c =====";     python3 -c "import base64; d=base64.b64decode('$cipher'); k=b'KEY$c'; print(bytes(d[i]^k[i%4] for i in range(len(d))).decode('latin1', errors='ignore'))";     echo; done
## another task
Here's a clean GitHub-style write-up you can use.

---

# Secure Document Viewer – Finding the Hardcoded Encryption Key

## Objective

Find the encryption key used by the application to decrypt a confidential document.

## Initial Enumeration

The application displayed an encrypted document along with the message:

> *Only authorized personnel can access the decryption key.*

Since the decryption functionality was unavailable, the next step was to inspect the client-side resources.

---

## Step 1 – Download the Homepage

```bash
curl -s http://10.49.133.165:5004/ -o index.html
```

---

## Step 2 – Search for Interesting Keywords

To identify any references to JavaScript files or hidden functionality, I searched the HTML source.

```bash
grep -RiE "key|secret|decrypt|token|api|debug|admin|flag" index.html
```

Output:

```html
<script src="/static/js/decrypt.js"></script>
```

This indicated that the application loads a JavaScript file responsible for document decryption.

---

## Step 3 – Download the JavaScript File

```bash
curl -s http://10.49.133.165:5004/static/js/decrypt.js -o decrypt.js
```

---

## Step 4 – Review the Source Code

Reading the JavaScript source revealed the following configuration:

```javascript
const SECRET_KEY = "my-secret-key-16";
const ENCRYPTION_MODE = "ECB";
const KEY_SIZE = 128;
```

The developer had accidentally hardcoded the encryption key directly into the client-side JavaScript.

---

## Step 5 – Verify the Discovery

To quickly locate sensitive information, I searched for cryptographic keywords.

```bash
grep -iE "key|secret|decrypt|aes|iv|pass|flag" decrypt.js
```

Output:

```javascript
const SECRET_KEY = "my-secret-key-16";
const KEY_SIZE = 128;
```

---

## Vulnerability

The application stores the encryption key inside a publicly accessible JavaScript file.

Since all client-side JavaScript is downloaded by every user's browser, anyone can retrieve the key simply by inspecting the source code.

This completely defeats the purpose of encrypting the document because the key is exposed alongside the encrypted data.

---

## Security Impact

Hardcoding cryptographic keys in client-side code is a serious security flaw because:

* Anyone can download the JavaScript.
* The encryption key becomes publicly accessible.
* Attackers can decrypt any protected content.
* Encryption no longer provides confidentiality.

---

## Key Found

```text
my-secret-key-16
```

---
