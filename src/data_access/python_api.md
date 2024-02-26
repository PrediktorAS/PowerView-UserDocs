# Introduction to pyPrediktorMapClient

Helper functions for communicating with Prediktors OPC UA ModelIndex REST-API and OPC UA Values REST-API. Typically used for data anlytics purposes, you'll find Jypiter Notebooks with examples in the notebooks folder.

# Installation of pyPrediktorMapClient

To install the pyPrediktorMapClient library, use the command pip install pyPrediktorMapClient via PyPi. 

## Local Installation of Python Code

### Step 1: Prerequisites
Before starting, ensure you meet the following prerequisites:
- **Python**: Latest version of Python installed.
- **VPN Connection**: Connection to the Prediktor VPN network or access to APIs.

### Step 2: Installation Setup

1. Start by cloning the repository.

```
git clone git@github.com:PrediktorAS/pyPrediktorMapClient.git
```

2. Create a virtual environment

```
python -m venv .venv
```
3. Activate the virtual environment

```
.venv\Scripts\activate  (For Windows)
source .venv/bin/activate (For macOS/Linux)
```

### Step 3: Define the environment variables

If developing locally, create a `.env` file in the project's root directory and add the environment variables. If working in a different environment, define the environment variables accordingly.

The `.env` uses a syntax similar to Bash:

```
# Development settings
DOMAIN=example.org
ADMIN_EMAIL=admin@${DOMAIN}
ROOT_URL=${DOMAIN}/app
```

The environment file is not meant to be committed to source control, it is added to the .gitignore file.

### Step 4: Install Dependencies

Install Python packages within the working directory:
```
pip install -r requirements.txt
```

## Exploration of Functionalities 
The library facilitates interaction with various data types based on the objects in the Modelindex. To get started, open the `Exploring_API_Functions_Authentication` Jupyter notebook in the `notebooks` folder. This notebook:
1. Imports necessary Python packages.
2. Imports functionalities such as OPC UA and ModelIndex from scripts in the `src` folder.
3. Imports environment variables (credentials) from the `.env` file.
4. Retrieves the authentication token required for accessing the certain APIs.

### Modelindex API
With above settings and authentication token, can be connected to model index APIs.
1. To get a list of dictionaries containing the Model Uris and its corresponding indices from the Model Index.
2. Obtaining an overview of all object types present in the Model Index.
3. TAccessing unique object types, represented by unique IDs, which can be further queried for specific details. For instance, using ID 6:0:1009 provides information about all listed sites.
4. Conversely, accessing object type IDs using names obtained from the aforementioned approach.  




