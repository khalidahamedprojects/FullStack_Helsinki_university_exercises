sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of server: Payload:["I got Nintendo switch last month"] status code:302 found. The server's response is the 302 redirect so it temporavarily present in the above url and moves to exampleapp/notes
    
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    Note right of server: status code 200 found
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    Note right of server: status code 200 found
    server-->>browser: CSS File
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    Note right of server: status code 200 found
    server-->>browser: JavaScript File
    deactivate server

    Note right of browser : [browser starts executing the javascript code that fetches the JSON<br/>From the server]

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    Note right of browser to server: status code 200 found
    server-->>browser: [data.json] [{content: "I got Nintendo switch last month","Date":"23-10-2025"},...]
    deactivate server

    Note right of browser: [browser executes the callback function that renders the note]
