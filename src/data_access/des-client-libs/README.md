# Prediktor DataEngineering Client Library 
A Prediktor python library (python 3) to be used for dataengineering with APIS monitored data. Typical usage is with Jupyter Notebook or other python code.

A typical setup is a python environment on you local computer, and a centralized server running Prediktor DataEngineering Service (REST API) that connects to various databases, APIS and Honeystore to extract data.

# Prediktor DataEngineering Architecture
![DataEngineering Architecture](../img/DataEngineering_architecture1.png)

# Prediktor DataEngineering App for Scatec
A web application that utilize the DataEngineering Clientlibs Library together with custom customer scripts. The scripts can be manually triggered or executed automatically by the scheduler. 

To enable a script as an URL in the DataEngineering App, this needs to be ordered from Prediktor AS. 

# Available URLs for Scatec
| Endpoint URL | Description | Parameters |
|--------------|-------------|------------|
| / | Status and app information   | None |
| /api | Redirect to DataEngineering Service API | None |
| /bokeh_stringperformance | Web application | None |
| /invoke | Invoke any of the supported scripts outputed | Required |
| /log_entry | Script | Required |

The URL /log_entry can be used to verify if the clientlibs library and dataengineering-service is responding properly.  Call the log_entry with parameter `log_entry?id=test`  
If there is an error, the dataengineering-service connection will re-initialized.  


# Prerequisites 
__Always use shell/prompt with administrator rights!__

Install the conda environment on your computer: 
- Install miniconda (https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html)

## Install Prediktor DataEngineering Client Library 
- create a folder c:/prediktor/clientlibs/ 
- Download the latest clientlibs source code (zip) and unzip to c:/prediktor/clientlibs/ 

Your folder structure should now look like:  
- prediktor  
  - clientlibs  
    - clientlibs folder with python source code
    - setup.py 
    - additional files and subfolders

## Setup conda environment with clientlibs
- Open an anaconda prompt with administrator rights
- Change directory to c:/prediktor/clientlibs/ 

### Create an isolated virtual environment with clientlibs and its dependencies
You can install clientlibs to the base environment if you want, but we recommend using a separate environment.

- Create a new environment with python, conda and pip, force recreate if already exits (skip this step if you already have an environment with correct version of python, conda and pip)
- `conda create --name clientlibsEnv python=3.7 conda=4.7 pip=19.2`
- Activate the environment
- `conda activate clientlibsEnv`
- Install clientlibs library and its dependencies (fixed versions)
- `python setup.py install`
- If you want to update to the latest version of all dependencies you can run `python setup.py installLatest` instead (you should understand the difference between fixed versions and latest available version)
- Run the unit tests to verify dependencies
- `pytest -s -v .\tests\unit`

# Using clientlibs python library
You can use the clientlibs python library with any tool supporting python.
The anaconda environment described in the installation process is needed.  

If you use conda virtual environment, a yml file is provided enabling you to create the basic of the environment from the yml file.

This sample code should get you started:  

```python
from clientlibs import *

#Change the URL to the URL of the rest service to your server
deSession = initialize('http://your-server:5000/api/DataEngineering/', alias='Scatec')

# Use any other function from the clientlibs
```

The api documentation is available as docstrings in the Prediktor DataEngineering Client Library.
You can view it with pydoc or your favorite python IDE.


# Example code
There are testfiles located in the folder tests/  
These can be run to test the clientlibs library and to see example code of usage.  
The tests are implemented using pytest framework.  
The test configuration is located in conftest.py  

## Connection and Code Example
This small example connects to the remote server and queries various data. The example code can be copy/pasted to a Jupyter Notebook.  
The import statement might be adjusted if clientlibs is not in a subfolder of your current working directory.

```python
# import the library
from clientlibs import *

# Make a connection to the remote server
deSession = initialize('http://your-server:<port>/api/DataEngineering/', alias='<Your alias>')

# Load the domains into local variables for easier access
pViewAssets = deSession.domains.PV_Assets
pViewServes = deSession.domains.PV_Serves

# Find all weather stations. Here we use the *assets* domain
weather_stations = pViewAssets.get_objects_of_type(deSession.types.WeatherStationType)
weather_stations

# Find the connection between weather stations and inverters using the *serves* domain
inverters = pViewServes.get_children_of_type(weather_stations, deSession.types.InverterType)
inverters

# Find all sites
sites = pViewAssets.get_objects_of_type(deSession.types.SiteType)
sites

# Get a specific site
sitename = "JO-GL"
site = sites.loc[sites.Name == sitename]
site

# Find all string sets within a site. Here we use the *assets* domain
stringsets = pViewAssets.get_children_of_type(site,deSession.types.StringSetType)
stringsets

# Read aggregated time-series values between two dates with a resampling interval of 1 minute using average as aggregation method. See read_aggregated documentation for more information
data = deSession.read_aggregated(
        stringsets, start='2020-04-01', stop='2020-04-02', interval='1 minute',
        include_variables=['NominalDCPower', 'ModuleTemperatureCoefficient'], aggregation='average')
data


# Read real time values for strings
data = deSession.read_variables(
         stringsets, 
         'NominalDCPower')
data

# Write model result to DES database
d_write = {'ObjectType': ['Inverter'],
     'ObjectName': ['Inv01'],
     'ResultType': ['PR'],
     'Time': [nu.datetime64('2022-10-13')],
      'Value': [32.555]
    }
df_write = pd.DataFrame(d_write)
deSession.write_model_result(df_write, *df_write.columns)

# Read model result from DES database
d_read = {'ObjectType': ['Inverter'],
     'ObjectName': ['Inv01'],
     'ResultType': ['PR'],
     'FromTime': [pd.to_datetime('2022-10-12T12:00:00')],
     'ToTime': [pd.to_datetime('2022-10-14T13:00:00')]
    }
df_read = pd.DataFrame(d_read)


# Write model parameters to DES database
import pandas as pd
d = {'ObjectName': ['ERLING1'],
     'ParameterType': ['N01'],
      'Value': [32.555]}
df = pd.DataFrame(d)
deSession.write_model_parameters(df, *df.columns)

# Read model parameters from DES database
df_read = df[['ObjectName', 'ParameterType']]
deSession.read_model_parameters(df_read, *df_read.columns)

# Execute PView DWH stored procedure, example GetTimeseriesData
d = {'FacilityName' : ['JO-GL'],
     'Resolution' : '600',
    'Aggregation' : 'Average',         
     'TagName' : ['JO-GL-TS01-I01.INV-AC_voltage_phase_BC'],
    'FromDate' : '2022-08-01',
    'ToDate' : '2022-09-01'}
deSession.exec_procedure(db_alias='SSO_DWH', proc_name='GetTimeseriesData', arguments=d)

```
See also [DES DWH Methods](DES_DWH_Methods.md)


# Troubleshooting, Tips and Tricks

## Python dependencies not found or something strange going on
- Update clientlibs:
- `python setup.py install`
  
- Delete the folder `__pycache__` in several folders (module and test folders)

- Create a new virtual environment from the yml file.  

- Reinstall clientlibs (see below)

### Reinstall clientlibs:  
- Delete the clientlibs/ folder located in c:/prediktor/
- Download the latest clientlibs source code (zip) and unzip to c:/prediktor/clientlibs/ 
- Activate your existing environment (`conda activate clientlibsEnv`)
- In your anaconda prompt (administrator), navigate to clientlibs folder (eg. c:\\prediktor\\clientlibs), run the command:  
- `pip uninstall clientlibs`
- Reinstall clientlibs:  
- `python setup.py install`

