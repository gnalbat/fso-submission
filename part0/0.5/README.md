### 0.5: Single page app diagram
The following sequence diagram depicts the situation where the user goes to the single-page app version of the notes app at https://studies.cs.helsinki.fi/exampleapp/spa.

```mermaid
sequenceDiagram
    participant browser
    participant server


    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JavaScript file for single-page app functionality
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file for styling
    deactivate server
    activate browser
    Note right of browser: Browser starts executing the JavaScript code that fetches the JSON from the server

    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    deactivate browser
    activate server
    server-->>browser: [{ "content": "", "date": "2024-01-05T12:06:46.155Z" }, ... ]
    deactivate server

    Note right of browser: Browser executes the callback function that renders the notes
```