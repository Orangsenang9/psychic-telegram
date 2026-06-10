---
name: Feature request
about: Suggest an idea for this project
title: ''
labels: wontfix
assignees: Orangsenang9

---

**Is your feature request related to a problem? Please describe.**
A clear and concise description of what the problem is. Ex. I'm always frustrated when [...]

**Describe the solution you'd like**
A clear and concise description of what you want to happen.

**Describe alternatives you've considered**
A clear and concise description of any alternative solutions or features you've considered.

**Additional context**
Add any other context or screenshots about the feature request here.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chunk Details</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            margin: 0;
            padding: 20px;
        }
        footer {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: #333;
            color: white;
            text-align: center;
            padding: 10px 0;
            font-size: small;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        h1 {
            text-align: center;
            margin-bottom: 20px;
        }
        .box {
            background-color: #fff;
            padding: 20px;
            margin-bottom: 30px;
            border: 1px solid #ddd;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .file-details ul {
            list-style-type: none;
            padding-left: 0;
        }
        .file-details li {
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
        }
        .back-button {
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            display: inline-block;
            margin-top: 20px;
            margin-bottom: 30px;
        }
        .back-button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Chunk Details</h1>

        <!-- File details box -->
        <div class="box file-details">
            <ul>
                <li><strong>Filename:</strong> <span>{{ filename }}</span></li>
                <li><strong>Chunk UUID:</strong> <span>{{ uuid }}</span></li>
                <li><strong>Title:</strong> <span>{{ title }}</span></li>
                <li><strong>Type:</strong> <span>{{ doc_type }}</span></li>
                <li><strong>Created:</strong> <span>{{ creation_time }}</span></li>
                <li><strong>Chunk:</strong> <span>{{ chunk }}</span></li>
                <li><strong>Content:</strong> <br><span>{{ content }}</span></li>

            </ul>
        </div>

        <!-- Back to files list button -->
        <a href="/" class="back-button">Back to Home</a>
    </div>

    <!-- Footer - Bottom of Screen add html file and link to TinyLLM-->
    <footer style="position: fixed; bottom: 0; left: 0; width: 100%; background-color: #333; color: white; text-align: center; padding: 10px 0;">
        <a href="/" style="color: white; font-size: small;">Home</a> | 
        <a href="https://github.com/jasonacox/TinyLLM" style="color: white; font-size: small;">TinyLLM Document Manager {{ version }}</a> - view_chunk.html
   </footer>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>File Details</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            margin: 0;
            padding: 20px;
        }
        footer {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: #333;
            color: white;
            text-align: center;
            padding: 10px 0;
            font-size: small;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        table {
            border-top: 1px solid #ddd;
            border-bottom: 1px solid #ddd;
            border-collapse: collapse;
        }
        th, td {
            border-top: 1px solid #ddd;
            border-bottom: 1px solid #ddd;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        h1 {
            text-align: center;
            margin-bottom: 20px;
        }
        .box {
            background-color: #fff;
            padding: 20px;
            margin-bottom: 30px;
            border: 1px solid #ddd;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .file-details ul {
            list-style-type: none;
            padding-left: 0;
        }
        .file-details li {
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
        }
        .back-button {
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            display: inline-block;
            margin-top: 20px;
            margin-bottom: 30px;
        }
        .back-button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Document Chunk Details</h1>

        <!-- File details box -->
        <div class="box file-details">
            <h2>Details of Document Chunks</h2>
            <ul>
                <li><strong>Filename:</strong> <span id="filename">{{ filename }}</span></li>
                <li><strong>Creation Time:</strong> <span id="creation_time">{{ creation_time }}</span></li>
                <!-- Loop through chunks and display title and uuid -->
                <div id="chunkList">Loading...</div>
            </ul>
        </div>

        <!-- Back to files list button -->
        <a href="/" class="back-button">Back to Home</a>
    </div>

    <!-- Footer - Bottom of Screen add html file and link to TinyLLM-->
    <footer style="position: fixed; bottom: 0; left: 0; width: 100%; background-color: #333; color: white; text-align: center; padding: 10px 0;">
        <a href="/" style="color: white; font-size: small;">Home</a> | 
        <a href="https://github.com/jasonacox/TinyLLM" style="color: white; font-size: small;">TinyLLM Document Manager {{ version }}</a> - view.html
    </footer>
    <script src="/socket.io.js"></script>
    <script>
        
        let files = [];
        let collectionValue = '';
        const chunkList = document.getElementById('chunkList');

        // Connect to the Socket.IO server
        const socket = io.connect('http://' + document.domain + ':' + location.port);

        // Function to compare to titles and return 1 or -1
        function compareTitles(a, b) {
            // Pad all numbers in the string with zeros so they are 4 characters long
            function padNumbers(s) {
                return s.replace(/\d+/g, function(n) {
                    return n.replace(/(\d+)/, function(d) {
                        return ('0000' + d).slice(-4);
                    });
                });
            }
            // Compare the padded titles
            return padNumbers(a.title) > padNumbers(b.title) ? 1 : -1;
        }

        // Listen for messages from the server
        socket.on('chunks', function(data) {
            console.log('Received message:', data);
            if (data.loading > 0) {
                // Show the count of files being loaded
                chunkList.innerHTML = `Loaded ${data.loading} chunks...`;
            } else {
                // Sort the chunks by title using compareTitles function
                data.chunks.sort((a, b) => compareTitles(a, b));
                // Create Table
                chunkList.innerHTML = '';
                let table = document.createElement('table');
                // Table body
                let tbody = document.createElement('tbody');
                for (let i = 0; i < data.chunks.length; i++) {
                    let chunk = data.chunks[i];
                    let tr = document.createElement('tr');
                    
                    let tdIndex = document.createElement('td');
                    tdIndex.textContent = `Chunk ${i+1}`;
                    tr.appendChild(tdIndex);
                    
                    let tdTitle = document.createElement('td');
                    tdTitle.textContent = chunk.title;
                    tr.appendChild(tdTitle);

                    let tdSize = document.createElement('td');
                    if (chunk.chunk_size <= 1) {
                        tdSize.textContent = ``;
                    } else {
                        tdSize.textContent = `(${chunk.chunk_size} bytes)`;
                    }
                    tr.appendChild(tdSize);
                    
                    let tdLink = document.createElement('td');
                    tdLink.style.textAlign = 'right';
                    let a = document.createElement('a');
                    a.href = `/view_chunk?uuid=${chunk.uuid}`;
                    a.textContent = '[View Chunk]';
                    tdLink.appendChild(a);
                    tr.appendChild(tdLink);
                    
                    tbody.appendChild(tr);
                }
                table.appendChild(tbody);
                chunkList.appendChild(table);

                
            }
        });

        socket.on('connected', function(data) {
            console.log('Server:', data);
        });

        // Set collectionValue from cookie
        const cookie = document.cookie;
        const cookieParts = cookie.split(';');
        for (let i = 0; i < cookieParts.length; i++) {
            const cookiePart = cookieParts[i].trim();
            if (cookiePart.startsWith('collection=')) {
                collectionValue = cookiePart.substring('collection='.length);
                break;
            }
        }

        // Request updated list of collections from the server
        function loadDocuments() {
            // Get filename from get parameter
            const urlParams = new URLSearchParams(window.location.search);
            const filename = urlParams.get('filename');
            // Send message to server to load the list of documents for the collection           
            socket.emit('loadDocuments', {
                filename: filename,
                collection: collectionValue
            });
        }

        // Load the list of documents
        loadDocuments();

    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>File Details</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            margin: 0;
            padding: 20px;
        }
        footer {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: #333;
            color: white;
            text-align: center;
            padding: 10px 0;
            font-size: small;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        table {
            border-top: 1px solid #ddd;
            border-bottom: 1px solid #ddd;
            border-collapse: collapse;
        }
        th, td {
            border-top: 1px solid #ddd;
            border-bottom: 1px solid #ddd;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        h1 {
            text-align: center;
            margin-bottom: 20px;
        }
        .box {
            background-color: #fff;
            padding: 20px;
            margin-bottom: 30px;
            border: 1px solid #ddd;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .file-details ul {
            list-style-type: none;
            padding-left: 0;
        }
        .file-details li {
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
        }
        .back-button {
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            display: inline-block;
            margin-top: 20px;
            margin-bottom: 30px;
        }
        .back-button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Document Chunk Details</h1>

        <!-- File details box -->
        <div class="box file-details">
            <h2>Details of Document Chunks</h2>
            <ul>
                <li><strong>Filename:</strong> <span id="filename">{{ filename }}</span></li>
                <li><strong>Creation Time:</strong> <span id="creation_time">{{ creation_time }}</span></li>
                <!-- Loop through chunks and display title and uuid -->
                <div id="chunkList">Loading...</div>
            </ul>
        </div>

        <!-- Back to files list button -->
        <a href="/" class="back-button">Back to Home</a>
    </div>

    <!-- Footer - Bottom of Screen add html file and link to TinyLLM-->
    <footer style="position: fixed; bottom: 0; left: 0; width: 100%; background-color: #333; color: white; text-align: center; padding: 10px 0;">
        <a href="/" style="color: white; font-size: small;">Home</a> | 
        <a href="https://github.com/jasonacox/TinyLLM" style="color: white; font-size: small;">TinyLLM Document Manager {{ version }}</a> - view.html
    </footer>
    <script src="/socket.io.js"></script>
    <script>
        
        let files = [];
        let collectionValue = '';
        const chunkList = document.getElementById('chunkList');

        // Connect to the Socket.IO server
        const socket = io.connect('http://' + document.domain + ':' + location.port);

        // Function to compare to titles and return 1 or -1
        function compareTitles(a, b) {
            // Pad all numbers in the string with zeros so they are 4 characters long
            function padNumbers(s) {
                return s.replace(/\d+/g, function(n) {
                    return n.replace(/(\d+)/, function(d) {
                        return ('0000' + d).slice(-4);
                    });
                });
            }
            // Compare the padded titles
            return padNumbers(a.title) > padNumbers(b.title) ? 1 : -1;
        }

        // Listen for messages from the server
        socket.on('chunks', function(data) {
            console.log('Received message:', data);
            if (data.loading > 0) {
                // Show the count of files being loaded
                chunkList.innerHTML = `Loaded ${data.loading} chunks...`;
            } else {
                // Sort the chunks by title using compareTitles function
                data.chunks.sort((a, b) => compareTitles(a, b));
                // Create Table
                chunkList.innerHTML = '';
                let table = document.createElement('table');
                // Table body
                let tbody = document.createElement('tbody');
                for (let i = 0; i < data.chunks.length; i++) {
                    let chunk = data.chunks[i];
                    let tr = document.createElement('tr');
                    
                    let tdIndex = document.createElement('td');
                    tdIndex.textContent = `Chunk ${i+1}`;
                    tr.appendChild(tdIndex);
                    
                    let tdTitle = document.createElement('td');
                    tdTitle.textContent = chunk.title;
                    tr.appendChild(tdTitle);

                    let tdSize = document.createElement('td');
                    if (chunk.chunk_size <= 1) {
                        tdSize.textContent = ``;
                    } else {
                        tdSize.textContent = `(${chunk.chunk_size} bytes)`;
                    }
                    tr.appendChild(tdSize);
                    
                    let tdLink = document.createElement('td');
                    tdLink.style.textAlign = 'right';
                    let a = document.createElement('a');
                    a.href = `/view_chunk?uuid=${chunk.uuid}`;
                    a.textContent = '[View Chunk]';
                    tdLink.appendChild(a);
                    tr.appendChild(tdLink);
                    
                    tbody.appendChild(tr);
                }
                table.appendChild(tbody);
                chunkList.appendChild(table);

                
            }
        });

        socket.on('connected', function(data) {
            console.log('Server:', data);
        });

        // Set collectionValue from cookie
        const cookie = document.cookie;
        const cookieParts = cookie.split(';');
        for (let i = 0; i < cookieParts.length; i++) {
            const cookiePart = cookieParts[i].trim();
            if (cookiePart.startsWith('collection=')) {
                collectionValue = cookiePart.substring('collection='.length);
                break;
            }
        }

        // Request updated list of collections from the server
        function loadDocuments() {
            // Get filename from get parameter
            const urlParams = new URLSearchParams(window.location.search);
            const filename = urlParams.get('filename');
            // Send message to server to load the list of documents for the collection           
            socket.emit('loadDocuments', {
                filename: filename,
                collection: collectionValue
            });
        }

        // Load the list of documents
        loadDocuments();

    </script>
</body>
</html>
# Third-Party Software Licenses

This project uses the following third-party libraries:

## Frontend Libraries (JavaScript/CSS)

### Prism.js
- **License**: MIT License
- **Copyright**: Copyright (c) 2012 Lea Verou
- **Website**: https://prismjs.com/
- **Purpose**: Syntax highlighting for code blocks in the chat interface
- **Files**: 
  - `app/static/prism.min.js`
  - `app/static/prism.min.css`
  - `app/static/prism-python.min.js`
  - `app/static/prism-javascript.min.js`
  - `app/static/prism-markup.min.js`

### marked.js
- **License**: MIT License
- **Copyright**: Copyright (c) 2018+, MarkedJS (https://github.com/markedjs/)
- **Website**: https://marked.js.org/
- **Purpose**: Markdown parsing and rendering in the chat interface
- **Files**: `app/static/marked.min.js`

### Socket.IO
- **License**: MIT License
- **Copyright**: Copyright (c) 2014-present Automattic <dev@cloudup.com>
- **Website**: https://socket.io/
- **Purpose**: Real-time bidirectional communication between client and server
- **Files**: `app/static/socket.io.js`

## Backend Libraries (Python)

### FastAPI
- **License**: MIT License
- **Copyright**: Copyright (c) 2018 Sebastián Ramírez
- **Website**: https://fastapi.tiangolo.com/
- **Purpose**: Modern web framework for building APIs

### Uvicorn
- **License**: BSD License
- **Website**: https://www.uvicorn.org/
- **Purpose**: ASGI web server implementation

### Python-SocketIO
- **License**: MIT License
- **Website**: https://python-socketio.readthedocs.io/
- **Purpose**: Server-side Socket.IO implementation

### OpenAI Python Client
- **License**: MIT License
- **Website**: https://github.com/openai/openai-python
- **Purpose**: OpenAI API client for LLM interaction

### Beautiful Soup 4 (bs4)
- **License**: MIT License
- **Website**: https://www.crummy.com/software/BeautifulSoup/
- **Purpose**: HTML/XML parsing for web scraping

### PyPDF
- **License**: BSD License
- **Website**: https://github.com/py-pdf/pypdf
- **Purpose**: PDF file reading and text extraction

### Pillow & pillow-heif
- **License**: HPND License (Historical Permission Notice and Disclaimer)
- **Website**: https://python-pillow.org/
- **Purpose**: Image processing and HEIF format support

### Weaviate Client
- **License**: BSD-3-Clause License
- **Website**: https://weaviate.io/
- **Purpose**: Vector database client for RAG functionality

### ReportLab
- **License**: BSD License
- **Website**: https://www.reportlab.com/opensource/
- **Purpose**: PDF document generation

### python-docx
- **License**: MIT License
- **Website**: https://python-docx.readthedocs.io/
- **Purpose**: Microsoft Word document generation

### python-pptx
- **License**: MIT License
- **Website**: https://python-pptx.readthedocs.io/
- **Purpose**: Microsoft PowerPoint document generation

### openpyxl
- **License**: MIT License
- **Website**: https://openpyxl.readthedocs.io/
- **Purpose**: Excel spreadsheet generation

### pypandoc
- **License**: MIT License
- **Website**: https://github.com/bebraw/pypandoc
- **Purpose**: Document format conversion

### aiohttp
- **License**: Apache License 2.0
- **Website**: https://docs.aiohttp.org/
- **Purpose**: Async HTTP client/server framework

### Requests
- **License**: Apache License 2.0
- **Website**: https://requests.readthedocs.io/
- **Purpose**: HTTP library for API calls

### lxml
- **License**: BSD License
- **Website**: https://lxml.de/
- **Purpose**: XML and HTML processing

### Jinja2
- **License**: BSD License
- **Website**: https://jinja.palletsprojects.com/
- **Purpose**: Template engine for HTML rendering

### Pydantic
- **License**: MIT License
- **Website**: https://pydantic-docs.helpmanual.io/
- **Purpose**: Data validation using Python type annotations

### python-dotenv
- **License**: BSD License
- **Website**: https://github.com/theskumar/python-dotenv
- **Purpose**: Environment variable management

### pandas
- **License**: BSD License
- **Website**: https://pandas.pydata.org/
- **Purpose**: Data manipulation and analysis

---

## MIT License Text

```
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Apache License 2.0

Libraries using Apache License 2.0 (aiohttp, requests) are licensed under terms that allow free use, modification, and distribution. Full license text available at: https://www.apache.org/licenses/LICENSE-2.0

## BSD License

Libraries using BSD License (Uvicorn, PyPDF, ReportLab, Jinja2, python-dotenv, pandas, lxml, Weaviate Client) are licensed under permissive terms similar to MIT. Each has slight variations but all allow free use, modification, and distribution with attribution.

---

All third-party libraries are used in accordance with their respective licenses.

# TinyLLM Chatbot Releases

## Container

The TinyLLM Chatbot docker container is available at: [jasonacox/chatbot](https://hub.docker.com/r/jasonacox/chatbot).

## 0.16.6 - UI Enhancements and Intent Router Improvements

* Added download button for generated and uploaded images with hover-to-reveal functionality.
* Enhanced list formatting with proper bottom margin spacing for better readability.
* Improved UI button opacity settings for better visual hierarchy (View Raw button now translucent).
* Added support for separate LLM model for intent routing via `INTENT_ROUTER_LLM` environment variable.
* This allows using a faster, smaller model for intent detection while using a more capable model for content generation.
* Updated stats page to display intent router LLM configuration.
* Image download functionality includes automatic filename generation with timestamps for generated images.

## 0.16.5 - Enhanced Markdown and Code Rendering

* Added syntax highlighting for code blocks using Prism.js with support for Python, JavaScript, and HTML.
* Improved streaming output rendering with proper HTML escaping to prevent code interpretation during display.
* Enhanced code block styling with dark theme background and optimized font size and line spacing.
* Fixed content jump issue when streaming text transitions to rendered markdown by adding consistent margin spacing.
* Added comprehensive third-party license attribution for all frontend and backend libraries.
* All static assets (Prism.js, marked.js, Socket.IO) now served locally to support air-gapped deployments.

## 0.16.4 - Document Generation Support

* Added comprehensive document generation functionality with support for PDF, Word, Excel, and PowerPoint formats.
* Added intelligent document intent detection that automatically recognizes when users request document creation.
* Added document download functionality with direct browser download links for generated documents.
* Added dedicated document generation module with structured content processing and LLM-enhanced formatting.
* Added support for conversation context in document generation, allowing users to create documents from previous responses.
* Fixed route mounting order to ensure document download routes are properly accessible.
* Enhanced frontend to display download links with document icons for generated files.
* Added comprehensive debug logging throughout the document generation pipeline for better troubleshooting.

## 0.16.3 - OpenAI Image Generation Support

* Added OpenAI DALL-E image generation support with dedicated environment variables.
* Added separate configuration for OpenAI image generation: `OPENAI_IMAGE_API_KEY`, `OPENAI_IMAGE_API_BASE`, `OPENAI_IMAGE_MODEL`, and `OPENAI_IMAGE_SIZE`.
* Fixed "/image route not enabled" error by separating OpenAI image settings from LiteLLM proxy configuration.
* Improved image generation route handling with automatic format detection for different providers (SwarmUI/OpenAI).

## 0.16.2 - Repetition Filter Settings

* Added environment variables for repetition filter: `REPEAT_WINDOW` and `REPEAT_COUNT`.
* These control the window size and repeat count for the LLM output repetition filter. Users can now adjust these via environment variables to fine-tune anti-repetition behavior.
* Documentation: Updated Chatbot environment variable sections in the README to use consistent tables.
* Documentation: Improved clarity, formatting, and consistency in README and environment variable documentation.

## 0.16.1 - Image Generation

* Added environment variables for image generation settings: `IMAGE_MODEL`, `IMAGE_CFGSCALE`, `IMAGE_STEPS`, `IMAGE_SEED`, `IMAGE_TIMEOUT`, `IMAGE_WIDTH`, and `IMAGE_HEIGHT`.

## 0.16.0 - Refactor Chatbot

* Refactor - To improve maintainability and prepare for future expansions, the chatbot code has been modularized.
* Image Generation - The chatbot now uses the SwarmUI APIs to generate images. Users can request image generation using the explicit `/image {prompt}` command or indirectly by using the intent router. Intent router will allow for user dialogue to adjust the image via prompt updates.
* Upgrade note: This is a major version upgrade. You will need to reset your prompts for the image intent to work correctly.

## 0.15.25 - Improvements

* Chatbot - Improve intent routing for news.

## 0.15.24 - Intent Improvements

* Chatbot - Improve the conversation context for intent routing. This allows conversational intent following.

## 0.15.23 - Intent Hotfix

* Chatbot - Fix intent router to work with multi-modal (image) context. Updated internet search RAG to better handle conversation thread context answering.

## 0.15.22 - Intent Router

* Chatbot - The chatbot now has simple heuristics (based on LLM queries) to determine the users intent and to route to the built-in functions to ground the response. This includes internet search functions `/news`, `/stock`, `/weather` and `/search`.
* To activate set environmental variable `INTENT_ROUTER=true` or use the prompt command `/intent on`.

## 0.15.21 - Internet Search

* Chatbot - The `/search` command has been added to allow the chatbot to search the internet to help answer your prompt. By default, the first 5 most relevant internet search results are added to the context.

Usage: /search {opt:number} {query}

## 0.15.20 - Chatbot Model

* Model selection behavior improved. Session will persist with selected model in that session even when refreshed. Last model selection will be remembered and auto-selected for any new sessions but will not impact existing sessions.

## 0.15.19 - Chatbot Docs

* Update URL reader to display reading status to user while processing document.

## 0.15.18 - Chatbot Updates

* Model selection will now be stored as a cookie to allow it to persist between sessions.
* Image handling has been updated to recover when switching between vision models and language models. A new `MAX_IMAGES` setting has been added to allow persisting more than one image in the same conversation context (must be supported by model or the images will be pruned by chatbot)
* Model selection option `/model list` will display list of available models in chat windows.

## 0.15.17 - Model Selector

* Chatbot - The `/model` command will now initiate a UI popup window and dropdown to allow the user to select a model from the list of available models. Alternatively, the user can specify the model with the command (e.g. `/model mixtral`) to select it immediately without the popup.

## 0.15.16 - Think Tags

* Chatbot - Add `/think filter` command and `THINK_FILTER` environmental setting to have chatbot filter out (no display) the \<think>\</think> content from models that have built in CoT reasoning like Deepseek R1.

## 0.15.15 - Docker Compose

* Quick Start using Docker compose for Chatbot.
* Chatbot - Bug Fix: Remove token limit on response. The `MAXTOKENS` setting is used to prune content sent to LLM. If not set, no pruning will happen.
* Chatbot - Added additional LiteLLM support with the environmental settings `LITELLM_PROXY` and `LITELLM_KEY`. If set, these will override the OpenAI API settings to use LiteLLM and will remove `EXTRA_BODY` defaults that conflict with LiteLLM.

## 0.15.14 - Multi-model Support

* Chatbot - Add `/model` command to list available models and dynamically set models during the session.

## 0.15.13 - Resource Fix

* Chatbot - Add LLM connection closures for non-streaming ad-hoc calls (e.g. CoT calls). This has removed the resource warning. Improved debug messages.
* Chatbot Documentation - Updated CoT prompts and added reasoning.md for additional prompt options.

## 0.15.12 - Update CoT

* Chatbot - Update Chain of Thought (CoT) to check request before routing all prompts through the CoT process. Using `/think always` will force CoT for all requests. Additionally, CoT prompts updated for better responses.

## 0.15.11 - Chain of Thought

* Chatbot - Add Chain of Thought (CoT) thinking option using the `/think on` or `/think off` toggles to the UI. When activated, queries will be passed through an out-of-band CoT loop to allow the LLM to thoughtfully explore answer and then provide a conclusion summary to the user. Set environmental variable "THINKING" to "true" to default all conversations to CoT mode.

## 0.15.10 - Bug Fix

* Chatbot - Fix error handling bug used to auto-detect max content length of LLM. Updated user input UI rendering to better handle indentation.

## 0.15.9 - DocMan Auth

* DocMan - Add basic authentication and secure connection options to Weaviate.

## 0.15.8 - Enhance Image Processing

* Chatbot - Add support for HEIC file type and resize all images to max dimensions of 1024. Handle image pasting into input field. Remove previous images from context thread.
* Chatbot - Clean up logging: non-critical logs are moved to DEBUG level.

## 0.15.7 - Vision Model Support

* Chatbot - Allows user to drag and drop images into the context window for multi-modal vision LLMs.

## 0.15.6 - Progressive Loading

* Chatbot - Updated /rag commands to allow turning auto-RAG on and off, setting the collection and result number.

## 0.15.5 - Async and SocketIO

* Chatbot - Switch to async and socket communication for more responsive UI. Bug fixes.

## 0.15.2 - Weaviate Client Updates

* Chatbot and DocMan: Provide control for WEAVIATE_HOST and WEAVIATE_GRPC_HOST (and PORTs) settings separately via environmental variables.

## 0.15.1 - Document Manager Updates

* DocMan: Bug fixes and add features to process more document types (file or URL).

## 0.15.0 - Document Manager

* Chatbot: Using Document class for RAG functions.
* DocMan: New web based UI for managing documents in the Weaviate vector database. Allows user to upload and embed content from URLs and uploaded files. Provides optional chunking and management of embedded documents.

## 0.14.13 - TPS Calculation

* Chatbot: Fix a bug that was counting null tokens.

## 0.14.12 - Toxic Filter

* Chatbot: Add toxic filter option (uses environmental variable `TOXIC_THRESHOLD`) to analyze and filter out bad prompts. Uses LLM to evaluate and score prompt. Set variable between 0 and 1 or 99 to disable (default).
* Chatbot: Add `EXTRA_BODY` variable (JSON string) to customize chat completion calls.

## 0.14.11 - OpenAI Support

* Chatbot: Add logic to detect OpenAI URL and disable non-OpenAI stop_token_ids.

## 0.14.10 - Fix Popup

* Chatbot: Fix issue where DOM was being corrupted by popup. New logic creates separate div for conversation debug.

## 0.14.9 - Conversation Thread

* Chatbot: Add `Debug Session` link to footer to display conversation thread.

## 0.14.8 - RAG Updates

* Chatbot: Update some RAG to remove duplicate documents.

## 0.14.7 - TemplateResponse

* Update TemplateResponse arguments to current format.

## 0.14.6 - News Links

* Chatbot: Expand `/news/` RAG command to include reference URL links in news article headlines.
* Add response statistics (number of tokens and tokens per second) to footer.
* Serve up local copy of socket.io.js library to help with air-gap installations.

## 0.14.5 - Ollama Support

* Add logic to chatbot to support OpenAI API servers that do not support the `/v1/models` API. This allows the Chatbot to work with Ollama provided the user specifies the LLM_MODEL.

## 0.14.4 - Llama-3 Support

* Add chatbot workaround for Meta Llama-3 support via stop token addition.
* Add logic to better handle model maximum context length errors with automated downsizing.
* Error handling and auto-retry for model changes on LLM.

## 0.14.3 - Resize Control

* Add intuitive UI control at top of user input area to allow user to resize text input box.

## 0.14.2 - Chatbot Stock RAG

* Add error checking and help for `/stock {company}` command.
* Allow user input textarea to be resized vertically.

## 0.14.1 - Chatbot Baseprompt

* Fixed bug with baseprompt updates to respond to saved Settings or new sessions.
* Updated baseprompt to include date and guidance for complex and open-ended questions.
* Add `TZ` local timezone environmental variable to ensure correct date in baseprompt.

## 0.14.0 - Chatbot Controls

* Added ability to change LLM Temperature and MaxTokens in settings.
* Added optional prompt settings read-only options to allow viewing but prevent changes (`PROMPT_RO=true`).

## 0.13.0 - Use Weaviate for RAG

* Moved from Qdrant to Weaviate - This externalizes the sentence transformation work and lets the chatbot run as a smaller service. Activate by setting `WEAVIATE_HOST` to the address of the DB.
* Added "References" text to output from `/rag` queries.
* Added `ONESHOT` environmental variable that if `True` will remove conversation threading allowing each query to be answered as a standalone session.
* Added `RAG_ONLY` environmental variable that if `True` will assume all queries should be directed to the default RAG database as set by `WEAVIATE_LIBRARY`.

## 0.12.6 - CUDA Support

* Add CUDA support for sentence transformers.
* Improve web page import function `extract_text_from_html()` for better RAG formatting.

## 0.12.5 - Chatbot LLM Model

* Added logic to poll LLM for model list. If only one model is available, use that. Otherwise verify the user requested model is available.
* Chatbot UI now shows model name and adds responsive elements to better display on mobile devices.
* Add encoding user prompts to correctly display html code in Chatbot.
* Fix `chat.py` CLI chatbot to handle user/assistant prompts for vLLM.

## 0.12.3 - Extract from URL

* Bug fix for `handle_url_prompt()` to extract text from URL.

## 0.12.2 - Misc Improvements

* Speed up command functions using async, using `aiohttp`.
* Fix prompt_expand for rag command.
* Added topic option to `/news` command.

## 0.12.1 - Performance Improvements

* Speed up user prompt echo. Immediately send to chat windows instead of waiting for LLM stream to start.
* Optimize message handling dispatching using async.
* Use AsyncOpenAI for non-streamed queries.

## 0.12.0 - FastAPI and Uvicorn

* Ported Chatbot to the async FastAPI and Uvicorn ASGI high speed web server implementation.
* Added /stats page to display configuration settings and current stats (optional `?format=json`)
* UI updated to help enforce focus on text entry box.
* Moved `prompts.json` and Sentence Transformer model location to a `./.tinyllm` for Docker support.

## 0.11.4 - Stats Page

* Add `/stats` URL to Chatbot for settings and current status information.
* Update Chatbot HTML to set focus on user textbox.
* Move `prompts.json` and Sentence Transformer models into `.tinyllm` directory.

## 0.11.3 - Optimize for Docker

* Improve Chatbot for Docker
* Added admin alert broadcast feature (`POST /alert`)

## 0.11.0 - Chatbot Updates

* Add multi-line entry to prompt input using Shift-Enter.
* Fix HTML and CSS to support windows resize for settings dialogue box.
* Bug fix and Simplify RAG commands using slash prompts.

Commands: /reset /version /sessions /rag /news /weather /stock

## 0.10.5 - vLLM Support

* vLLM provides a faster inference engine capable of handling multiple sessions simultaneously. It also runs well in Nvidia Docker containers.
* Chatbot: System prompts are not needed by vLLM as it does the translation based on the model being used. Using system prompts is now a configuration toggle in chatbot.

## 0.10.1 - Misc Updates

* Updated default prompts.
* Minor formatting updates

## 0.10.0 - Chat Prompt Settings

* Settings button allows user to update base and query prompts for the chatbot.

## 0.9.3 - Chat Format and News

* Chatbot: Added `/news` RAG command to chatbot which will cause it to attempt to fetch the latest news and have the LLM summarize it for you.

## 0.9.0 - Classifier

* Chatbot: Added `:` commands that will run a classifier on the prompt to determine RAG method to inform the LLM with current data to provide the response.

## 0.7.1 - Markdown Formatting

* Chatbot: Added "Copy code" button to code excerpts in LLM response.

## 0.7.0 - RAG Features

* Chatbot: Added `@` and `!` commands to pull prompt data documents from vector database for RAG responses.

## 0.1.0 - Initial Release
# TinyLLM Web Based Chatbot and Document Manager

Chatbot: ![Chatbot](https://img.shields.io/docker/pulls/jasonacox/chatbot) DocMan: ![DocMan](https://img.shields.io/docker/pulls/jasonacox/docman)

The TinyLLM Chatbot is a web based python flask app that allows you to chat with a LLM using the OpenAI API.

The intent of this project is to build and interact with a locally hosted LLM using consumer grade hardware. With the Chatbot, we explore stitching context through conversational threads, rendering responses via realtime token streaming from LLM, and using external data to provide context for the LLM response (Retrieval Augmented Generation). With the Document Manager, we explore uploading documents to a Vector Database to use in retrieval augmented generation, allowing our Chatbot to produce answers grounded in knowledge that we provide.

Below are steps to get the Chatbot and Document Manager running.

## Quick Start

The fastest way to get started is using Docker Compose with LiteLLM:

```bash
# Clone the repository
git clone https://github.com/jasonacox/TinyLLM.git
cd TinyLLM/chatbot/litellm

# Edit the configuration files for your setup
nano compose.yaml    # Configure your models and API keys
nano config.yaml     # Set up LLM providers (OpenAI, local models, etc.)

# Launch the complete stack
docker compose up -d
```

This will start:
- **Chatbot** at http://localhost:5000
- **LiteLLM Dashboard** at http://localhost:4000/ui
- **PostgreSQL** database for usage tracking
- **SearXNG** search engine at http://localhost:8080

### Alternative: Docker Only

If you prefer to run just the chatbot with a local LLM:

```bash
# Create the configuration directory
mkdir -p .tinyllm

# Run with your local LLM endpoint
docker run -d \
    -p 5000:5000 \
    -e OPENAI_API_BASE="http://localhost:8000/v1" \
    -e OPENAI_API_KEY="your-api-key" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    jasonacox/chatbot
```

Visit http://localhost:5000 to start chatting!

## Chatbot

The Chatbot can be launched as a Docker container or via command line.

### Environmental Variables

Below are the main environment variables you can set to configure the TinyLLM Chatbot. These can be set in your shell, Docker environment, or .env file as needed.

| Variable                | Default / Example                        | Description |
|-------------------------|------------------------------------------|-------------|
| `OPENAI_API_KEY`        | Asimov-3-Laws                            | API key for OpenAI or local LLM (required) |
| `OPENAI_API_BASE`       | http://localhost:8000/v1                 | Base URL for OpenAI-compatible API |
| `LLM_MODEL`             | models/7B/gguf-model.bin                 | Model to use (e.g. gpt-3.5-turbo, local file) |
| `TEMPERATURE`           | 0.0                                      | LLM temperature (creativity) |
| `USE_SYSTEM`            | false                                    | Use system prompt in chat if true |
| `EXTRA_BODY`            |                                          | Extra body parameters for OpenAI API (JSON) |
| `LITELLM_PROXY`         |                                          | LiteLLM Proxy URL (optional) |
| `LITELLM_KEY`           |                                          | LiteLLM Secret Key (optional) |
| `PORT`                  | 5000                                     | Port for chatbot server |
| `MAXCLIENTS`            | 1000                                     | Max concurrent clients |
| `TOKEN`                 | secret                                   | Admin token for TinyLLM |
| `MAXTOKENS`             | 0                                        | Max tokens to send to LLM for RAG |
| `AGENT_NAME`            |                                          | Name of your bot |
| `ONESHOT`               | false                                    | Enable one-shot mode |
| `RAG_ONLY`              | false                                    | Enable RAG-only mode |
| `THINKING`              | false                                    | Enable thinking mode by default |
| `THINK_FILTER`          | false                                    | Enable thinking filter |
| `TOXIC_THRESHOLD`       | 99                                       | Toxicity threshold (0-1, 99 disables) |
| `INTENT_ROUTER`         | false                                    | Enable intent detection & routing |
| `INTENT_ROUTER_LLM`     |                                          | Optional separate LLM for intent routing (uses LLM_MODEL if not set) |
| `MAX_IMAGES`            | 1                                        | Max images to keep in context |
| `PROMPT_FILE`           | .tinyllm/prompts.json                    | File to store system prompts |
| `PROMPT_RO`             | false                                    | Enable read-only prompts |
| `SEARXNG`               | http://localhost:8080                    | SearxNG URL for web search |
| `WEB_SEARCH`            | false                                    | Enable web search for all queries |
| `IMAGE_PROVIDER`        | swarmui                                  | Image generation provider (swarmui or openai) |
| `SWARMUI`               | http://localhost:7801                    | SwarmUI host URL for image generation |
| `IMAGE_MODEL`           | OfficialStableDiffusion/sd_xl_base_1.0   | SwarmUI image model to use |
| `IMAGE_CFGSCALE`        | 7.5                                      | CFG scale for SwarmUI image generation |
| `IMAGE_STEPS`           | 20                                       | Steps for SwarmUI image generation |
| `IMAGE_SEED`            | -1                                       | Seed for SwarmUI image generation |
| `IMAGE_TIMEOUT`         | 300                                      | Timeout for image generation (seconds) |
| `OPENAI_IMAGE_MODEL`    | dall-e-3                                 | OpenAI image model (dall-e-2 or dall-e-3) |
| `OPENAI_IMAGE_SIZE`     | 1024x1024                                | OpenAI image size |
| `OPENAI_IMAGE_QUALITY`  | standard                                 | OpenAI image quality (standard or hd) |
| `OPENAI_IMAGE_STYLE`    | vivid                                    | OpenAI image style (vivid or natural) |
| `IMAGE_WIDTH`           | 1024                                     | Image width |
| `IMAGE_HEIGHT`          | 1024                                     | Image height |
| `REPEAT_WINDOW`         | 200                                      | Window size for repetition detection |
| `REPEAT_COUNT`          | 5                                        | Number of repeats to trigger detection |
| `DEBUG`                 | false                                    | Enable debug mode |
| `WEAVIATE_HOST`         |                                          | Weaviate host for RAG (optional) |
| `WEAVIATE_GRPC_HOST`    |                                          | Weaviate gRPC host (optional) |
| `WEAVIATE_PORT`         | 8080                                     | Weaviate port |
| `WEAVIATE_GRPC_PORT`    | 50051                                    | Weaviate gRPC port |
| `WEAVIATE_LIBRARY`      | tinyllm                                  | Weaviate library to use |
| `WEAVIATE_AUTH_KEY`     |                                          | Weaviate Auth Key |
| `RESULTS`               | 1                                        | Number of results to return from RAG |
| `ALPHA_KEY`             | alpha_key                                | Alpha Vantage API Key |
| `UPLOAD_FOLDER`         | /tmp                                     | Folder to store uploaded documents |

> **Note:** Most boolean settings accept `true` or `false` (case-insensitive). For more details, see the comments in `chatbot/app/core/config.py`.

### Method 1: Docker Compose

A quickstart method is located in the [litellm](./litellm/) folder. This setup will launch the Chatbot + LiteLLM and PostgreSQL. This works on Mac and Linux (or WSL) systems.

```bash
cd litellm

# Edit compose.yaml and config.yaml for your setup.
nano compose.yaml
nano config.yaml

# Launch
docker compose up -d
```

The containers will download and launch. The database will be set up in the `./db` folder.
- The Chatbot will be available at http://localhost:5000
- The LiteLLM usage dashboard will be available at http://localhost:4000/ui

### Method 2: Docker

```bash
# Create placeholder prompts.json
touch prompts.json

# Run Chatbot - see run.sh for additional settings
docker run \
    -d \
    -p 5000:5000 \
    -e PORT=5000 \
    -e OPENAI_API_BASE="http://localhost:8000/v1" \
    -e INTENT_ROUTER=false \
    -e TZ="America/Los_Angeles" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    --restart unless-stopped \
    jasonacox/chatbot
```

#### LiteLLM Proxy Option

You can optionally set up LiteLLM to proxy multiple LLM backends (e.g. local vLLM, AWS Bedrock, OpenAI, Azure, Anthropic). See [LiteLLM documentation](https://docs.litellm.ai/docs/) for more information.

First, define your LLM connections in the local `config.yaml` file (see [LiteLLM options](https://docs.litellm.ai/docs/providers)). Note, if you are using a cloud provider service like AWS Bedrock or Azure, make sure you set up access first.

```yaml
model_list:

  - model_name: local-pixtral
    litellm_params:
      model: openai/mistralai/Pixtral-12B-2409
      api_base: http://localhost:8000/v1
      api_key: myAPIkey

  - model_name: bedrock-titan
    litellm_params:
      model: bedrock/amazon.titan-text-premier-v1:0
      aws_access_key_id: os.environ/CUSTOM_AWS_ACCESS_KEY_ID
      aws_secret_access_key: os.environ/CUSTOM_AWS_SECRET_ACCESS_KEY
      aws_region_name: os.environ/CUSTOM_AWS_REGION_NAME

  - model_name: gpt-3.5-turbo
    litellm_params:
      model: openai/gpt-3.5-turbo
      api_key: os.environ/OPENAI_API_KEY
```

Now,run the LiteLLM container. Edit this script to include your AWS and/or OpenAI keys for the models you want.

```bash
# Run LiteLLM Proxy - see
docker run \
    -d \
    -v $(pwd)/config.yaml:/app/config.yaml \
    -e CUSTOM_AWS_ACCESS_KEY_ID=your_AWS_key_here \
    -e CUSTOM_AWS_SECRET_ACCESS_KEY=your_AWS_secret_here \
    -e CUSTOM_AWS_REGION_NAME=us-east-1 \
    -e OPENAI_API_KEY=your_OpenAI_key_option \
    -p 4000:4000 \
    --name $CONTAINER \
    --restart unless-stopped \
    ghcr.io/berriai/litellm:main-latest \
    --config /app/config.yaml 
```

Finally, set up the chatbot to use LiteLLM:

```bash
# Run Chatbot - see run.sh for additional settings
docker run \
    -d \
    -p 5000:5000 \
    -e PORT=5000 \
    -e LITELLM_PROXY="http://localhost:4000/v1" \
    -e LITELLM_KEY="sk-mykey" \
    -e LLM_MODEL="local-pixtral" \
    -e TZ="America/Los_Angeles" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    --restart unless-stopped \
    jasonacox/chatbot
```

The Chatbot will try to use the specified model (`LLM_MODEL`) but if it is not available, it will select another available model. You can list and change the models inside the chatbot using the `/model` commands.

View the chatbot at http://localhost:5000

### Method 3: Command Line

```bash
# Install required packages
pip install -r requirements.txt

# Run the chatbot web server - change the base URL to be where you host your llmserver
OPENAI_API_BASE="http://localhost:8000/v1" python3 server.py
```

### Chat Commands and Retrieval Augmented Generation (RAG)

Some RAG (Retrieval Augmented Generation) features including:

* Summarizing external websites and PDFs (paste a URL in chat window)
* If a Weaviate host is specified, the chatbot can use the vector database information to respond. See [rag](../rag/weaviate/) for details on how to set up Weaviate.
* Perform chain of thought (CoT) reasoning with `/think on` command (see [reasoning](./reasoning.md) for more details).
* Command - There are information commands using `/`

```
/reset                                  # Reset session
/version                                # Display chatbot version
/sessions                               # Display current sessions
/news                                   # List top 10 headlines from current news
/stock [company]                        # Display stock symbol and current price
/weather [location]                     # Provide current weather conditions
/rag on [library] [opt:number]          # Route all prompts through RAG using specified library
/rag off                                #   Disable
/think on                               # Perform Chain of Thought thinking on relevant prompts
/think off                              #   Disable
/think filter [on|off]                  # Have chatbot filter out <think></think> content
/model [LLM_name]                       # Display or select LLM model to use (dialogue popup)
/search [opt:number] [prompt]           # Search the web to help answer the prompt
/intent [on|off]                        # Activate intent router to automatically run above functions
/image [prompt]                         # Generate an image based on the prompt
```

See the [rag](../rag/) for more details about RAG.

### Image Generation

The chatbot supports image generation through two providers:

1. **SwarmUI** (default) - Local image generation using Stable Diffusion models
2. **OpenAI** - Cloud-based image generation using DALL-E models

#### SwarmUI Configuration

```bash
export IMAGE_PROVIDER="swarmui"
export SWARMUI="http://localhost:7801"
export IMAGE_MODEL="OfficialStableDiffusion/sd_xl_base_1.0"
```

#### OpenAI Configuration

```bash
export IMAGE_PROVIDER="openai"
export OPENAI_API_KEY="your-openai-api-key"
export OPENAI_IMAGE_MODEL="dall-e-3"
```

See [IMAGE_CONFIG.md](IMAGE_CONFIG.md) for complete configuration options.

### Example Session

The examples below use a Llama 2 7B model served up with the OpenAI API compatible [llmserver](https://github.com/jasonacox/TinyLLM/tree/main/llmserver) on an Intel i5 system with an Nvidia GeForce GTX 1060 GPU.

#### Chatbot

Open http://127.0.0.1:5000 - Example session:

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/08097e39-9c00-4f75-8c9a-d329c886b148">

#### Read URL

If a URL is pasted in the text box, the chatbot will read and summarize it.

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/44d8a2f7-54c1-4b1c-8471-fdf13439be3b">

#### Current News

The `/news` command will fetch the latest news and have the LLM summarize the top ten headlines. It will store the raw feed in the context prompt to allow follow-up questions.

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/2732fe07-99ee-4795-a8ac-42d9a9712f6b">

#### Model Selection

The `/model` command will pop up the list of available models. Use the dropdown to select your model. Alternatively, specify the model with the command (e.g. `/model mixtral`) to select it immediately without the popup.

<img width="800" alt="image" src="https://github.com/user-attachments/assets/e21ad350-6ae0-47de-b7ee-135176d66fe7" />

#### Search the Web

The `/search` command will allow the chatbot to search the web to help answer your prompt. This requires a [SearXNG](https://docs.searxng.org/) server which is started as part of the docker compose setup or can be run using:

```bash
# Start SearXNG container

echo "Starting $container container..."
docker run \
     -d \
     -p 8080:8080 \
     -v "${PWD}/litellm/searxng:/etc/searxng:rw" \
     -e "BASE_URL=http://localhost:8080/" \
     -e "INSTANCE_NAME=my-instance" \
     --name $container \
     --restart unless-stopped \
     searxng/searxng
```

The [settings.yml](./litellm/searxng/settings.yml) file needs to be edited to allow the json format. 

The chatbot looks for the environmental variable `SEARXNG` to set the URL of the search service, otherwise it uses http://localhost:8080. You can activate it by using the prompt command like this: `/search What is the cost of gas in Texas?`

<img width="800" alt="image" src="https://github.com/user-attachments/assets/8ee65216-6b11-4590-bf19-695e5b6e9a63" />

#### Intent Router

The chatbot now has the ability to read prompts and determine if a function call would help provide a grounded answer. 

It can be activated by setting the `INTENT_ROUTER=true` environmental variable or using the prompt command `/intent on`.  It will use things like /search to find current data on things that tend to change frequently (e.g. cost of eggs). It will also use /weather, /stock and /news. The heuristics it is using is based on LLM calls so the performance will vary based on the LLM you are using. It was tuned for use with the Llama-3.2-11B-Vision model.

**Using a Separate Model for Intent Routing**: You can optionally specify a different, faster LLM model for intent detection by setting the `INTENT_ROUTER_LLM` environment variable. This is useful when you want to use a smaller, faster model for intent classification while using a larger, more capable model for actual content generation. If not set, the default LLM model specified by `LLM_MODEL` will be used for both intent routing and content generation.

```bash
export INTENT_ROUTER_LLM="your-fast-model-name"
```

<img width="800" alt="image" src="https://github.com/user-attachments/assets/422a7c13-ec6f-43bb-a959-e37d0bb709ec" />

## Document Manager (Weaviate)

The document manager allows you to manage the collections and documents in the Weaviate vector database. It provides an easy way for you to upload and ingest the content from files or URLs. It performs simple chunking (if requested). The simple UI lets you navigate through the collections and documents.

### Environmental Variables

Below are the main environment variables for the Document Manager (Weaviate):

| Variable              | Default / Example | Description |
|-----------------------|-------------------|-------------|
| `MAX_CHUNK_SIZE`      | 1024              | Maximum size of a chunk in bytes |
| `UPLOAD_FOLDER`       | uploads           | Folder where uploaded files are stored |
| `HOST`                | localhost         | Weaviate host |
| `COLLECTIONS`         | all               | Comma separated list of collections allowed |
| `PORT`                | 8000              | Port for the web server |
| `COLLECTIONS_ADMIN`   | true              | Allow users to create and delete collections |
| `WEAVIATE_HOST`       | localhost         | Weaviate host |
| `WEAVIATE_GRPC_HOST`  | localhost         | Weaviate gRPC host |
| `WEAVIATE_PORT`       | 8080              | Weaviate port |
| `WEAVIATE_GRPC_PORT`  | 50051             | Weaviate gRPC port |
| `WEAVIATE_LIBRARY`    | tinyllm           | Weaviate library to use |
| `WEAVIATE_AUTH_KEY`   |                   | Weaviate Auth Key |

> **Note:** Most boolean settings accept `true` or `false` (case-insensitive).

### Docker Setup

The Document Manager uses a vector database to store the uploaded content. Set up the Weaviate vector database using this docker compose and the included [docker-compose.yml](docker-compose.yml) file.

```bash
# Setup and run Weaviate vector database on port 8080

docker compose up -d
```

To run the Document Manager, run the following and adjust as needed. Once running, the document manager will be available at http://localhost:5001

```bash
docker run \
    -d \
    -p 5001:5001 \
    -e PORT="5001" \
    -e WEAVIATE_HOST="localhost" \
    -e WEAVIATE_GRPC_HOST="localhost" \
    -e WEAVIATE_PORT="8080" \
    -e WEAVIATE_GRPC_PORT="50051" \
    -e MAX_CHUNK_SIZE="1024" \
    -e UPLOAD_FOLDER="uploads" \
    -e COLLECTIONS_ADMIN="true" \
    --name docman \
    --restart unless-stopped \
    jasonacox/docman
```
Note - You can restrict collections by providing the environmental variable `COLLECTIONS` to a string of comma separated collection names.

### Usage

You can now create collections (libraries of content) and upload files and URLs to be stored into the vector database for the Chatbot to reference.

<img width="800" alt="image" src="https://github.com/user-attachments/assets/544c75d4-a1a3-4c32-a95f-7f12ff11a450">

<img width="800" alt="image" src="https://github.com/user-attachments/assets/4b15ef87-8f25-4d29-9214-801a326b406f">

The Chatbot can use this information if you send the prompt command:

```bash
# Usage: /rag {library} {opt:number} {prompt}

# Examples:
/rag records How much did we donate to charity in 2022?
/rag blog 5 List some facts about solar energy.
```

## Credits

This project uses the following open-source libraries:

- **[Prism.js](https://prismjs.com/)** - Syntax highlighting (MIT License)
- **[marked.js](https://marked.js.org/)** - Markdown parsing (MIT License)
- **[Socket.IO](https://socket.io/)** - Real-time communication (MIT License)

See [THIRD-PARTY-LICENSES.md](THIRD-PARTY-LICENSES.md) for full license details.

# TinyLLM Web Based Chatbot and Document Manager

Chatbot: ![Chatbot](https://img.shields.io/docker/pulls/jasonacox/chatbot) DocMan: ![DocMan](https://img.shields.io/docker/pulls/jasonacox/docman)

The TinyLLM Chatbot is a web based python flask app that allows you to chat with a LLM using the OpenAI API.

The intent of this project is to build and interact with a locally hosted LLM using consumer grade hardware. With the Chatbot, we explore stitching context through conversational threads, rendering responses via realtime token streaming from LLM, and using external data to provide context for the LLM response (Retrieval Augmented Generation). With the Document Manager, we explore uploading documents to a Vector Database to use in retrieval augmented generation, allowing our Chatbot to produce answers grounded in knowledge that we provide.

Below are steps to get the Chatbot and Document Manager running.

## Quick Start

The fastest way to get started is using Docker Compose with LiteLLM:

```bash
# Clone the repository
git clone https://github.com/jasonacox/TinyLLM.git
cd TinyLLM/chatbot/litellm

# Edit the configuration files for your setup
nano compose.yaml    # Configure your models and API keys
nano config.yaml     # Set up LLM providers (OpenAI, local models, etc.)

# Launch the complete stack
docker compose up -d
```

This will start:
- **Chatbot** at http://localhost:5000
- **LiteLLM Dashboard** at http://localhost:4000/ui
- **PostgreSQL** database for usage tracking
- **SearXNG** search engine at http://localhost:8080

### Alternative: Docker Only

If you prefer to run just the chatbot with a local LLM:

```bash
# Create the configuration directory
mkdir -p .tinyllm

# Run with your local LLM endpoint
docker run -d \
    -p 5000:5000 \
    -e OPENAI_API_BASE="http://localhost:8000/v1" \
    -e OPENAI_API_KEY="your-api-key" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    jasonacox/chatbot
```

Visit http://localhost:5000 to start chatting!

## Chatbot

The Chatbot can be launched as a Docker container or via command line.

### Environmental Variables

Below are the main environment variables you can set to configure the TinyLLM Chatbot. These can be set in your shell, Docker environment, or .env file as needed.

| Variable                | Default / Example                        | Description |
|-------------------------|------------------------------------------|-------------|
| `OPENAI_API_KEY`        | Asimov-3-Laws                            | API key for OpenAI or local LLM (required) |
| `OPENAI_API_BASE`       | http://localhost:8000/v1                 | Base URL for OpenAI-compatible API |
| `LLM_MODEL`             | models/7B/gguf-model.bin                 | Model to use (e.g. gpt-3.5-turbo, local file) |
| `TEMPERATURE`           | 0.0                                      | LLM temperature (creativity) |
| `USE_SYSTEM`            | false                                    | Use system prompt in chat if true |
| `EXTRA_BODY`            |                                          | Extra body parameters for OpenAI API (JSON) |
| `LITELLM_PROXY`         |                                          | LiteLLM Proxy URL (optional) |
| `LITELLM_KEY`           |                                          | LiteLLM Secret Key (optional) |
| `PORT`                  | 5000                                     | Port for chatbot server |
| `MAXCLIENTS`            | 1000                                     | Max concurrent clients |
| `TOKEN`                 | secret                                   | Admin token for TinyLLM |
| `MAXTOKENS`             | 0                                        | Max tokens to send to LLM for RAG |
| `AGENT_NAME`            |                                          | Name of your bot |
| `ONESHOT`               | false                                    | Enable one-shot mode |
| `RAG_ONLY`              | false                                    | Enable RAG-only mode |
| `THINKING`              | false                                    | Enable thinking mode by default |
| `THINK_FILTER`          | false                                    | Enable thinking filter |
| `TOXIC_THRESHOLD`       | 99                                       | Toxicity threshold (0-1, 99 disables) |
| `INTENT_ROUTER`         | false                                    | Enable intent detection & routing |
| `INTENT_ROUTER_LLM`     |                                          | Optional separate LLM for intent routing (uses LLM_MODEL if not set) |
| `MAX_IMAGES`            | 1                                        | Max images to keep in context |
| `PROMPT_FILE`           | .tinyllm/prompts.json                    | File to store system prompts |
| `PROMPT_RO`             | false                                    | Enable read-only prompts |
| `SEARXNG`               | http://localhost:8080                    | SearxNG URL for web search |
| `WEB_SEARCH`            | false                                    | Enable web search for all queries |
| `IMAGE_PROVIDER`        | swarmui                                  | Image generation provider (swarmui or openai) |
| `SWARMUI`               | http://localhost:7801                    | SwarmUI host URL for image generation |
| `IMAGE_MODEL`           | OfficialStableDiffusion/sd_xl_base_1.0   | SwarmUI image model to use |
| `IMAGE_CFGSCALE`        | 7.5                                      | CFG scale for SwarmUI image generation |
| `IMAGE_STEPS`           | 20                                       | Steps for SwarmUI image generation |
| `IMAGE_SEED`            | -1                                       | Seed for SwarmUI image generation |
| `IMAGE_TIMEOUT`         | 300                                      | Timeout for image generation (seconds) |
| `OPENAI_IMAGE_MODEL`    | dall-e-3                                 | OpenAI image model (dall-e-2 or dall-e-3) |
| `OPENAI_IMAGE_SIZE`     | 1024x1024                                | OpenAI image size |
| `OPENAI_IMAGE_QUALITY`  | standard                                 | OpenAI image quality (standard or hd) |
| `OPENAI_IMAGE_STYLE`    | vivid                                    | OpenAI image style (vivid or natural) |
| `IMAGE_WIDTH`           | 1024                                     | Image width |
| `IMAGE_HEIGHT`          | 1024                                     | Image height |
| `REPEAT_WINDOW`         | 200                                      | Window size for repetition detection |
| `REPEAT_COUNT`          | 5                                        | Number of repeats to trigger detection |
| `DEBUG`                 | false                                    | Enable debug mode |
| `WEAVIATE_HOST`         |                                          | Weaviate host for RAG (optional) |
| `WEAVIATE_GRPC_HOST`    |                                          | Weaviate gRPC host (optional) |
| `WEAVIATE_PORT`         | 8080                                     | Weaviate port |
| `WEAVIATE_GRPC_PORT`    | 50051                                    | Weaviate gRPC port |
| `WEAVIATE_LIBRARY`      | tinyllm                                  | Weaviate library to use |
| `WEAVIATE_AUTH_KEY`     |                                          | Weaviate Auth Key |
| `RESULTS`               | 1                                        | Number of results to return from RAG |
| `ALPHA_KEY`             | alpha_key                                | Alpha Vantage API Key |
| `UPLOAD_FOLDER`         | /tmp                                     | Folder to store uploaded documents |

> **Note:** Most boolean settings accept `true` or `false` (case-insensitive). For more details, see the comments in `chatbot/app/core/config.py`.

### Method 1: Docker Compose

A quickstart method is located in the [litellm](./litellm/) folder. This setup will launch the Chatbot + LiteLLM and PostgreSQL. This works on Mac and Linux (or WSL) systems.

```bash
cd litellm

# Edit compose.yaml and config.yaml for your setup.
nano compose.yaml
nano config.yaml

# Launch
docker compose up -d
```

The containers will download and launch. The database will be set up in the `./db` folder.
- The Chatbot will be available at http://localhost:5000
- The LiteLLM usage dashboard will be available at http://localhost:4000/ui

### Method 2: Docker

```bash
# Create placeholder prompts.json
touch prompts.json

# Run Chatbot - see run.sh for additional settings
docker run \
    -d \
    -p 5000:5000 \
    -e PORT=5000 \
    -e OPENAI_API_BASE="http://localhost:8000/v1" \
    -e INTENT_ROUTER=false \
    -e TZ="America/Los_Angeles" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    --restart unless-stopped \
    jasonacox/chatbot
```

#### LiteLLM Proxy Option

You can optionally set up LiteLLM to proxy multiple LLM backends (e.g. local vLLM, AWS Bedrock, OpenAI, Azure, Anthropic). See [LiteLLM documentation](https://docs.litellm.ai/docs/) for more information.

First, define your LLM connections in the local `config.yaml` file (see [LiteLLM options](https://docs.litellm.ai/docs/providers)). Note, if you are using a cloud provider service like AWS Bedrock or Azure, make sure you set up access first.

```yaml
model_list:

  - model_name: local-pixtral
    litellm_params:
      model: openai/mistralai/Pixtral-12B-2409
      api_base: http://localhost:8000/v1
      api_key: myAPIkey

  - model_name: bedrock-titan
    litellm_params:
      model: bedrock/amazon.titan-text-premier-v1:0
      aws_access_key_id: os.environ/CUSTOM_AWS_ACCESS_KEY_ID
      aws_secret_access_key: os.environ/CUSTOM_AWS_SECRET_ACCESS_KEY
      aws_region_name: os.environ/CUSTOM_AWS_REGION_NAME

  - model_name: gpt-3.5-turbo
    litellm_params:
      model: openai/gpt-3.5-turbo
      api_key: os.environ/OPENAI_API_KEY
```

Now,run the LiteLLM container. Edit this script to include your AWS and/or OpenAI keys for the models you want.

```bash
# Run LiteLLM Proxy - see
docker run \
    -d \
    -v $(pwd)/config.yaml:/app/config.yaml \
    -e CUSTOM_AWS_ACCESS_KEY_ID=your_AWS_key_here \
    -e CUSTOM_AWS_SECRET_ACCESS_KEY=your_AWS_secret_here \
    -e CUSTOM_AWS_REGION_NAME=us-east-1 \
    -e OPENAI_API_KEY=your_OpenAI_key_option \
    -p 4000:4000 \
    --name $CONTAINER \
    --restart unless-stopped \
    ghcr.io/berriai/litellm:main-latest \
    --config /app/config.yaml 
```

Finally, set up the chatbot to use LiteLLM:

```bash
# Run Chatbot - see run.sh for additional settings
docker run \
    -d \
    -p 5000:5000 \
    -e PORT=5000 \
    -e LITELLM_PROXY="http://localhost:4000/v1" \
    -e LITELLM_KEY="sk-mykey" \
    -e LLM_MODEL="local-pixtral" \
    -e TZ="America/Los_Angeles" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    --restart unless-stopped \
    jasonacox/chatbot
```

The Chatbot will try to use the specified model (`LLM_MODEL`) but if it is not available, it will select another available model. You can list and change the models inside the chatbot using the `/model` commands.

View the chatbot at http://localhost:5000

### Method 3: Command Line

```bash
# Install required packages
pip install -r requirements.txt

# Run the chatbot web server - change the base URL to be where you host your llmserver
OPENAI_API_BASE="http://localhost:8000/v1" python3 server.py
```

### Chat Commands and Retrieval Augmented Generation (RAG)

Some RAG (Retrieval Augmented Generation) features including:

* Summarizing external websites and PDFs (paste a URL in chat window)
* If a Weaviate host is specified, the chatbot can use the vector database information to respond. See [rag](../rag/weaviate/) for details on how to set up Weaviate.
* Perform chain of thought (CoT) reasoning with `/think on` command (see [reasoning](./reasoning.md) for more details).
* Command - There are information commands using `/`

```
/reset                                  # Reset session
/version                                # Display chatbot version
/sessions                               # Display current sessions
/news                                   # List top 10 headlines from current news
/stock [company]                        # Display stock symbol and current price
/weather [location]                     # Provide current weather conditions
/rag on [library] [opt:number]          # Route all prompts through RAG using specified library
/rag off                                #   Disable
/think on                               # Perform Chain of Thought thinking on relevant prompts
/think off                              #   Disable
/think filter [on|off]                  # Have chatbot filter out <think></think> content
/model [LLM_name]                       # Display or select LLM model to use (dialogue popup)
/search [opt:number] [prompt]           # Search the web to help answer the prompt
/intent [on|off]                        # Activate intent router to automatically run above functions
/image [prompt]                         # Generate an image based on the prompt
```

See the [rag](../rag/) for more details about RAG.

### Image Generation

The chatbot supports image generation through two providers:

1. **SwarmUI** (default) - Local image generation using Stable Diffusion models
2. **OpenAI** - Cloud-based image generation using DALL-E models

#### SwarmUI Configuration

```bash
export IMAGE_PROVIDER="swarmui"
export SWARMUI="http://localhost:7801"
export IMAGE_MODEL="OfficialStableDiffusion/sd_xl_base_1.0"
```

#### OpenAI Configuration

```bash
export IMAGE_PROVIDER="openai"
export OPENAI_API_KEY="your-openai-api-key"
export OPENAI_IMAGE_MODEL="dall-e-3"
```

See [IMAGE_CONFIG.md](IMAGE_CONFIG.md) for complete configuration options.

### Example Session

The examples below use a Llama 2 7B model served up with the OpenAI API compatible [llmserver](https://github.com/jasonacox/TinyLLM/tree/main/llmserver) on an Intel i5 system with an Nvidia GeForce GTX 1060 GPU.

#### Chatbot

Open http://127.0.0.1:5000 - Example session:

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/08097e39-9c00-4f75-8c9a-d329c886b148">

#### Read URL

If a URL is pasted in the text box, the chatbot will read and summarize it.

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/44d8a2f7-54c1-4b1c-8471-fdf13439be3b">

#### Current News

The `/news` command will fetch the latest news and have the LLM summarize the top ten headlines. It will store the raw feed in the context prompt to allow follow-up questions.

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/2732fe07-99ee-4795-a8ac-42d9a9712f6b">

#### Model Selection

The `/model` command will pop up the list of available models. Use the dropdown to select your model. Alternatively, specify the model with the command (e.g. `/model mixtral`) to select it immediately without the popup.

<img width="800" alt="image" src="https://github.com/user-attachments/assets/e21ad350-6ae0-47de-b7ee-135176d66fe7" />

#### Search the Web

The `/search` command will allow the chatbot to search the web to help answer your prompt. This requires a [SearXNG](https://docs.searxng.org/) server which is started as part of the docker compose setup or can be run using:

```bash
# Start SearXNG container

echo "Starting $container container..."
docker run \
     -d \
     -p 8080:8080 \
     -v "${PWD}/litellm/searxng:/etc/searxng:rw" \
     -e "BASE_URL=http://localhost:8080/" \
     -e "INSTANCE_NAME=my-instance" \
     --name $container \
     --restart unless-stopped \
     searxng/searxng
```

The [settings.yml](./litellm/searxng/settings.yml) file needs to be edited to allow the json format. 

The chatbot looks for the environmental variable `SEARXNG` to set the URL of the search service, otherwise it uses http://localhost:8080. You can activate it by using the prompt command like this: `/search What is the cost of gas in Texas?`

<img width="800" alt="image" src="https://github.com/user-attachments/assets/8ee65216-6b11-4590-bf19-695e5b6e9a63" />

#### Intent Router

The chatbot now has the ability to read prompts and determine if a function call would help provide a grounded answer. 

It can be activated by setting the `INTENT_ROUTER=true` environmental variable or using the prompt command `/intent on`.  It will use things like /search to find current data on things that tend to change frequently (e.g. cost of eggs). It will also use /weather, /stock and /news. The heuristics it is using is based on LLM calls so the performance will vary based on the LLM you are using. It was tuned for use with the Llama-3.2-11B-Vision model.

**Using a Separate Model for Intent Routing**: You can optionally specify a different, faster LLM model for intent detection by setting the `INTENT_ROUTER_LLM` environment variable. This is useful when you want to use a smaller, faster model for intent classification while using a larger, more capable model for actual content generation. If not set, the default LLM model specified by `LLM_MODEL` will be used for both intent routing and content generation.

```bash
export INTENT_ROUTER_LLM="your-fast-model-name"
```

<img width="800" alt="image" src="https://github.com/user-attachments/assets/422a7c13-ec6f-43bb-a959-e37d0bb709ec" />

## Document Manager (Weaviate)

The document manager allows you to manage the collections and documents in the Weaviate vector database. It provides an easy way for you to upload and ingest the content from files or URLs. It performs simple chunking (if requested). The simple UI lets you navigate through the collections and documents.

### Environmental Variables

Below are the main environment variables for the Document Manager (Weaviate):

| Variable              | Default / Example | Description |
|-----------------------|-------------------|-------------|
| `MAX_CHUNK_SIZE`      | 1024              | Maximum size of a chunk in bytes |
| `UPLOAD_FOLDER`       | uploads           | Folder where uploaded files are stored |
| `HOST`                | localhost         | Weaviate host |
| `COLLECTIONS`         | all               | Comma separated list of collections allowed |
| `PORT`                | 8000              | Port for the web server |
| `COLLECTIONS_ADMIN`   | true              | Allow users to create and delete collections |
| `WEAVIATE_HOST`       | localhost         | Weaviate host |
| `WEAVIATE_GRPC_HOST`  | localhost         | Weaviate gRPC host |
| `WEAVIATE_PORT`       | 8080              | Weaviate port |
| `WEAVIATE_GRPC_PORT`  | 50051             | Weaviate gRPC port |
| `WEAVIATE_LIBRARY`    | tinyllm           | Weaviate library to use |
| `WEAVIATE_AUTH_KEY`   |                   | Weaviate Auth Key |

> **Note:** Most boolean settings accept `true` or `false` (case-insensitive).

### Docker Setup

The Document Manager uses a vector database to store the uploaded content. Set up the Weaviate vector database using this docker compose and the included [docker-compose.yml](docker-compose.yml) file.

```bash
# Setup and run Weaviate vector database on port 8080

docker compose up -d
```

To run the Document Manager, run the following and adjust as needed. Once running, the document manager will be available at http://localhost:5001

```bash
docker run \
    -d \
    -p 5001:5001 \
    -e PORT="5001" \
    -e WEAVIATE_HOST="localhost" \
    -e WEAVIATE_GRPC_HOST="localhost" \
    -e WEAVIATE_PORT="8080" \
    -e WEAVIATE_GRPC_PORT="50051" \
    -e MAX_CHUNK_SIZE="1024" \
    -e UPLOAD_FOLDER="uploads" \
    -e COLLECTIONS_ADMIN="true" \
    --name docman \
    --restart unless-stopped \
    jasonacox/docman
```
Note - You can restrict collections by providing the environmental variable `COLLECTIONS` to a string of comma separated collection names.

### Usage

You can now create collections (libraries of content) and upload files and URLs to be stored into the vector database for the Chatbot to reference.

<img width="800" alt="image" src="https://github.com/user-attachments/assets/544c75d4-a1a3-4c32-a95f-7f12ff11a450">

<img width="800" alt="image" src="https://github.com/user-attachments/assets/4b15ef87-8f25-4d29-9214-801a326b406f">

The Chatbot can use this information if you send the prompt command:

```bash
# Usage: /rag {library} {opt:number} {prompt}

# Examples:
/rag records How much did we donate to charity in 2022?
/rag blog 5 List some facts about solar energy.
```

## Credits

This project uses the following open-source libraries:

- **[Prism.js](https://prismjs.com/)** - Syntax highlighting (MIT License)
- **[marked.js](https://marked.js.org/)** - Markdown parsing (MIT License)
- **[Socket.IO](https://socket.io/)** - Real-time communication (MIT License)

See [THIRD-PARTY-LICENSES.md](THIRD-PARTY-LICENSES.md) for full license details.
# TinyLLM Web Based Chatbot and Document Manager

Chatbot: ![Chatbot](https://img.shields.io/docker/pulls/jasonacox/chatbot) DocMan: ![DocMan](https://img.shields.io/docker/pulls/jasonacox/docman)

The TinyLLM Chatbot is a web based python flask app that allows you to chat with a LLM using the OpenAI API.

The intent of this project is to build and interact with a locally hosted LLM using consumer grade hardware. With the Chatbot, we explore stitching context through conversational threads, rendering responses via realtime token streaming from LLM, and using external data to provide context for the LLM response (Retrieval Augmented Generation). With the Document Manager, we explore uploading documents to a Vector Database to use in retrieval augmented generation, allowing our Chatbot to produce answers grounded in knowledge that we provide.

Below are steps to get the Chatbot and Document Manager running.

## Quick Start

The fastest way to get started is using Docker Compose with LiteLLM:

```bash
# Clone the repository
git clone https://github.com/jasonacox/TinyLLM.git
cd TinyLLM/chatbot/litellm

# Edit the configuration files for your setup
nano compose.yaml    # Configure your models and API keys
nano config.yaml     # Set up LLM providers (OpenAI, local models, etc.)

# Launch the complete stack
docker compose up -d
```

This will start:
- **Chatbot** at http://localhost:5000
- **LiteLLM Dashboard** at http://localhost:4000/ui
- **PostgreSQL** database for usage tracking
- **SearXNG** search engine at http://localhost:8080

### Alternative: Docker Only

If you prefer to run just the chatbot with a local LLM:

```bash
# Create the configuration directory
mkdir -p .tinyllm

# Run with your local LLM endpoint
docker run -d \
    -p 5000:5000 \
    -e OPENAI_API_BASE="http://localhost:8000/v1" \
    -e OPENAI_API_KEY="your-api-key" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    jasonacox/chatbot
```

Visit http://localhost:5000 to start chatting!

## Chatbot

The Chatbot can be launched as a Docker container or via command line.

### Environmental Variables

Below are the main environment variables you can set to configure the TinyLLM Chatbot. These can be set in your shell, Docker environment, or .env file as needed.

| Variable                | Default / Example                        | Description |
|-------------------------|------------------------------------------|-------------|
| `OPENAI_API_KEY`        | Asimov-3-Laws                            | API key for OpenAI or local LLM (required) |
| `OPENAI_API_BASE`       | http://localhost:8000/v1                 | Base URL for OpenAI-compatible API |
| `LLM_MODEL`             | models/7B/gguf-model.bin                 | Model to use (e.g. gpt-3.5-turbo, local file) |
| `TEMPERATURE`           | 0.0                                      | LLM temperature (creativity) |
| `USE_SYSTEM`            | false                                    | Use system prompt in chat if true |
| `EXTRA_BODY`            |                                          | Extra body parameters for OpenAI API (JSON) |
| `LITELLM_PROXY`         |                                          | LiteLLM Proxy URL (optional) |
| `LITELLM_KEY`           |                                          | LiteLLM Secret Key (optional) |
| `PORT`                  | 5000                                     | Port for chatbot server |
| `MAXCLIENTS`            | 1000                                     | Max concurrent clients |
| `TOKEN`                 | secret                                   | Admin token for TinyLLM |
| `MAXTOKENS`             | 0                                        | Max tokens to send to LLM for RAG |
| `AGENT_NAME`            |                                          | Name of your bot |
| `ONESHOT`               | false                                    | Enable one-shot mode |
| `RAG_ONLY`              | false                                    | Enable RAG-only mode |
| `THINKING`              | false                                    | Enable thinking mode by default |
| `THINK_FILTER`          | false                                    | Enable thinking filter |
| `TOXIC_THRESHOLD`       | 99                                       | Toxicity threshold (0-1, 99 disables) |
| `INTENT_ROUTER`         | false                                    | Enable intent detection & routing |
| `INTENT_ROUTER_LLM`     |                                          | Optional separate LLM for intent routing (uses LLM_MODEL if not set) |
| `MAX_IMAGES`            | 1                                        | Max images to keep in context |
| `PROMPT_FILE`           | .tinyllm/prompts.json                    | File to store system prompts |
| `PROMPT_RO`             | false                                    | Enable read-only prompts |
| `SEARXNG`               | http://localhost:8080                    | SearxNG URL for web search |
| `WEB_SEARCH`            | false                                    | Enable web search for all queries |
| `IMAGE_PROVIDER`        | swarmui                                  | Image generation provider (swarmui or openai) |
| `SWARMUI`               | http://localhost:7801                    | SwarmUI host URL for image generation |
| `IMAGE_MODEL`           | OfficialStableDiffusion/sd_xl_base_1.0   | SwarmUI image model to use |
| `IMAGE_CFGSCALE`        | 7.5                                      | CFG scale for SwarmUI image generation |
| `IMAGE_STEPS`           | 20                                       | Steps for SwarmUI image generation |
| `IMAGE_SEED`            | -1                                       | Seed for SwarmUI image generation |
| `IMAGE_TIMEOUT`         | 300                                      | Timeout for image generation (seconds) |
| `OPENAI_IMAGE_MODEL`    | dall-e-3                                 | OpenAI image model (dall-e-2 or dall-e-3) |
| `OPENAI_IMAGE_SIZE`     | 1024x1024                                | OpenAI image size |
| `OPENAI_IMAGE_QUALITY`  | standard                                 | OpenAI image quality (standard or hd) |
| `OPENAI_IMAGE_STYLE`    | vivid                                    | OpenAI image style (vivid or natural) |
| `IMAGE_WIDTH`           | 1024                                     | Image width |
| `IMAGE_HEIGHT`          | 1024                                     | Image height |
| `REPEAT_WINDOW`         | 200                                      | Window size for repetition detection |
| `REPEAT_COUNT`          | 5                                        | Number of repeats to trigger detection |
| `DEBUG`                 | false                                    | Enable debug mode |
| `WEAVIATE_HOST`         |                                          | Weaviate host for RAG (optional) |
| `WEAVIATE_GRPC_HOST`    |                                          | Weaviate gRPC host (optional) |
| `WEAVIATE_PORT`         | 8080                                     | Weaviate port |
| `WEAVIATE_GRPC_PORT`    | 50051                                    | Weaviate gRPC port |
| `WEAVIATE_LIBRARY`      | tinyllm                                  | Weaviate library to use |
| `WEAVIATE_AUTH_KEY`     |                                          | Weaviate Auth Key |
| `RESULTS`               | 1                                        | Number of results to return from RAG |
| `ALPHA_KEY`             | alpha_key                                | Alpha Vantage API Key |
| `UPLOAD_FOLDER`         | /tmp                                     | Folder to store uploaded documents |

> **Note:** Most boolean settings accept `true` or `false` (case-insensitive). For more details, see the comments in `chatbot/app/core/config.py`.

### Method 1: Docker Compose

A quickstart method is located in the [litellm](./litellm/) folder. This setup will launch the Chatbot + LiteLLM and PostgreSQL. This works on Mac and Linux (or WSL) systems.

```bash
cd litellm

# Edit compose.yaml and config.yaml for your setup.
nano compose.yaml
nano config.yaml

# Launch
docker compose up -d
```

The containers will download and launch. The database will be set up in the `./db` folder.
- The Chatbot will be available at http://localhost:5000
- The LiteLLM usage dashboard will be available at http://localhost:4000/ui

### Method 2: Docker

```bash
# Create placeholder prompts.json
touch prompts.json

# Run Chatbot - see run.sh for additional settings
docker run \
    -d \
    -p 5000:5000 \
    -e PORT=5000 \
    -e OPENAI_API_BASE="http://localhost:8000/v1" \
    -e INTENT_ROUTER=false \
    -e TZ="America/Los_Angeles" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    --restart unless-stopped \
    jasonacox/chatbot
```

#### LiteLLM Proxy Option

You can optionally set up LiteLLM to proxy multiple LLM backends (e.g. local vLLM, AWS Bedrock, OpenAI, Azure, Anthropic). See [LiteLLM documentation](https://docs.litellm.ai/docs/) for more information.

First, define your LLM connections in the local `config.yaml` file (see [LiteLLM options](https://docs.litellm.ai/docs/providers)). Note, if you are using a cloud provider service like AWS Bedrock or Azure, make sure you set up access first.

```yaml
model_list:

  - model_name: local-pixtral
    litellm_params:
      model: openai/mistralai/Pixtral-12B-2409
      api_base: http://localhost:8000/v1
      api_key: myAPIkey

  - model_name: bedrock-titan
    litellm_params:
      model: bedrock/amazon.titan-text-premier-v1:0
      aws_access_key_id: os.environ/CUSTOM_AWS_ACCESS_KEY_ID
      aws_secret_access_key: os.environ/CUSTOM_AWS_SECRET_ACCESS_KEY
      aws_region_name: os.environ/CUSTOM_AWS_REGION_NAME

  - model_name: gpt-3.5-turbo
    litellm_params:
      model: openai/gpt-3.5-turbo
      api_key: os.environ/OPENAI_API_KEY
```

Now,run the LiteLLM container. Edit this script to include your AWS and/or OpenAI keys for the models you want.

```bash
# Run LiteLLM Proxy - see
docker run \
    -d \
    -v $(pwd)/config.yaml:/app/config.yaml \
    -e CUSTOM_AWS_ACCESS_KEY_ID=your_AWS_key_here \
    -e CUSTOM_AWS_SECRET_ACCESS_KEY=your_AWS_secret_here \
    -e CUSTOM_AWS_REGION_NAME=us-east-1 \
    -e OPENAI_API_KEY=your_OpenAI_key_option \
    -p 4000:4000 \
    --name $CONTAINER \
    --restart unless-stopped \
    ghcr.io/berriai/litellm:main-latest \
    --config /app/config.yaml 
```

Finally, set up the chatbot to use LiteLLM:

```bash
# Run Chatbot - see run.sh for additional settings
docker run \
    -d \
    -p 5000:5000 \
    -e PORT=5000 \
    -e LITELLM_PROXY="http://localhost:4000/v1" \
    -e LITELLM_KEY="sk-mykey" \
    -e LLM_MODEL="local-pixtral" \
    -e TZ="America/Los_Angeles" \
    -v $PWD/.tinyllm:/app/.tinyllm \
    --name chatbot \
    --restart unless-stopped \
    jasonacox/chatbot
```

The Chatbot will try to use the specified model (`LLM_MODEL`) but if it is not available, it will select another available model. You can list and change the models inside the chatbot using the `/model` commands.

View the chatbot at http://localhost:5000

### Method 3: Command Line

```bash
# Install required packages
pip install -r requirements.txt

# Run the chatbot web server - change the base URL to be where you host your llmserver
OPENAI_API_BASE="http://localhost:8000/v1" python3 server.py
```

### Chat Commands and Retrieval Augmented Generation (RAG)

Some RAG (Retrieval Augmented Generation) features including:

* Summarizing external websites and PDFs (paste a URL in chat window)
* If a Weaviate host is specified, the chatbot can use the vector database information to respond. See [rag](../rag/weaviate/) for details on how to set up Weaviate.
* Perform chain of thought (CoT) reasoning with `/think on` command (see [reasoning](./reasoning.md) for more details).
* Command - There are information commands using `/`

```
/reset                                  # Reset session
/version                                # Display chatbot version
/sessions                               # Display current sessions
/news                                   # List top 10 headlines from current news
/stock [company]                        # Display stock symbol and current price
/weather [location]                     # Provide current weather conditions
/rag on [library] [opt:number]          # Route all prompts through RAG using specified library
/rag off                                #   Disable
/think on                               # Perform Chain of Thought thinking on relevant prompts
/think off                              #   Disable
/think filter [on|off]                  # Have chatbot filter out <think></think> content
/model [LLM_name]                       # Display or select LLM model to use (dialogue popup)
/search [opt:number] [prompt]           # Search the web to help answer the prompt
/intent [on|off]                        # Activate intent router to automatically run above functions
/image [prompt]                         # Generate an image based on the prompt
```

See the [rag](../rag/) for more details about RAG.

### Image Generation

The chatbot supports image generation through two providers:

1. **SwarmUI** (default) - Local image generation using Stable Diffusion models
2. **OpenAI** - Cloud-based image generation using DALL-E models

#### SwarmUI Configuration

```bash
export IMAGE_PROVIDER="swarmui"
export SWARMUI="http://localhost:7801"
export IMAGE_MODEL="OfficialStableDiffusion/sd_xl_base_1.0"
```

#### OpenAI Configuration

```bash
export IMAGE_PROVIDER="openai"
export OPENAI_API_KEY="your-openai-api-key"
export OPENAI_IMAGE_MODEL="dall-e-3"
```

See [IMAGE_CONFIG.md](IMAGE_CONFIG.md) for complete configuration options.

### Example Session

The examples below use a Llama 2 7B model served up with the OpenAI API compatible [llmserver](https://github.com/jasonacox/TinyLLM/tree/main/llmserver) on an Intel i5 system with an Nvidia GeForce GTX 1060 GPU.

#### Chatbot

Open http://127.0.0.1:5000 - Example session:

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/08097e39-9c00-4f75-8c9a-d329c886b148">

#### Read URL

If a URL is pasted in the text box, the chatbot will read and summarize it.

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/44d8a2f7-54c1-4b1c-8471-fdf13439be3b">

#### Current News

The `/news` command will fetch the latest news and have the LLM summarize the top ten headlines. It will store the raw feed in the context prompt to allow follow-up questions.

<img width="800" alt="image" src="https://github.com/jasonacox/TinyLLM/assets/836718/2732fe07-99ee-4795-a8ac-42d9a9712f6b">

#### Model Selection

The `/model` command will pop up the list of available models. Use the dropdown to select your model. Alternatively, specify the model with the command (e.g. `/model mixtral`) to select it immediately without the popup.

<img width="800" alt="image" src="https://github.com/user-attachments/assets/e21ad350-6ae0-47de-b7ee-135176d66fe7" />

#### Search the Web

The `/search` command will allow the chatbot to search the web to help answer your prompt. This requires a [SearXNG](https://docs.searxng.org/) server which is started as part of the docker compose setup or can be run using:

```bash
# Start SearXNG container

echo "Starting $container container..."
docker run \
     -d \
     -p 8080:8080 \
     -v "${PWD}/litellm/searxng:/etc/searxng:rw" \
     -e "BASE_URL=http://localhost:8080/" \
     -e "INSTANCE_NAME=my-instance" \
     --name $container \
     --restart unless-stopped \
     searxng/searxng
```

The [settings.yml](./litellm/searxng/settings.yml) file needs to be edited to allow the json format. 

The chatbot looks for the environmental variable `SEARXNG` to set the URL of the search service, otherwise it uses http://localhost:8080. You can activate it by using the prompt command like this: `/search What is the cost of gas in Texas?`

<img width="800" alt="image" src="https://github.com/user-attachments/assets/8ee65216-6b11-4590-bf19-695e5b6e9a63" />

#### Intent Router

The chatbot now has the ability to read prompts and determine if a function call would help provide a grounded answer. 

It can be activated by setting the `INTENT_ROUTER=true` environmental variable or using the prompt command `/intent on`.  It will use things like /search to find current data on things that tend to change frequently (e.g. cost of eggs). It will also use /weather, /stock and /news. The heuristics it is using is based on LLM calls so the performance will vary based on the LLM you are using. It was tuned for use with the Llama-3.2-11B-Vision model.

**Using a Separate Model for Intent Routing**: You can optionally specify a different, faster LLM model for intent detection by setting the `INTENT_ROUTER_LLM` environment variable. This is useful when you want to use a smaller, faster model for intent classification while using a larger, more capable model for actual content generation. If not set, the default LLM model specified by `LLM_MODEL` will be used for both intent routing and content generation.

```bash
export INTENT_ROUTER_LLM="your-fast-model-name"
```

<img width="800" alt="image" src="https://github.com/user-attachments/assets/422a7c13-ec6f-43bb-a959-e37d0bb709ec" />

## Document Manager (Weaviate)

The document manager allows you to manage the collections and documents in the Weaviate vector database. It provides an easy way for you to upload and ingest the content from files or URLs. It performs simple chunking (if requested). The simple UI lets you navigate through the collections and documents.

### Environmental Variables

Below are the main environment variables for the Document Manager (Weaviate):

| Variable              | Default / Example | Description |
|-----------------------|-------------------|-------------|
| `MAX_CHUNK_SIZE`      | 1024              | Maximum size of a chunk in bytes |
| `UPLOAD_FOLDER`       | uploads           | Folder where uploaded files are stored |
| `HOST`                | localhost         | Weaviate host |
| `COLLECTIONS`         | all               | Comma separated list of collections allowed |
| `PORT`                | 8000              | Port for the web server |
| `COLLECTIONS_ADMIN`   | true              | Allow users to create and delete collections |
| `WEAVIATE_HOST`       | localhost         | Weaviate host |
| `WEAVIATE_GRPC_HOST`  | localhost         | Weaviate gRPC host |
| `WEAVIATE_PORT`       | 8080              | Weaviate port |
| `WEAVIATE_GRPC_PORT`  | 50051             | Weaviate gRPC port |
| `WEAVIATE_LIBRARY`    | tinyllm           | Weaviate library to use |
| `WEAVIATE_AUTH_KEY`   |                   | Weaviate Auth Key |

> **Note:** Most boolean settings accept `true` or `false` (case-insensitive).

### Docker Setup

The Document Manager uses a vector database to store the uploaded content. Set up the Weaviate vector database using this docker compose and the included [docker-compose.yml](docker-compose.yml) file.

```bash
# Setup and run Weaviate vector database on port 8080

docker compose up -d
```

To run the Document Manager, run the following and adjust as needed. Once running, the document manager will be available at http://localhost:5001

```bash
docker run \
    -d \
    -p 5001:5001 \
    -e PORT="5001" \
    -e WEAVIATE_HOST="localhost" \
    -e WEAVIATE_GRPC_HOST="localhost" \
    -e WEAVIATE_PORT="8080" \
    -e WEAVIATE_GRPC_PORT="50051" \
    -e MAX_CHUNK_SIZE="1024" \
    -e UPLOAD_FOLDER="uploads" \
    -e COLLECTIONS_ADMIN="true" \
    --name docman \
    --restart unless-stopped \
    jasonacox/docman
```
Note - You can restrict collections by providing the environmental variable `COLLECTIONS` to a string of comma separated collection names.

### Usage

You can now create collections (libraries of content) and upload files and URLs to be stored into the vector database for the Chatbot to reference.

<img width="800" alt="image" src="https://github.com/user-attachments/assets/544c75d4-a1a3-4c32-a95f-7f12ff11a450">

<img width="800" alt="image" src="https://github.com/user-attachments/assets/4b15ef87-8f25-4d29-9214-801a326b406f">

The Chatbot can use this information if you send the prompt command:

```bash
# Usage: /rag {library} {opt:number} {prompt}

# Examples:
/rag records How much did we donate to charity in 2022?
/rag blog 5 List some facts about solar energy.
```

## Credits

This project uses the following open-source libraries:

- **[Prism.js](https://prismjs.com/)** - Syntax highlighting (MIT License)
- **[marked.js](https://marked.js.org/)** - Markdown parsing (MIT License)
- **[Socket.IO](https://socket.io/)** - Real-time communication (MIT License)

See [THIRD-PARTY-LICENSES.md](THIRD-PARTY-LICENSES.md) for full license details.
