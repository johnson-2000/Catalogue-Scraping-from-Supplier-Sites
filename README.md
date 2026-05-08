## Catalogue Scraping from Supplier Sites

### Project Overview
This project focuses on automating the extraction of product catalogue data from vendor websites 
at scale. It utilizes **Python** and **Selenium** to scrape inventory data such as product 
attributes, specifications, and URLs for thousands of SKUs, eliminating the need for manual 
lookups and building a structured product database from supplier sites. The script is designed 
to be easily extended to capture any additional data points available on the vendor's product pages.

---

### Base Script Overview
The base script automates the scraping process and populates an output Excel file used for 
catalogue management. It involves several key steps:

**1. Loading and Resuming Data**
- Checks for an existing output file to resume from where the script last stopped.
- Falls back to the input file for a fresh run if no prior output exists.
- Ensures all required columns are present before processing begins.

**2. Initializing the Browser**
- Launches an undetected Chrome browser instance to avoid bot detection.
- Configures a WebDriver wait for reliable element loading on each page.

**3. Iterating Through Material Numbers**
- Loops through the list of material numbers from the input file.
- Skips rows that already contain scraped data to avoid redundant requests.

**4. Scraping Product Data**
- Navigates to the vendor's search page for each SKU.
- Extracts product attributes and specifications available on the product page.
- The script can be extended to capture any additional data fields the vendor site exposes,
  such as **pricing**, **availability**, **dimensions**, **certifications**, and more.

**5. Handling Blocks and CAPTCHAs**
- Detects CAPTCHA pages and pauses execution for manual resolution before continuing.
- Stops and saves progress automatically if data is missing, indicating a likely site block.

**6. Saving Output Incrementally**
- Writes scraped data back to the output Excel file after every item to prevent data loss.
- Ensures a clean, resumable state at all times during the run.

**7. Human-Like Pacing and Cooldowns**
- Applies random delays between requests to mimic human browsing behavior.
- Triggers extended cooldown periods every 18 items to avoid rate-limiting and IP blocks.

---

### Python Skills Demonstrated

- **Web Automation** — Using Selenium and undetected-chromedriver to interact with live websites
  while bypassing bot detection.
- **Data Extraction & Manipulation** — Reading and writing structured data from Excel files 
  using pandas.
- **Resume Logic** — Implementing checkpoint-based resumption to handle interruptions gracefully.
- **Error Handling** — Catching exceptions for missing data and site blocks, saving progress 
  before stopping.
- **Anti-Detection Techniques** — Applying randomized delays and cooldown periods to simulate 
  human behavior.
- **Progress Tracking** — Using `tqdm` for real-time progress updates with live status 
  in the terminal.

---

This base script serves as the foundational element for building a supplier product catalogue 
database, providing a reliable and scalable approach to automated data collection from vendor 
websites. By design, the script is modular and can be extended to scrape any additional product 
attributes available on the site — making it a flexible foundation for building a comprehensive 
catalogue database.
