# PrivateChat
Easy messaging app with P2P private conversations.

### Table of contents
* [Tech Stack](#tech-stack)
* [Installation](#installation)
* [Features](#features)

### Tech Stack:
| **Frontend** | **Backend** | **Database** |
| ------ | ------ | ------ |
**[React.js]** | **[Node.js]** |  **[PostgreSQL]**
**[Redux.js]** | **[Express.js]** | **[AWS S3]**
**[Socket.io - client]** | **[Socket.io - server]**  
**[PeerJs - WebRTC]** |
**[Material-UI]** |
## Installation
```bash
$ git clone https://github.com/younes200/p2p-chat.git
$ cd p2p-chat
$ npm install
$ cd config && touch secrets.json
```

##### Secret.json
Paste in the following code and remember to configure [PostgreSQL] and [AWS S3] it accordingly...
```javascript
{
    "psqlConfig": "postgres:postgres:postgres@localhost:5432/p2p-chat",
    "sessionSecret": "this is a secret!!",
    "bcryptSalt": "this is a secret!!",
    "AWS_KEY": "XXXXXXX",
    "AWS_SECRET": "XXXXXXX/XXXXXXX/",
    "AWS_BUCKET": "p2p-chat",
    "s3Url": "https://s3.amazonaws.com/XXXXXXX/"
}
```

## Features:
> As a user, I can **register and login**. If I am already login, I can skip this step.

The user can create or submit its credentials: Passwords are hashed using the bcrypt library.
Forms include CSRF protection using the csurf npm package.

![p2p_chat-register]
![p2p_chat-login]

> As a user, I can **personalize my profile picture**.

![p2p_chat-profile_pic]

> As a user, I can **see who of my friends is online now**.

> As a user, I can **find friends using the search box**.

![p2p_chat-find_friends]

This Feature is implemented as an incremental search field.
Input events result in ajax requests, and the route hit does a database queries with pattern matching to find matches.

> As a user, I can **see a list of all of my friends**. I can also **manage friendship status**:
I can send a friendship request,
I can cancel ann erroneous friendship request,
I can accept friends requests,
I can terminate friendships

![p2p_chat-manage_friendship]

> As a user, I can **use the group chat** feature to chat with everyone that is online.

![p2p_chat-group_chat]

> As a user, I can **use the private chat** to talk to other friends that can be **either online or offline**.

![p2p_chat-private_chat]

> As a user, I can **use the secure chat** to talk to other friends.

This feature is achieved by enabling **two clients to speak directly to each other through the webRTC** protocol (p2p connection).
The **messages** payload **are stored only locally** in the redux store of each client. They are also not persistent.


License
----
**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


[//]: # (Tech Stack references:)
   [React.js]: <https://reactjs.org/docs/installation.html>
   [Node.js]: <https://nodejs.org/dist/latest-v8.x/docs/api/>
   [PostgreSQL]: <https://www.postgresql.org/docs/10/static/index.html>
   [Redux.js]: <http://redux.js.org/>
   [Express.js]: <http://expressjs.com/en/4x/api.html>
   [AWS S3]: <https://aws.amazon.com/documentation/s3/>
   [Socket.io - client]: <https://socket.io/docs/server-api/>
   [Socket.io - server]: <https://socket.io/docs/server-api/>
   [PeerJs - WebRTC]: <http://peerjs.com/docs/#api>
   [Material-UI]: <http://www.material-ui.com/#/>
   [younes200]: <https://github.com/younes200/>

[//]: # (Picture references:)
    [p2p_chat-register]: <https://github.com/younes200/p2p-chat/blob/master/readme/p2p_chat-register.gif>
    [p2p_chat-login]: <https://github.com/younes200/p2p-chat/blob/master/readme/p2p_chat-login.gif>
    [p2p_chat-profile_pic]: <https://github.com/younes200/p2p-chat/blob/master/readme/p2p_chat-profile_pic.gif>
    [p2p_chat-find_friends]: <https://github.com/younes200/p2p-chat/blob/master/readme/p2p_chat-find_friends.gif>
    [p2p_chat-manage_friendship]: <https://github.com/younes200/p2p-chat/blob/master/readme/p2p_chat-manage_friendship%20.gif>
    [p2p_chat-group_chat]: <https://github.com/younes200/p2p-chat/blob/master/readme/p2p_chat-group_chat.gif>
    [p2p_chat-private_chat]: <https://github.com/younes200/p2p-chat/blob/master/readme/p2p_chat-private_chat.gif>
