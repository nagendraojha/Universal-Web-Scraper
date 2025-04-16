# Universal-Web-Scraper
Here’s a description for the README file explaining the provided Python code:

---

# Universal Web Scraper

This Python script is a universal web scraper designed to extract various elements from websites. It supports both static and dynamic content scraping using **requests** and **Selenium**. The scraper allows for customizable CSS selectors and can save scraped data to a JSON file for easy storage and processing.

## Features:
- **Extract Multiple Elements**: Supports scraping a variety of elements like ratings, reviews, price, title, description, images, and links.
- **Dynamic Content Handling**: Automatically handles JavaScript-rendered content using Selenium (headless Chrome browser).
- **Customizable CSS Selectors**: Users can provide their own CSS selectors to target specific elements on the page.
- **Output in JSON Format**: Scraped data is saved in a structured JSON file for easy analysis or further processing.

## Dependencies:
The script uses the following libraries:
- `requests` for sending HTTP requests.
- `BeautifulSoup` (from `bs4`) for parsing HTML.
- `Selenium` for scraping dynamic content (JavaScript-rendered pages).
- `re` for regular expressions (used for extracting ratings and other elements).
- `json` for saving the scraped data to a file.

To install the required libraries, run:
```bash
pip install requests beautifulsoup4 selenium
```

## How to Use:
1. **Run the Script**:
   - Simply execute the script in a Python environment. It will prompt you for input parameters.
   
   ```bash
   python scraper.py
   ```

2. **Enter Website URL**: 
   - Provide the URL of the website you wish to scrape.
   
3. **Select Elements to Scrape**:
   - Specify which elements you want to extract. For example: `ratings`, `reviews`, `price`, `title`, `images`, `links`.
   
4. **Handle Dynamic Content**:
   - Choose whether to use Selenium for scraping JavaScript-rendered pages (e.g., pages that load content dynamically).
   
5. **Custom Selectors**:
   - Optionally, you can provide custom CSS selectors for any of the elements you wish to scrape.
   
6. **Output Filename**:
   - Provide a filename to save the scraped data in JSON format (default is `scraped_data.json`).

## Example of Scraping Input:
```
Enter the URL to scrape: https://example.com
What elements do you want to scrape? (comma separated): ratings, reviews, price, title
Do you need to handle dynamic content? (JavaScript-rendered pages): Use Selenium? (y/n): n
Do you want to specify custom CSS selectors? (y/n): y
Enter CSS selector for ratings (or press Enter for auto-detection): .rating
Enter output filename (without extension): product_info
```

## Key Functions:
- **get_user_input**: Prompts the user to input the URL, elements to scrape, and other settings.
- **scrape_website**: Main function to scrape the website, choosing between requests-based scraping or Selenium-based scraping.
- **scrape_with_selenium**: Handles scraping of JavaScript-rendered pages using Selenium.
- **extract_elements**: Extracts the elements (ratings, reviews, price, etc.) from the parsed HTML.
- **specialized extraction functions**: Functions such as `extract_ratings`, `extract_reviews`, `extract_price`, etc., are used to extract specific elements from the page.
- **save_to_json**: Saves the scraped data to a JSON file.

## Example Output:
Once the data is scraped, the result will be saved in a JSON file with the specified filename, containing the extracted elements. Example:

```json
{
    "url": "https://example.com",
    "domain": "example.com",
    "ratings": [
        {
            "value": "4.5",
            "element": "<span class='rating'>4.5</span>",
            "selector": ".rating"
        }
    ],
    "reviews": [
        {
            "text": "Great product, highly recommend!",
            "author": "John Doe",
            "rating": "5",
            "date": "2025-04-15"
        }
    ],
    "price": {
        "value": "$49.99",
        "element": "<span class='price'>$49.99</span>",
        "selector": ".price"
    },
    "title": "Amazing Product",
    "description": "This is a great product for everyday use.",
    "images": [
        {
            "src": "https://example.com/image1.jpg",
            "alt": "Image 1",
            "width": "600",
            "height": "400"
        }
    ],
    "links": [
        {
            "text": "More Info",
            "href": "https://example.com/more-info"
        }
    ]
}
```

