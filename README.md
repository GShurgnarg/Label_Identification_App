# Label_Identification_App

This is an application to identify the contents of a label on an alcohol bottle and determine its compliance with government and customer requirements, 

including alc. %, gov warning, description, etc.

# About TTB Label Requirements

For reference, TTB requires specific information on alcohol beverage labels. The exact requirements vary by beverage type (beer, wine, distilled spirits) but common elements include:

-Brand name

-Class/type designation

-Alcohol content (with some exceptions for certain wine/beer)

-Net contents

-Name and address of bottler/producer

-Country of origin for imports

-Government Health Warning Statement (mandatory on all alcohol beverages)

# Deliverables

-Source Code Repository (GitHub or similar)

-All source code

-README with setup and run instructions

-Brief documentation of approach, tools used, assumptions made

# Deployed Application URL

-Working prototype we can access and test


/////////////////////////////////////////////////////////////////////////////////////////////////////

# Alcohol TTB Verifier

A web application that captures or uploads images of alcohol bottle labels, extracts key regulatory data using the Gemini AI API, and validates the extracted values against an expected template. It also strictly checks for mandatory TTB compliance formatting (such as checking if the Government Warning is in bold and ALL CAPS).

## Setup & Installation

Follow these steps to get the application running locally on your machine.

### 1) Install Dependencies
Open terminal in project directory, run the following command for installing required Python packages:

```bash
pip install flask google-genai pillow
```

### 2) Configure Your API Key
Get a free API key from Google AI Studio. Set it in your terminal so the backend server can authenticate:

* **Mac/Linux:**
  ```bash
  export GEMINI_API_KEY="your_api_key_here"
  ```
* **Windows (Command Prompt):**
  ```cmd
  set GEMINI_API_KEY="your_api_key_here"
  ```
* **Windows (PowerShell):**
  ```powershell
  $env:GEMINI_API_KEY="your_api_key_here"
  ```

### 3) Run the Application
Start the local Python server:

```bash
python app.py
```

Once running, use browser & go to `http://localhost:5000` to test the app
