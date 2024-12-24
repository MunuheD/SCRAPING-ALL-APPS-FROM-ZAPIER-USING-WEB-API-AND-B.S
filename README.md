# Zapier Data Scraping Project

## Overview
The goal of the project is to ETHICALLY extract all the apps (around 7700) listed in the Zapier platform (https://zapier.com/apps); 
the details to be scraped are the app's name, the app's description, and its unique URL.
To extract the app's name and the links to crawl, I used a Python scraping tool that first used Zapier's web API,
which I documented using Chrome's developer tool. I then used a crawler that applied Beautiful Soup to
extract app details and the app's external URL. The project would have taken a human approximately five days to complete. 
My Python bot completed the entire task within 7 hours!

### Key Features
1. **API Interaction**: Retrieves a list of applications from the Zapier Explore API in batches.
2. **Web Scraping**: Extracts detailed information (descriptions and URLs) from application profiles using Beautiful Soup.
3. **Batch Processing**: Processes data in manageable batches to optimize memory usage and track progress.
4. **File Management**: Saves each batch of results to separate Excel files.
5. **File Consolidation**: Combines all batch files into a single Excel file for ease of analysis.

## Requirements
### Dependencies
- Python 3.x
- Required Python Libraries:
  - requests
  - pandas
  - openpyxl
  - beautifulsoup4

### Folder Structure
Ensure your workspace is structured as follows:
```
project_directory/
├── zapier_scraper.py  # Main script file
├── output/            # Folder where batch and combined Excel files will be stored
└── README.md          # Documentation
```

## Steps to Run
### 1. API Interaction
The script interacts with the Zapier Explore API to fetch application data in batches.
- **Endpoint**: https://zapier.com/explore-api
- **Headers**: Include User-Agent, Content-Type, x-api-key, and x-csrftoken.
- **Payload**: Contains dynamic offset and limit parameters to iterate through all available applications.

Run the script to generate the initial dataset.

### 2. Web Scraping with Beautiful Soup
- Processes each application profile URL fetched from the API.
- Extracts application descriptions and URLs for detailed information.

### 3. Batch Processing
The script divides the dataset into smaller batches (default size: 100 records) and saves each batch to an Excel file.

### 4. File Consolidation
Finally, the script combines all the batch files into a single Excel file:
- Input: Excel files named `ZapierScrapingResults_batch_*.xlsx`.
- Output: Combined_ZapierScrapingResults.xlsx containing all application data.

## Configuration
### Adjustable Parameters
- Base API URL.
- Headers for authentication or user-agent changes.
- Batch size to optimize performance.
- Output directory to save Excel files.

### File Paths
Update the paths in the script to match your file storage location.

## Error Handling
The script includes robust error handling:
- Retries failed requests up to 10 times.
- Logs failed URLs for review.
- Handles missing data gracefully by assigning default values (e.g., "not given").

## Outputs
1. **Batch Files**: Excel files named ZapierScrapingResults_batch_1.xlsx, ZapierScrapingResults_batch_2.xlsx, etc.
2. **Final Combined File**: Combined_ZapierScrapingResults.xlsx containing all application data.

## Ethical Considerations
The script adheres to ethical scraping practices by:
- Using a User-Agent header to identify requests.
- Including delays to prevent server overload.
### Disclaimer

**Please note that this script relies on the structure of the https://zapier.com/apps website to extract data.** If the website's layout or structure changes, the script may fail to work as expected. In such cases, the HTML parsing logic and URL generation may need to be updated to align with the new structure of the site.

## Conclusion
This project demonstrates an end-to-end data scraping solution, leveraging both APIs and web scraping techniques
for structured data extraction. By following the steps above, you can reproduce the results and customize the script 
for similar projects.


