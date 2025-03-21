Python is pretty decent and a quick alternative to data manipulation and scripting. gspread is a library used for data ingest, manipulation and creation of google spreadsheets and can prove to be a powerful tool if the workplace habitually uses the google suits.

[gspread docs](https://docs.gspread.org/en/v6.1.2/index.html)

```python
#Import these libraries are essential
import gspread
#Google Cloud account must be set up
from google.oauth2.service_account import Credentials

```

A Google Cloud Service Account is necessary and requires a Google Cloud account. Documentation can be acquired [here](https://cloud.google.com/). 
[1] It's worth creating an account in general for use of linking YouTube videos.


```python
def getSheet():
	# Scope defines the actions you can perform on spreadsheet
	scopes = ["https://www.googleapis.com/auth/spreadsheets"]
	# Ingests a credentials to assure permissions and sets scope of actions
	creds = Credentials.from_service_account_file("creds.json", scopes = scopes)
	# Authorize gspread to Google Cloud API
	client = gspread.authorize(creds)
	# Spreadsheet ID and opens it within the script
	sheets_id = '1hZKAYyg6N5ImNGghRs9TUy7Wodw9lxkQhvRhoh_Cj2Y'
	sheet = client.open_by_key(sheets_id)
```