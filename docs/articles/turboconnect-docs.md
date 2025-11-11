# How to communicate with the server
So when you connect the server will send 2 messages
```json
{
    "type":"id",
    "id":"afe4e809-dbaa-4beb-a850-d87fd59ec1e4"
}
```
The type field is always there and explain what the server is sending
This message is the server sending you your id
Then the other message will be 
```json
{
    "type":"server_data",
    "data":{
        "address":"wss://place.natounet21.dev",
        "version":"0.1.7.1",
        "features":[
            "text",
            "username",
            "timestamp",
            "chatarray"
        ]
    }
}
```
This message is the server sending you what it can do for now this not useful but when the server will be open source it will be useful to know what the server are you communicating with can do.
## Authentification
After you will need to respond there two messages you can use : 
The first is to authenticate with ScratchAuth
```json
{
    "type":"auth"
}
```
When sending this the server will send back
```json
{
    "type":"authing",
    "url":"https://..."
}
```
After you can use the Network extension of TurboWarp to open a new tab with this url sent in the JSON.
After displaying and that the user connect with the popup it should close automatically but something it might not.
After you are authed :D But before let me explain the other message
The other message is : 
```json
{
    "type":"set_user",
    "name":"Uhmmm"
}
```
The name field is the username you want then you are also Authed
NOTE : This cracked authentification if you use it your username will look like `[✖] name` but if you were Authing with ScratchAuth it would look like : `[✔] name`
## Rooms
After authing or before you need to set your room before sending anything
this what to send 
```json
{
    "type":"set_room",
    "room":"genral"
}
```
## Communication
YAY you are now authed time to chat!
First to chat you will need to send this : 
```json
{
    "type":"chat",
    "message":"Message"
}
```
Replace message by your message after
everyone will recieve: 
```json
{
    "type":"chatted",
    "message":"Message",
    "username":"[✔] name",
    "id":"afe4e809-dbaa-4beb-a850-d87fd59ec1e4"
}
```
## Join and leaves
This experimental and can bug a lot but this how
when someone join you will recieve : 
```json
{
    "type":"join",
    "name":"[✔] name"
}
```
and for disconnect : 
```json
{
    "type":"disconnected",
    "name":"[✔] name"
}
```