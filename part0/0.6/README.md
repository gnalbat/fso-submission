### 0.6: New note in Single page app diagram
The following sequence diagram depicts the situation where the user creates a new note using the single-page version of the app.

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: Browser appends the form input to the list and sends a POST request to server
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa <br>Content-type: application/json ({content:	"test", date:	"2024-01-05T17:25:57.134Z"})
    activate server
    Note left of server: Server sends a response, in this case in a JSON-format containing a message
    server-->>browser: content-type: application/json ({"message":"note created"})
    deactivate server
```