0x01. Basic authentication

Base64 Encoding and Basic Authentication
What is Base64? Base64 is a binary-to-text encoding scheme that represents binary data in an ASCII string format. It is commonly used to transmit data that needs to be stored or transferred in an environment that only allows certain ASCII characters.

How to Encode a String in Base64 You can encode a string in Base64 using the following steps:

Convert the string to bytes:

message = "Hello, World!" message_bytes = message.encode('ascii') Encode the bytes to a Base64 string:

import base64 base64_bytes = base64.b64encode(message_bytes) base64_message = base64_bytes.decode('ascii') The resulting base64_message will be the Base64 encoded version of the original string.

What is Basic Authentication?
Basic authentication is a simple authentication scheme built into the HTTP protocol. It involves sending a username and password in the Authorization header of an HTTP request. The username and password are combined and encoded in Base64 before being sent.

How to Send the Authorization Header To send the Authorization header with Basic authentication, follow these steps:

Combine the username and password with a colon:

username = "myusername" password = "mypassword" credentials = f"{username}:{password}" Encode the credentials in Base64:

import base64 credentials_b64 = base64.b64encode(credentials.encode('ascii')).decode('ascii') Add the Authorization header to your HTTP request:

headers = { 'Authorization': f'Basic {credentials_b64}' } Now, you can use these headers in your HTTP requests to authenticate with a server using Basic authentication.

Simple API
Simple HTTP API for playing with User model.

Files
models/
base.py: base of all models of the API - handle serialization to file
user.py: user model
api/v1
app.py: entry point of the API
views/index.py: basic endpoints of the API: /status and /stats
views/users.py: all users endpoints
Setup
$ pip3 install -r requirements.txt
Run
$ API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
Routes
GET /api/v1/status: returns the status of the API
GET /api/v1/stats: returns some stats of the API
GET /api/v1/users: returns the list of users
GET /api/v1/users/:id: returns an user based on the ID
DELETE /api/v1/users/:id: deletes an user based on the ID
POST /api/v1/users: creates a new user (JSON parameters: email, password, last_name (optional) and first_name (optional))
PUT /api/v1/users/:id: updates an user based on the ID (JSON parameters: last_name and first_name)
