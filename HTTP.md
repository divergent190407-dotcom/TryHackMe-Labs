# Networking Basics

## What is an IP Address?
An IP address identifies a device on a network.

## Types of IP Addresses
- Public IP:

10.0.0.0 - 10.255.255.255 (10/8)
172.16.0.0 - 172.31.255.255 (172.16/12)
192.168.0.0 - 192.168.255.255 (192.168/16)

- Private IP
 
- commands :
ifconfig
##http
-# HTTP Notes — Clean & Clever

## What is HTTP?

**HTTP (HyperText Transfer Protocol)** is the language used by browsers and servers to communicate on the web.

<img width="1140" height="270" alt="image" src="https://github.com/user-attachments/assets/03f9a2f9-528e-4fee-9195-583bfb8f74eb" />
When you open a website:

```text
Browser  →  Request  →  Server
Browser  ←  Response ←  Server
```

Example:
You type `https://google.com`

* Browser sends an HTTP request
* Google’s server sends back a response (HTML, CSS, JS, images)


# Structure of HTTP Communication

## 1. Request

A client (browser) sends:

```http
GET /index.html HTTP/1.1
Host: example.com
```

Contains:

* Method : GET
* Path : 
* Headers
* Optional body


## 2. Response

Server replies:

```http
HTTP/1.1 200 OK
Content-Type: text/html
```

Contains:

* Status code: 200, the most common status code. Conveys that the request was successful. 
* Headers
* Data/content


# HTTP Methods

| Method | Purpose             |
| ------ | ------------------- |
| GET    | Fetch data          |
| POST   | Send/create data    |
| PUT    | Update entire data  |
| PATCH  | Update partial data |
| DELETE | Remove data         |


# GET

Used to retrieve data.

Example:

```http
GET /users
```

Used when:

* Opening websites
* Searching data
* Reading APIs


## POST

Used to send data.

Example:

```http
POST /login
```

Usually carries:

* Username
* Password
* Form data

---


# HTTP Headers

Headers carry extra information.

Example:

```http
Content-Type: application/json
Authorization: Bearer token
User-Agent: Chrome
```

---

## Important Headers

| Header        | Purpose         |
| ------------- | --------------- |
| Host          | Website name    |
| User-Agent    | Browser info    |
| Authorization | Authentication  |
| Cookie        | Session storage |
| Content-Type  | Data format     |

---

# Cookies

Cookies store small data in browser.

Used for:

* Login sessions
* Preferences
* Tracking

Example:

```http
Set-Cookie: session=abc123
```

---

# Sessions

A session identifies a logged-in user.

Flow:

```text
Login → Server creates session → Browser stores cookie
```

---

# HTTP vs HTTPS

## HTTP

* Data travels as plain text
* Not secure

---

## HTTPS

* Encrypted using SSL/TLS
* Secure communication

Example:

```text
https://
```

### Why HTTPS matters:

* Protects passwords
* Prevents packet sniffing
* Stops man-in-the-middle attacks

---

# DNS + HTTP Flow

When visiting a site:

```text
1. Enter URL
2. DNS finds IP address
3. Browser connects to server
4. HTTP request sent
5. Server responds
6. Page loads
```

---

# Stateless Nature of HTTP

HTTP is **stateless**.

Meaning:

* Server forgets previous requests
* Every request is independent

State is maintained using:

* Cookies
* Sessions
* Tokens

---

# Authentication

## Basic Authentication

```http
Authorization: Basic base64data
```

Weak because credentials can be decoded.

---

## Token Authentication

Uses tokens like JWT.

Example:

```http
Authorization: Bearer eyJh...
```

More secure and modern.

---

# Common Content Types

| Type                | Meaning      |
| ------------------- | ------------ |
| text/html           | Web pages    |
| application/json    | APIs         |
| image/png           | Images       |
| multipart/form-data | File uploads |

---

- Front-end server: This is usually the reverse
or load balancer that forwards the requests to the back-end.
- Back-end server: This server-side component processes user requests, interacts with databases, and serves data to the front-end. It's often developed using languages like
, Python, and Javascript and frameworks like Laravel, Django, or Node.js.
- Databases: Persistent storage systems where application data is stored. Examples of this are databases like MySQL, PostgreSQL, and NoSQL.
- APIs (Application Programming Interfaces): Interfaces allow the front and back-end to communicate and integrate with other services.
Microservices: Instead of a single monolithic back-end, many modern applications use microservices, which are small, independent services that communicate over a network, often using
/ or .

# HTTP Versions

| Version  | Features            |
| -------- | ------------------- |
| HTTP/1.1 | Traditional         |
| HTTP/2   | Faster multiplexing |
| HTTP/3   | Uses QUIC/UDP       |

---

# REST APIs and HTTP

REST APIs use HTTP methods.

Example:

```text
GET    /users
POST   /users
PUT    /users/1
DELETE /users/1
```

---

# Packet Flow (Simple View)

```text
Browser
   ↓
TCP Connection
   ↓
HTTP Request
   ↓
Server
   ↓
HTTP Response
   ↓
Browser Renders Page
```

---

# Important Cybersecurity Concepts in HTTP

#1. Packet Sniffing

Capturing network traffic.

Dangerous on HTTP because data is visible.


#2. MITM Attack

Man-In-The-Middle attack.

Attacker intercepts communication.

HTTPS helps prevent this.

#3. CSRF

Forces users to perform unwanted actions.

#4. XSS

Injecting malicious JavaScript into websites.


# Useful Tools

| Tool       | Use                   |
| ---------- | --------------------- |
| Wireshark  | Packet analysis       |
| Burp Suite | Web security testing  |
| Postman    | API testing           |
| curl       | Command-line requests |

---

# curl Examples

## GET Request

```bash
curl https://example.com
```

---

## POST Request

```bash
curl -X POST https://example.com/login
```


# Easy Memory Tricks

- Request = Asking
- Response = Answer
- GET = Grab
- POST = Push
-4xx = Your mistake
- 5xx = Server mistake

HTTP is:

* Stateless
* Request-response based
* Application layer protocol
* Used for web communication

HTTPS adds:

* Encryption
* Integrity
* Authentication



## Common Ports
- 80 → HTTP
- 443 → HTTPS
- 22 → SSH

## OSI Model(seven layers)
1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application
