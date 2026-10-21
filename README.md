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

* **Terminal:**
  ```bash
  pip install flask google-genai pillow
  ```

### 2) Configure Your API Key
Get a free API key from Google AI Studio. Set it in your terminal so the backend server can authenticate:

* **Mac/Linux:**
  ```bash
  export GEMINI_API_KEY="your_api_key_here"
  ```
  (I'm not as familiar with mac & linux but if you have that system this should work)
  
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

# Logs from render.com while deploying:
==> Downloading cache...
==> Cloning from https://github.com/GShurgnarg/Label_Identification_App
==> Checking out commit 7774a3b13daf938cd5e73736ef2b2874cc20b7a8 in branch main
==> Downloaded and extracted 22 MiB cache in 5s.
==> Using Python version 3.14.8 (default)
==> Docs on specifying a Python version: https://render.com/docs/python-version
==> Installing Python version 3.14.8...
==> Using Poetry version 2.1.3 (default)
==> Docs on specifying a Poetry version: https://render.com/docs/poetry-version
==> Running build command 'pip install -r requirements.txt'...
Collecting google-genai (from -r requirements.txt (line 1))
  Using cached google_genai-2.32.0-py3-none-any.whl.metadata (58 kB)
Collecting flask (from -r requirements.txt (line 2))
  Using cached flask-3.1.3-py3-none-any.whl.metadata (3.2 kB)
Collecting pillow (from -r requirements.txt (line 3))
  Using cached pillow-13.0.0-cp314-cp314-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl.metadata (9.1 kB)
Collecting gunicorn (from -r requirements.txt (line 4))
  Using cached gunicorn-26.2.0-py3-none-any.whl.metadata (5.5 kB)
Collecting anyio<5.0.0,>=4.8.0 (from google-genai->-r requirements.txt (line 1))
  Using cached anyio-4.15.1-py3-none-any.whl.metadata (4.7 kB)
Collecting google-auth<3.0.0,>=2.56.0 (from google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Using cached google_auth-2.62.0-py3-none-any.whl.metadata (6.0 kB)
Collecting httpx<1.0.0,>=0.28.1 (from google-genai->-r requirements.txt (line 1))
  Using cached httpx-0.28.1-py3-none-any.whl.metadata (7.1 kB)
Collecting pydantic<3.0.0,>=2.12.5 (from google-genai->-r requirements.txt (line 1))
  Using cached pydantic-2.14.1-py3-none-any.whl.metadata (133 kB)
Collecting requests<3.0.0,>=2.28.1 (from google-genai->-r requirements.txt (line 1))
  Using cached requests-2.34.2-py3-none-any.whl.metadata (4.8 kB)
Collecting tenacity<9.2.0,>=8.2.3 (from google-genai->-r requirements.txt (line 1))
  Using cached tenacity-9.1.4-py3-none-any.whl.metadata (1.2 kB)
Collecting websockets<17.0,>=13.0.0 (from google-genai->-r requirements.txt (line 1))
  Using cached websockets-16.1.1-cp314-cp314-manylinux1_x86_64.manylinux_2_28_x86_64.manylinux_2_5_x86_64.whl.metadata (6.8 kB)
Collecting typing-extensions<5.0.0,>=4.14.0 (from google-genai->-r requirements.txt (line 1))
  Using cached typing_extensions-4.16.0-py3-none-any.whl.metadata (3.3 kB)
Collecting distro<2,>=1.7.0 (from google-genai->-r requirements.txt (line 1))
  Using cached distro-1.9.0-py3-none-any.whl.metadata (6.8 kB)
Collecting sniffio (from google-genai->-r requirements.txt (line 1))
  Using cached sniffio-1.3.1-py3-none-any.whl.metadata (3.9 kB)
Collecting idna>=2.8 (from anyio<5.0.0,>=4.8.0->google-genai->-r requirements.txt (line 1))
  Using cached idna-3.20-py3-none-any.whl.metadata (7.2 kB)
Collecting pyasn1-modules>=0.2.1 (from google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Using cached pyasn1_modules-0.4.2-py3-none-any.whl.metadata (3.5 kB)
Collecting cryptography>=41.0.5 (from google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Using cached cryptography-50.0.2-cp311-abi3-manylinux_2_34_x86_64.whl.metadata (4.4 kB)
Collecting certifi (from httpx<1.0.0,>=0.28.1->google-genai->-r requirements.txt (line 1))
  Using cached certifi-2026.10.19-py3-none-any.whl.metadata (2.5 kB)
Collecting httpcore==1.* (from httpx<1.0.0,>=0.28.1->google-genai->-r requirements.txt (line 1))
  Using cached httpcore-1.0.9-py3-none-any.whl.metadata (21 kB)
Collecting h11>=0.16 (from httpcore==1.*->httpx<1.0.0,>=0.28.1->google-genai->-r requirements.txt (line 1))
  Using cached h11-0.16.0-py3-none-any.whl.metadata (8.3 kB)
Collecting annotated-types>=0.6.0 (from pydantic<3.0.0,>=2.12.5->google-genai->-r requirements.txt (line 1))
  Using cached annotated_types-0.8.0-py3-none-any.whl.metadata (15 kB)
Collecting pydantic-core==2.50.1 (from pydantic<3.0.0,>=2.12.5->google-genai->-r requirements.txt (line 1))
  Using cached pydantic_core-2.50.1-cp314-cp314-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (6.5 kB)
Collecting typing-inspection>=0.4.4 (from pydantic<3.0.0,>=2.12.5->google-genai->-r requirements.txt (line 1))
  Using cached typing_inspection-0.4.4-py3-none-any.whl.metadata (2.6 kB)
Collecting charset_normalizer<4,>=2 (from requests<3.0.0,>=2.28.1->google-genai->-r requirements.txt (line 1))
  Using cached charset_normalizer-3.5.2-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (46 kB)
Collecting urllib3<3,>=1.26 (from requests<3.0.0,>=2.28.1->google-genai->-r requirements.txt (line 1))
  Using cached urllib3-2.8.0-py3-none-any.whl.metadata (7.4 kB)
Collecting blinker>=1.9.0 (from flask->-r requirements.txt (line 2))
  Using cached blinker-1.9.0-py3-none-any.whl.metadata (1.6 kB)
Collecting click>=8.1.3 (from flask->-r requirements.txt (line 2))
  Using cached click-8.5.0-py3-none-any.whl.metadata (2.6 kB)
Collecting itsdangerous>=2.2.0 (from flask->-r requirements.txt (line 2))
  Using cached itsdangerous-2.2.0-py3-none-any.whl.metadata (1.9 kB)
Collecting jinja2>=3.1.2 (from flask->-r requirements.txt (line 2))
  Using cached jinja2-3.1.6-py3-none-any.whl.metadata (2.9 kB)
Collecting markupsafe>=2.1.1 (from flask->-r requirements.txt (line 2))
  Using cached markupsafe-3.0.4-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (2.7 kB)
Collecting werkzeug>=3.1.0 (from flask->-r requirements.txt (line 2))
  Using cached werkzeug-3.1.9-py3-none-any.whl.metadata (4.1 kB)
Collecting cffi>=2.0.0 (from cryptography>=41.0.5->google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Using cached cffi-2.1.1-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.whl.metadata (2.5 kB)
Collecting pycparser (from cffi>=2.0.0->cryptography>=41.0.5->google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Using cached pycparser-3.11-py3-none-any.whl.metadata (8.2 kB)
Collecting pyasn1<0.7.0,>=0.6.1 (from pyasn1-modules>=0.2.1->google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Using cached pyasn1-0.6.4-py3-none-any.whl.metadata (8.4 kB)
Using cached google_genai-2.32.0-py3-none-any.whl (1.2 MB)
Using cached anyio-4.15.1-py3-none-any.whl (132 kB)
Using cached distro-1.9.0-py3-none-any.whl (20 kB)
Using cached google_auth-2.62.0-py3-none-any.whl (267 kB)
Using cached httpx-0.28.1-py3-none-any.whl (73 kB)
Using cached httpcore-1.0.9-py3-none-any.whl (78 kB)
Using cached pydantic-2.14.1-py3-none-any.whl (488 kB)
Using cached pydantic_core-2.50.1-cp314-cp314-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (2.2 MB)
Using cached requests-2.34.2-py3-none-any.whl (73 kB)
Using cached charset_normalizer-3.5.2-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (255 kB)
Using cached idna-3.20-py3-none-any.whl (69 kB)
Using cached tenacity-9.1.4-py3-none-any.whl (28 kB)
Using cached typing_extensions-4.16.0-py3-none-any.whl (45 kB)
Using cached urllib3-2.8.0-py3-none-any.whl (135 kB)
Using cached websockets-16.1.1-cp314-cp314-manylinux1_x86_64.manylinux_2_28_x86_64.manylinux_2_5_x86_64.whl (187 kB)
Using cached flask-3.1.3-py3-none-any.whl (103 kB)
Using cached pillow-13.0.0-cp314-cp314-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl (7.1 MB)
Using cached gunicorn-26.2.0-py3-none-any.whl (228 kB)
Using cached annotated_types-0.8.0-py3-none-any.whl (13 kB)
Using cached blinker-1.9.0-py3-none-any.whl (8.5 kB)
Using cached certifi-2026.10.19-py3-none-any.whl (136 kB)
Using cached click-8.5.0-py3-none-any.whl (125 kB)
Using cached cryptography-50.0.2-cp311-abi3-manylinux_2_34_x86_64.whl (4.8 MB)
Using cached cffi-2.1.1-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (221 kB)
Using cached h11-0.16.0-py3-none-any.whl (37 kB)
Using cached itsdangerous-2.2.0-py3-none-any.whl (16 kB)
Using cached jinja2-3.1.6-py3-none-any.whl (134 kB)
Using cached markupsafe-3.0.4-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (23 kB)
Using cached pyasn1_modules-0.4.2-py3-none-any.whl (181 kB)
Using cached pyasn1-0.6.4-py3-none-any.whl (84 kB)
Using cached typing_inspection-0.4.4-py3-none-any.whl (14 kB)
Using cached werkzeug-3.1.9-py3-none-any.whl (228 kB)
Using cached pycparser-3.11-py3-none-any.whl (51 kB)
Using cached sniffio-1.3.1-py3-none-any.whl (10 kB)
Installing collected packages: websockets, urllib3, typing-extensions, tenacity, sniffio, pycparser, pyasn1, pillow, markupsafe, itsdangerous, idna, h11, gunicorn, distro, click, charset_normalizer, certifi, blinker, annotated-types, werkzeug, typing-inspection, requests, pydantic-core, pyasn1-modules, jinja2, httpcore, cffi, anyio, pydantic, httpx, flask, cryptography, google-auth, google-genai

Successfully installed annotated-types-0.8.0 anyio-4.15.1 blinker-1.9.0 certifi-2026.10.19 cffi-2.1.1 charset_normalizer-3.5.2 click-8.5.0 cryptography-50.0.2 distro-1.9.0 flask-3.1.3 google-auth-2.62.0 google-genai-2.32.0 gunicorn-26.2.0 h11-0.16.0 httpcore-1.0.9 httpx-0.28.1 idna-3.20 itsdangerous-2.2.0 jinja2-3.1.6 markupsafe-3.0.4 pillow-13.0.0 pyasn1-0.6.4 pyasn1-modules-0.4.2 pycparser-3.11 pydantic-2.14.1 pydantic-core-2.50.1 requests-2.34.2 sniffio-1.3.1 tenacity-9.1.4 typing-extensions-4.16.0 typing-inspection-0.4.4 urllib3-2.8.0 websockets-16.1.1 werkzeug-3.1.9

[notice] A new release of pip is available: 26.2.1 -> 26.2.2
[notice] To update, run: pip install --upgrade pip
==> Uploading build...
==> Uploaded in 2.7s. Compression took 1.3s
==> Build successful 🎉
==> Deploying...
==> Setting WEB_CONCURRENCY=1 by default, based on available CPUs in the instance
==> Running 'python Backend_python_app'
 * Serving Flask app 'Backend_python_app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://10.25.226.227:5000
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 145-250-506
127.0.0.1 - - [21/Oct/2026 19:31:51] "HEAD / HTTP/1.1" 404 -
==> New primary port detected: 5000. Restarting deploy to update network configuration...
==> Docs on specifying a port: https://render.com/docs/web-services#port-binding
==> Running 'python Backend_python_app'
 * Serving Flask app 'Backend_python_app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://10.25.203.24:5000
Press CTRL+C to quit
 * Restarting with stat
/opt/render/project/python/Python-3.14.8/lib/python3.14/multiprocessing/resource_tracker.py:475: UserWarning: resource_tracker: There appear to be 1 leaked semaphore objects to clean up at shutdown: {'/mp-ya4lxgx4'}
  warnings.warn(
==> Your service is live 🎉
==> 
==> ///////////////////////////////////////////////////////////
==> 
==> Available at your primary URL https://label-identification-app.onrender.com
==> 
==> ///////////////////////////////////////////////////////////
 * Debugger is active!
 * Debugger PIN: 771-673-540
127.0.0.1 - - [21/Oct/2026 19:33:01] "HEAD / HTTP/1.1" 404 -
127.0.0.1 - - [21/Oct/2026 19:33:01] "GET / HTTP/1.1" 404 -
127.0.0.1 - - [21/Oct/2026 19:33:01] "HEAD / HTTP/1.1" 404 -
==> Detected a new open port HTTP:5000





# UPDATED LOG OUTPUT FOR DEPLOYING
==> Cloning from https://github.com/GShurgnarg/Label_Identification_App
==> Checking out commit c9941c8b33c9a7fce1e62c2c8b4184f4e4e595f1 in branch main
==> Using Python version 3.14.8 (default)
==> Docs on specifying a Python version: https://render.com/docs/python-version
==> Installing Python version 3.14.8...
==> Using Poetry version 2.1.3 (default)
==> Docs on specifying a Poetry version: https://render.com/docs/poetry-version
==> Running build command 'pip install -r requirements.txt'...
Collecting google-genai (from -r requirements.txt (line 1))
  Downloading google_genai-2.32.0-py3-none-any.whl.metadata (58 kB)
Collecting flask (from -r requirements.txt (line 2))
  Downloading flask-3.1.3-py3-none-any.whl.metadata (3.2 kB)
Collecting pillow (from -r requirements.txt (line 3))
  Downloading pillow-13.0.0-cp314-cp314-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl.metadata (9.1 kB)
Collecting gunicorn (from -r requirements.txt (line 4))
  Downloading gunicorn-26.2.0-py3-none-any.whl.metadata (5.5 kB)
Collecting anyio<5.0.0,>=4.8.0 (from google-genai->-r requirements.txt (line 1))
  Downloading anyio-4.15.1-py3-none-any.whl.metadata (4.7 kB)
Collecting google-auth<3.0.0,>=2.56.0 (from google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Downloading google_auth-2.62.0-py3-none-any.whl.metadata (6.0 kB)
Collecting httpx<1.0.0,>=0.28.1 (from google-genai->-r requirements.txt (line 1))
  Downloading httpx-0.28.1-py3-none-any.whl.metadata (7.1 kB)
Collecting pydantic<3.0.0,>=2.12.5 (from google-genai->-r requirements.txt (line 1))
  Downloading pydantic-2.14.1-py3-none-any.whl.metadata (133 kB)
Collecting requests<3.0.0,>=2.28.1 (from google-genai->-r requirements.txt (line 1))
  Downloading requests-2.34.2-py3-none-any.whl.metadata (4.8 kB)
Collecting tenacity<9.2.0,>=8.2.3 (from google-genai->-r requirements.txt (line 1))
  Downloading tenacity-9.1.4-py3-none-any.whl.metadata (1.2 kB)
Collecting websockets<17.0,>=13.0.0 (from google-genai->-r requirements.txt (line 1))
  Downloading websockets-16.1.1-cp314-cp314-manylinux1_x86_64.manylinux_2_28_x86_64.manylinux_2_5_x86_64.whl.metadata (6.8 kB)
Collecting typing-extensions<5.0.0,>=4.14.0 (from google-genai->-r requirements.txt (line 1))
  Downloading typing_extensions-4.16.0-py3-none-any.whl.metadata (3.3 kB)
Collecting distro<2,>=1.7.0 (from google-genai->-r requirements.txt (line 1))
  Downloading distro-1.9.0-py3-none-any.whl.metadata (6.8 kB)
Collecting sniffio (from google-genai->-r requirements.txt (line 1))
  Downloading sniffio-1.3.1-py3-none-any.whl.metadata (3.9 kB)
Collecting idna>=2.8 (from anyio<5.0.0,>=4.8.0->google-genai->-r requirements.txt (line 1))
  Downloading idna-3.20-py3-none-any.whl.metadata (7.2 kB)
Collecting pyasn1-modules>=0.2.1 (from google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Downloading pyasn1_modules-0.4.2-py3-none-any.whl.metadata (3.5 kB)
Collecting cryptography>=41.0.5 (from google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Downloading cryptography-50.0.2-cp311-abi3-manylinux_2_34_x86_64.whl.metadata (4.4 kB)
Collecting certifi (from httpx<1.0.0,>=0.28.1->google-genai->-r requirements.txt (line 1))
  Downloading certifi-2026.10.19-py3-none-any.whl.metadata (2.5 kB)
Collecting httpcore==1.* (from httpx<1.0.0,>=0.28.1->google-genai->-r requirements.txt (line 1))
  Downloading httpcore-1.0.9-py3-none-any.whl.metadata (21 kB)
Collecting h11>=0.16 (from httpcore==1.*->httpx<1.0.0,>=0.28.1->google-genai->-r requirements.txt (line 1))
  Downloading h11-0.16.0-py3-none-any.whl.metadata (8.3 kB)
Collecting annotated-types>=0.6.0 (from pydantic<3.0.0,>=2.12.5->google-genai->-r requirements.txt (line 1))
  Downloading annotated_types-0.8.0-py3-none-any.whl.metadata (15 kB)
Collecting pydantic-core==2.50.1 (from pydantic<3.0.0,>=2.12.5->google-genai->-r requirements.txt (line 1))
  Downloading pydantic_core-2.50.1-cp314-cp314-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (6.5 kB)
Collecting typing-inspection>=0.4.4 (from pydantic<3.0.0,>=2.12.5->google-genai->-r requirements.txt (line 1))
  Downloading typing_inspection-0.4.4-py3-none-any.whl.metadata (2.6 kB)
Collecting charset_normalizer<4,>=2 (from requests<3.0.0,>=2.28.1->google-genai->-r requirements.txt (line 1))
  Downloading charset_normalizer-3.5.2-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (46 kB)
Collecting urllib3<3,>=1.26 (from requests<3.0.0,>=2.28.1->google-genai->-r requirements.txt (line 1))
  Downloading urllib3-2.8.0-py3-none-any.whl.metadata (7.4 kB)
Collecting blinker>=1.9.0 (from flask->-r requirements.txt (line 2))
  Downloading blinker-1.9.0-py3-none-any.whl.metadata (1.6 kB)
Collecting click>=8.1.3 (from flask->-r requirements.txt (line 2))
  Downloading click-8.5.0-py3-none-any.whl.metadata (2.6 kB)
Collecting itsdangerous>=2.2.0 (from flask->-r requirements.txt (line 2))
  Downloading itsdangerous-2.2.0-py3-none-any.whl.metadata (1.9 kB)
Collecting jinja2>=3.1.2 (from flask->-r requirements.txt (line 2))
  Downloading jinja2-3.1.6-py3-none-any.whl.metadata (2.9 kB)
Collecting markupsafe>=2.1.1 (from flask->-r requirements.txt (line 2))
  Downloading markupsafe-3.0.4-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (2.7 kB)
Collecting werkzeug>=3.1.0 (from flask->-r requirements.txt (line 2))
  Downloading werkzeug-3.1.9-py3-none-any.whl.metadata (4.1 kB)
Collecting cffi>=2.0.0 (from cryptography>=41.0.5->google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Downloading cffi-2.1.1-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.whl.metadata (2.5 kB)
Collecting pycparser (from cffi>=2.0.0->cryptography>=41.0.5->google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Downloading pycparser-3.11-py3-none-any.whl.metadata (8.2 kB)
Collecting pyasn1<0.7.0,>=0.6.1 (from pyasn1-modules>=0.2.1->google-auth<3.0.0,>=2.56.0->google-auth[requests]<3.0.0,>=2.56.0->google-genai->-r requirements.txt (line 1))
  Downloading pyasn1-0.6.4-py3-none-any.whl.metadata (8.4 kB)
Downloading google_genai-2.32.0-py3-none-any.whl (1.2 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.2/1.2 MB 36.9 MB/s  0:00:00
Downloading anyio-4.15.1-py3-none-any.whl (132 kB)
Downloading distro-1.9.0-py3-none-any.whl (20 kB)
Downloading google_auth-2.62.0-py3-none-any.whl (267 kB)
Downloading httpx-0.28.1-py3-none-any.whl (73 kB)
Downloading httpcore-1.0.9-py3-none-any.whl (78 kB)
Downloading pydantic-2.14.1-py3-none-any.whl (488 kB)
Downloading pydantic_core-2.50.1-cp314-cp314-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (2.2 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.2/2.2 MB 106.0 MB/s  0:00:00
Downloading requests-2.34.2-py3-none-any.whl (73 kB)
Downloading charset_normalizer-3.5.2-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (255 kB)
Downloading idna-3.20-py3-none-any.whl (69 kB)
Downloading tenacity-9.1.4-py3-none-any.whl (28 kB)
Downloading typing_extensions-4.16.0-py3-none-any.whl (45 kB)
Downloading urllib3-2.8.0-py3-none-any.whl (135 kB)
Downloading websockets-16.1.1-cp314-cp314-manylinux1_x86_64.manylinux_2_28_x86_64.manylinux_2_5_x86_64.whl (187 kB)
Downloading flask-3.1.3-py3-none-any.whl (103 kB)
Downloading pillow-13.0.0-cp314-cp314-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl (7.1 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 7.1/7.1 MB 260.0 MB/s  0:00:00
Downloading gunicorn-26.2.0-py3-none-any.whl (228 kB)
Downloading annotated_types-0.8.0-py3-none-any.whl (13 kB)
Downloading blinker-1.9.0-py3-none-any.whl (8.5 kB)
Downloading certifi-2026.10.19-py3-none-any.whl (136 kB)
Downloading click-8.5.0-py3-none-any.whl (125 kB)
Downloading cryptography-50.0.2-cp311-abi3-manylinux_2_34_x86_64.whl (4.8 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 4.8/4.8 MB 155.2 MB/s  0:00:00
Downloading cffi-2.1.1-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (221 kB)
Downloading h11-0.16.0-py3-none-any.whl (37 kB)
Downloading itsdangerous-2.2.0-py3-none-any.whl (16 kB)
Downloading jinja2-3.1.6-py3-none-any.whl (134 kB)
Downloading markupsafe-3.0.4-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (23 kB)
Downloading pyasn1_modules-0.4.2-py3-none-any.whl (181 kB)
Downloading pyasn1-0.6.4-py3-none-any.whl (84 kB)
Downloading typing_inspection-0.4.4-py3-none-any.whl (14 kB)
Downloading werkzeug-3.1.9-py3-none-any.whl (228 kB)
Downloading pycparser-3.11-py3-none-any.whl (51 kB)
Downloading sniffio-1.3.1-py3-none-any.whl (10 kB)
Installing collected packages: websockets, urllib3, typing-extensions, tenacity, sniffio, pycparser, pyasn1, pillow, markupsafe, itsdangerous, idna, h11, gunicorn, distro, click, charset_normalizer, certifi, blinker, annotated-types, werkzeug, typing-inspection, requests, pydantic-core, pyasn1-modules, jinja2, httpcore, cffi, anyio, pydantic, httpx, flask, cryptography, google-auth, google-genai

Successfully installed annotated-types-0.8.0 anyio-4.15.1 blinker-1.9.0 certifi-2026.10.19 cffi-2.1.1 charset_normalizer-3.5.2 click-8.5.0 cryptography-50.0.2 distro-1.9.0 flask-3.1.3 google-auth-2.62.0 google-genai-2.32.0 gunicorn-26.2.0 h11-0.16.0 httpcore-1.0.9 httpx-0.28.1 idna-3.20 itsdangerous-2.2.0 jinja2-3.1.6 markupsafe-3.0.4 pillow-13.0.0 pyasn1-0.6.4 pyasn1-modules-0.4.2 pycparser-3.11 pydantic-2.14.1 pydantic-core-2.50.1 requests-2.34.2 sniffio-1.3.1 tenacity-9.1.4 typing-extensions-4.16.0 typing-inspection-0.4.4 urllib3-2.8.0 websockets-16.1.1 werkzeug-3.1.9

[notice] A new release of pip is available: 26.2.1 -> 26.2.2
[notice] To update, run: pip install --upgrade pip
==> Uploading build...
==> Uploaded in 2.8s. Compression took 1.3s
==> Build successful 🎉
==> Deploying...
==> Setting WEB_CONCURRENCY=1 by default, based on available CPUs in the instance
==> Running 'python Backend_python_app'
 * Serving Flask app 'Backend_python_app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://10.25.24.96:5000
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 860-572-465
127.0.0.1 - - [21/Oct/2026 19:43:24] "HEAD / HTTP/1.1" 200 -
==> Your service is live 🎉
127.0.0.1 - - [21/Oct/2026 19:43:27] "GET / HTTP/1.1" 200 -
==> 
==> ///////////////////////////////////////////////////////////
==> 
==> Available at your primary URL https://label-identification-app.onrender.com
==> 
==> ///////////////////////////////////////////////////////////
