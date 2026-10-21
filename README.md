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

# Approach and Assumptions

-My approach was to intake a file that would be provided by the company and received by TTB or whoever the submitted labels are given to, the company would then have these in a database, or in some accessible format to be read by the app, the app then has the employee take a picture of the label, the label is then read and compared to the file that has the 100% verified correct text (since the goal is to ensure that the actual physical label matches what they submitted for the application with TTB label requirements being fulfilled), so after comparing the physical label to the correct file with the submitted label, it tells the employee if its a match or if there an inconstancy... it's then up to the employee to find it, given more time we could add functionality to point out exactly where the error is, but as it seems now if implemented this would save time in removing redundancy by not having to check correct labels (that said, it would still be the company's responsibiliity to have the employees double check to ensure it's correct)

I was making several assumptions on how this application would work using the documentation provided as a guideline. Due to not being able to conduct the actual interviews myself I made assumptions like:

- there would be files available from the applicants or application process which would have the digitized labels with fields properly filled out, instead of having the people manually check each letter I assumed this app would be a mobile application allowing for easy usage of the camera and using this the user could scan the label and have an AI model or LLM take that photo input and automatically enter the picture data into proper fields to allow it to be compared with the actual data on the file. The tools used are an ai model, it can be any type but I went with the Google AI Gemini, the other tools used are the python packages required in the bash. The comparison for the app also assumes that the data in the file you are comparing the camera input to is correct in data and format. I input error handling for both the front end and back end but due to time constraints am currently unable to figure out every issue that might occur. This also assumes that what people are taking photos of are just things that look like labels, having a message if it cant find the data or fill the fields properly. This is a base line application so it also assumes you'll be able to enter commands into the terminal to get packages that make this function, as well as assuming the user knows what these words mean and how to enter terminal or console commands. It handles if there's an exact match for the expected content as compared with the correct file the applicant submitted to the company, however this also assumes the ability to properly verify the bold requirement of the company, that said, certain fonts or angles of the photo might cause this to be offput or read in error. More training data could help resolve this.

# ////////////////////////////////////////////////////////////////////

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
