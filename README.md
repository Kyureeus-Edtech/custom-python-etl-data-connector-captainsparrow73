CISA KEV ETL Connector
Overview

This ETL script fetches data from the CISA Known Exploited Vulnerabilities (KEV) Catalog, transforms it by sanitizing keys and adding an ingestion timestamp, and loads it into a MongoDB collection.

Source URL: CISA KEV JSON Feed

Format: JSON

Authentication Required: No

Destination: MongoDB (etl_db.cisa_kev)

Tech Stack

Python 3.x

requests

pymongo

python-dotenv

MongoDB (Local or Atlas Cloud)

Project Structure

custom-python-etl-data-connector-captainsaprrow73/
├── .env                 # Environment variables (not committed to Git)
├── .gitignore           # Ignore .env, venv, cache files
├── requirements.txt     # Dependencies
├── etl_connector.py     # Main ETL script
└── README.md            # Project documentation

Environment Variables (.env)

Create a file named .env in the project root with the following content:
CISA_KEV_URL=https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json
MONGO_URI=mongodb://localhost:27017
MONGO_DB=etl_db
MONGO_COLLECTION=cisa_kev

Setup and Run
1. Clone the repository
git clone <your_repo_url>
cd custom-python-etl-data-connector-captainsparrow73
2. Create and activate virtual environment
python -m venv .venv

# Windows PowerShell
.\.venv\Scripts\Activate.ps1

# macOS/Linux
source .venv/bin/activate
3. Install dependencies
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
4. Run the ETL script
python etl_connector.py


Verify Data in MongoDB

If using local MongoDB:

mongosh
use etl_db
db.cisa_kev.find().limit(3).pretty()


Features

No authentication required.

Adds ingested_at UTC timestamp to each record.

Sanitizes keys for MongoDB compatibility.

Bulk insert for better performance.

Author

Name: Mohamed Imran Fareeth S
Roll No: <3122225001072>

