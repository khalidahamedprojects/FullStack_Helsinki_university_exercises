sequenceDiagram
    participant browser
    participant server

    Note right of browser: User navigates to https://studies.cs.helsinki.fi/exampleapp/spa 

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa (Status Code 200 found)
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css (Status Code 200 found)
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js  (Status Code 200 found)
    activate server 
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code (spa.js)

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{content: "New note", date: "2025-10-20T09:56:15.976Z"},…]
    deactivate server

    Note right of browser: The browser executes the callback function RedrawNotes() that renders the notes onto the page.
