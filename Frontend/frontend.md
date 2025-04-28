# Test Case: AI Agent UI


Implement an AI Agent UI, that looks like Chat GPT (or pretty much any other AI UI).
The UI must connect to the backend using APIs listed below. Due to CORS restrictions, please use port 8080 for your app.

Following functional is required:
1) Login functional (cookie auth)
    - Login mask, navigate to main page on login success
    - If any request returns 401 - navigate back to Login page
2)	Show the chat dialogue between user and LLM.
    - Properly format LLM output (convert MD to HTML)
    - Show "thinking" animation untill responce is recieved
    - Clear the chat and assign new chat uid on page reload
3)	User should be able to score LLM answer giving positive or negative feedback (thumb up/down).

Generally you can use any tools, however, it is suggested to use the *Vue.js* framework, *yarn* package manager, *pinia* store. The *quasar* component library can be used to simplify the development.
Other tools/components can be used if needed.


# API definition:

Info: ***service-url as well as login credentials will be provided separately***

**POST: https://[service-url]/re-chat/login**

*Login*

Body parameters:
```
{
    "username": "string", // Username input
    "password": "string" // Pasword input
}
```

Response 200:
```
{
    "status": "OK"
}
```
Response 401:
```
{
    "status": "ERROR"
}
```

**GET https://[service-url]/re-chat/session**

*Get current session*

Response 200:
```
{
    "status": "OK",
    "user": "string", // Username of current session
    "expires_at": "ISO DateTime string" // Expires at DateTime
}
```

Response 401:
```
{
    "status": "ERROR"
}
```


## POST: https://[service-url]/re-chat/ai/completion 

*Query the completion of the user input* 

Body parameters:
```
{
    "uid": "string", // Unique chat Id (is used to keep context)
    "query": "string" // User query 
}
```

Response 200:
```
{
    "answer": "string", // LLM answer
}
```


## POST: https://[service-url]/re-chat/ai/completion/vote

*Score the completion*

Body parameters:

```
{
    "uid": "string", // Unique session ID
    "question": "string", // User question - text of the user input
    "answer": "string", // LLM answer - text of the aswer that is being scored
    "vote": bool // true for positive feedback, false for negative
}
```

Response 200:

```
{
    "status": "OK"
}
```