This Google Apps Script automates the process of connecting HubSpot data with Looker by exporting HubSpot deals data into a Google Sheet. The script dynamically pulls data based on specific filters, such as the deal creation date, and writes it into a Google Sheet, making it an ideal data source for Looker or other BI tools.

How the Code Works:

API Setup:
The script uses your HubSpot API key to authenticate requests. Replace 'yourkey' with your actual API key and update 'sheetID' and 'sheetName' with the appropriate values for your Google Sheet.

Data Retrieval:
It sends a request to the HubSpot API to fetch deals created in the last three months. The creation date is used as a filter to avoid exporting too many records, but this filter can be adjusted or removed depending on your needs.

Handling Pagination:
The script manages pagination to retrieve all deals that match the criteria. It loops through the API responses, adding each batch of deals to a list until all data is collected.

Writing Data to Google Sheets:
Clears any existing data in the specified Google Sheet.
Writes headers and iterates over the retrieved data to populate the sheet with each deal’s details, such as deal name, amount, close date, etc.

Optional: Filtering by Creation Date:
If you're working with a large dataset (over 2,000 deals), you can adjust the filters for the creation date to manage the volume of data retrieved:
Use one script to fetch deals from today to three months ago.
Use another script to fetch deals from three months ago to six months ago, and so on, as needed.
This approach helps to avoid exceeding HubSpot's API limits and ensures your Google Sheet can handle the data load.

Data Processing and Formatting:
The script includes helper functions to format dates and convert IDs (like pipeline and deal stage IDs) into human-readable names, making the data easier to understand.

Error Handling:
Basic error logging is included to catch and log any errors that occur during the data fetching or processing stages.

By using this script, you can automate the flow of data from HubSpot to Google Sheets and keep your Looker dashboards up-to-date without manual data exports. Adjust the filters and data retrieval logic as necessary based on the volume of data and specific reporting requirements.
