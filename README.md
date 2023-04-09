# Web-cloner-

import requests
from bs4 import BeautifulSoup
from googletrans import Translator

# Replace YOUR_API_KEY with your actual Google Cloud API key
translator = Translator(service_urls=['translate.google.com'], 
                        timeout=5, 
                        client_kwargs={'headers': {'Referer': 'https://www.google.com/', 
                                                   'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36'}}, 
                        credentials='YOUR_API_KEY')

# Specify the URL of the webpage you want to translate
url = 'https://en.wikipedia.org/wiki/Python_(programming_language)'

# Fetch the webpage content
response = requests.get(url)

# Parse the webpage content using BeautifulSoup
soup = BeautifulSoup(response.content, 'html.parser')

# Extract the text content of the webpage
html = soup.get_text()

# Translate the webpage content to Hindi
translated_html = translator.translate(html, dest='hi').text

# Print the translated content
print(translated_html)
