# Web Scraping with Python

This Python script demonstrates a basic web scraping technique to retrieve and parse data from a web page. It uses the urllib library to make an HTTP request and the re module to extract specific content from the page.

## Table of Contents
- [Description](#description)
- [Dependencies](#dependencies)
- [Code Explanation](#code-explanation)
- [Usage](#usage)
- [Example](#example)
- [Conclusion](#conclusion)

## Description

This script sends a search query to a website and extracts the content of <p> (paragraph) tags from the HTML response. It is a basic example of how to use Python for web scraping and can be adapted for more complex tasks.

## Dependencies

- Python 3.x
- Standard Python libraries: urllib and re (no external libraries required)

## Code Explanation

### 1. Import Libraries

import urllib.request
import urllib.parse
import re
- `urllib.request: For sending HTTP requests and receiving responses.
- urllib.parse: For encoding query parameters.
- re: For regular expression operations to parse HTML content.

### 2. Define URL and Query Parameters

``python
url = 'http://pythonprogramming.net'
values = {'s': 'basics',
          'submit': 'search'}

- `url`: The target URL to send the request.
- `values`: Dictionary containing query parameters to be sent with the request.

### 3. Encode Query Parameters

python
data = urllib.parse.urlencode(values)
data = data.encode('utf-8')

- `urllib.parse.urlencode()`: Encodes the dictionary into a query string.
- `.encode('utf-8')`: Converts the query string into bytes, which is necessary for sending in the HTTP request.

### 4. Create and Send the HTTP Request

python
req = urllib.request.Request(url, data)
resp = urllib.request.urlopen(req)
respData = resp.read()

- `urllib.request.Request()`: Prepares the request with the URL and encoded data.
- `urllib.request.urlopen()`: Sends the request and gets the response.
- `.read()`: Reads the response data.

### 5. Extract Paragraphs from HTML

python
paragraphs = re.findall(r'<p>(.*?)</p>', str(respData))

- `re.findall()`: Uses a regular expression to find all occurrences of `<p>` tags and extract their content.

### 6. Print Extracted Paragraphs

python
for eachP in paragraphs:
    print(eachP)

- Iterates over the extracted paragraphs and prints each one.

## Usage

1. **Set up the script**: Copy the code into a Python file (e.g., `web_scraping.py`).
2. **Modify parameters**: Adjust the `url` and `values` if needed to target different pages or search terms.
3. **Run the script**: Execute the script using Python:
   
bash
   python web_scraping.py
   `
4. **View results**: The script will print out the content of all `<p>` tags found in the HTML response.

## Example

This script targets the URL `http://pythonprogramming.net` and performs a search with the query parameter `'s': 'basics'`. The content of all `<p>` tags from the search results page will be extracted and printed.

## Conclusion

This project illustrates basic web scraping techniques using Python's standard libraries. It can be extended to handle more complex tasks, such as scraping other HTML elements, handling pagination, or managing cookies and sessions.

