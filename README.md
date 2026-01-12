# -Text-Morse-Code-Converter-API
Design and develop an API-based application that converts plain text into Morse code and Morse code back into plain text.
Morse Code API 🔊➝⚡

A simple REST API built using FastAPI that converts English text to Morse code and Morse code back to English.
It also includes an auto-detect endpoint that intelligently identifies the input type and performs the appropriate conversion.

🚀 Features

Encode English text to Morse code

Decode Morse code to English text

Auto-detect input type (English or Morse)

Clear error handling for invalid or unsupported characters

JSON-based API responses

🛠️ Tech Stack

Python

FastAPI

Pydantic

Uvicorn (for running the server)

📂 API Endpoints
1️⃣ Encode English → Morse

POST /encode

{
  "text": "HELLO WORLD"
}

Response

{
  "morse": ".... . .-.. .-.. --- / .-- --- .-. .-.. -.."
}
2️⃣ Decode Morse → English

POST /decode

{
  "morse": ".... . .-.. .-.. --- / .-- --- .-. .-.. -.."
}

Response

{
  "text": "HELLO WORLD"
}
3️⃣ Auto Convert (English or Morse)

POST /convert

{
  "input": "SOS"
}

or

{
  "input": "... --- ..."
}
⚙️ Working Principle
1. Request Handling

The API receives HTTP POST requests in JSON format.

FastAPI automatically validates the request body using Pydantic models.

Each endpoint processes input independently and returns a structured JSON response.

2. Input Type Identification

The /convert endpoint checks the input string.

If all characters belong to Morse symbols (., -, /, space), it is treated as Morse code.

Otherwise, the input is assumed to be English text.

Based on this check, the request is routed internally to the appropriate conversion function.

3. Character-to-Morse Mapping

A predefined Python dictionary maps:

English characters → Morse code

Morse code → English characters

English input is converted to uppercase for consistency.

Each character is translated using the dictionary.

Spaces between words are represented using / in Morse code.

4. Response Generation

Converted output is assembled into a string.

The API returns the result as a JSON object.

If an invalid character or Morse sequence is encountered, a 400 HTTP error is returned with a clear message.

❗ Error Handling

Unsupported English characters → 400 Bad Request

Invalid Morse sequences → 400 Bad Request

Missing input field → 400 Bad Request

▶️ How to Run Locally
pip install fastapi uvicorn
uvicorn main:app --reload

Open your browser at:

http://127.0.0.1:8000/docs
📌 Use Cases

Learning Morse code

Backend API practice using FastAPI

Encoding/decoding tools

Beginner-friendly API project for GitHub portfolio

👨‍💻 Author

Joseph Mathew
Electronics & Communication Engineering Student
