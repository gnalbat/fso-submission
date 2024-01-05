### 0.4: New note diagram
The following sequence diagram depits the chain of events caused by opening the page https://studies.cs.helsinki.fi/exampleapp/notes

```
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of browser: Browser sends form data through an HTTP POST Request
    server-->>browser: HTTP 302 Found <br> Location: https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate server
    

    activate browser
    Note left of server: Server informs browser of a redirect, browser sends a GET request to the target location
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate browser
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file for styling
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript file for app functionality
    deactivate server
    activate browser
    Note right of browser: Browser starts executing the JavaScript code that fetches the JSON from the server

    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    deactivate browser
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: Browser executes the callback function that renders the notes
```