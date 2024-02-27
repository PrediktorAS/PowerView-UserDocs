# Introduction to pyPrediktorMapClient

The pyPrediktorMapClient library offers a suite of helper functions designed to facilitate communication with Prediktor's OPC UA ModelIndex REST-API and OPC UA Values REST-API. It is particularly useful for data analytics applications. You can find example Jupyter Notebooks in the notebooks folder, providing practical insights into its usage.

## Installing pyPrediktorMapClient

To integrate the pyPrediktorMapClient library into your projects, simply execute the following command in your terminal or command prompt. This will install the latest version available on PyPi. 
```
pip install pyPrediktorMapClient
```

## Setting Up Local Development Environment
This guide outlines the steps to prepare a local environment for using the pyPrediktorMapClient library ([GitHub Repository URL](https://github.com/PrediktorAS/pyPrediktorMapClient)) effectively.

### Step 1: Prerequisites
Before diving into the installation, make sure you have the following prerequisites ready:
- **Python**: The latest version of Python installed on your system.
- **VPN Connection**: If necessary, establish a connection to the Prediktor VPN network to ensure access to the internal APIs..

### Step 2: Cloning and Environment Setup

1. **Clone the Repository**: Start by cloning the pyPrediktorMapClient repository to your local machine.
```
git clone git@github.com:PrediktorAS/pyPrediktorMapClient.git
```

2. **Create a virtual environment**: Isolate your project by creating a virtual environment.
```
python -m venv .venv
```
3. **Activate the virtual environment**: Depending on your operating system, activate the virtual environment.
- For Windows:
```
.venv\Scripts\activate
```
- For  macOS/Linux:
```
source .venv/bin/activate
```

### Step 3: Configuring Environment Variables

If developing locally, create a `.env` file in the project's root directory and populate it with necessary environment variables. If working in a different environment, define the environment variables accordingly.

The `.env` uses a syntax similar to Bash:
```
# Development settings
DOMAIN=example.org
ADMIN_EMAIL=admin@${DOMAIN}
ROOT_URL=${DOMAIN}/app
```

Note: The `.env` file is for local use only and should not be included in your version control system. Ensure it's listed in your `.gitignore`.

### Step 4: Installing Dependencies

Lastly, install the required Python packages within your activated virtual environment.
```
pip install -r requirements.txt
```

## Exploration of Functionalities 
The library facilitates interaction with various data types based on the objects in the Modelindex. To get started, open the `Exploring_API_Functions_Authentication` Jupyter notebook in the `notebooks` folder. This notebook:
1. **Import Packages and Modules**: Start by importing all necessary Python packages and specific functionalities like OPC UA and ModelIndex from the src folder.
3. **Load Credentials**: Load environment variables (credentials) from the `.env` file.
4. **Authenticate**: Obtain the authentication token required for accessing the certain APIs.
```
auth_client = AUTH_CLIENT(rest_url=ory_url, username=username, password=password)
```

### Using the ModelIndex API
Once authenticated, can can start interacting with the ModelIndex APIs.  
1. **Connect to ModelIndex API**: Establish a connection using the authentication token.
```
model_data = ModelIndex(url=model_index_url, auth_client=auth_client, session=auth_client.session)
```
2. **Retrieve Model URIs**: Obtain a list of dictionaries containing the Model URIs and their corresponding indices.
```
namespaces = model_data.get_namespace_array()
```
3. **Explore Object Types**: Get an overview of all object types present and access unique object types for more specific details. 
```
object_types_json = model_data.get_object_types()
object_types_unique = object_types.dataframe[["Id", "Name"]].drop_duplicates()
```
4. **Access Specific Object Type**:Utilize names to find object type IDs and query further.
```
object_type_id = model_data.get_object_type_id_from_name("SiteType")
```
5. **Work with Variables**: Access and manipulate variables in a structured format like Pandas DataFrame.
```
sites.variables_as_dataframe()
site_id = sites.list_of_ids()[1]
```
6. **Navigate Hierarchies**: Explore the relationship between different entities such as sites, string sets, and trackers.
```
string_sets_for_first_park_as_json = model_data.get_object_descendants("StringSetType", [site_id], "PV_Assets")
trackers_as_json = model_data.get_object_ancestors("TrackerType", string_sets_for_first_park.list_of_ids(), "PV_Serves")
```

### Accessing OPC UA API
The same authentication token allows for OPC UA API access.  
1. **Connect to OPC UA API**: Similar to ModelIndex API, establish a connection tailored for OPC UA functionalities.
```
opc_data = OPC_UA(rest_url=opcua_rest_url, opcua_url=opcua_server_url, namespaces=namespace_list, auth_client=auth_client)
```
2. **Retrieve Live Values**: Fetch current values of signals, including their timestamp and quality, from an OPC UA server.
```
live_value = opc_data.get_values(
    trackers.variables_as_list(["AngleMeasured", "AngleSetpoint"])
)
```
3. **Historical Data**: Obtain historical data for analysis, allowing for insights over time.  
```
one_day_historic_tracker_data = opc_data.get_historical_aggregated_values(
    start_time=(datetime.datetime.now() - datetime.timedelta(30)),
    end_time=(datetime.datetime.now() - datetime.timedelta(29)),
    pro_interval=3600000,
    agg_name="Average",
    variable_list=trackers.variables_as_list(["AngleMeasured"]),
)
```

