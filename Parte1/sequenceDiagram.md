sequenceDiagram
    participant usuario
    participant navegador
    participant servidor

    usuario->>navegador: Escribe una nota en el campo de texto
    usuario->>navegador: Hace clic en el botón "Save"

    navegador->>servidor: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate servidor
    servidor-->>navegador: 302 Found (Redirige a /notes)
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate servidor
    servidor-->>navegador: HTML document
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate servidor
    servidor-->>navegador: CSS file
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate servidor
    servidor-->>navegador: JavaScript file
    deactivate servidor

    Note right of navegador: El navegador ejecuta el JavaScript y solicita las notas actualizadas

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate servidor
    servidor-->>navegador: JSON con las notas (incluyendo la nueva nota)
    deactivate servidor

    Note right of navegador: El navegador renderiza la nueva lista de notas
