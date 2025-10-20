sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types a new note [content:'hello,welcome'] and clicks 'Save'.

    Note right of browser: The browser's JavaScript (spa.js) intercepts the form submission. <br>As it contains a script which allows the browser to generate html code for the data which we need so that we needed only the json data from the server.<br/>It prevents the default page reload.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note over browser,server: The browser sends the new note as a JSON payload.<br/>(Content-Type: application/json)

    server-->>browser: 201 Created<br/>(Request Payload: {content: "hello, welcome",date:"2025-10-20T16:23:46.632Z"} )
    deactivate server
    Note over browser,server: The server saves the note and sends {"message":"note created"} back to the console .
    
    Note right of browser: The JavaScript's "success" callback receives the new note.<br/>It appends this *one* new note to the list on the page.<br/>(No second GET request is needed).
