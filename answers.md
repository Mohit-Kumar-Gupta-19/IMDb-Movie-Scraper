📘 Technical Questions & Answers
PERCEPTECH SOLUTIONS  Python Developer Assignment

Author: Mohit Kumar Gupta
Date: 7 November 2025

1️⃣ What Python libraries are you most experienced with for web scraping? Compare your top two choices.

I have the most experience with BeautifulSoup and Selenium, and some familiarity with Scrapy.
Here’s a brief comparison:

Feature	BeautifulSoup	Selenium
Type	HTML parser	Browser automation tool
Best for	Static websites with simple HTML structure	Dynamic websites with JavaScript-based content
Speed	Fast and lightweight	Slower due to browser rendering
Complexity	Easy to learn and implement	Requires more setup and resource usage
Dependencies	Works with requests	Requires browser driver (e.g., ChromeDriver)

When I use each:

✅ BeautifulSoup: When the target site’s content is available directly in HTML responses (like IMDb, Wikipedia, or blogs). It’s fast, efficient, and ideal for smaller or lightweight scraping tasks.

✅ Selenium: When the website uses heavy JavaScript (like Netflix, Amazon, or LinkedIn) or requires user interaction such as logging in, scrolling, or clicking buttons.

2️⃣ Common Techniques Websites Use to Detect and Block Scrapers

Websites often use several mechanisms to protect their data and ensure fair use. The three most common ones are:

Rate Limiting or IP Blocking:
Detects high-frequency requests from the same IP and temporarily or permanently blocks them.

User-Agent Detection:
Some websites check if the request headers contain a valid browser-like User-Agent. Requests without one are flagged as bots.

JavaScript Rendering / Dynamic Content:
Modern websites use frameworks like React or Angular to load data dynamically via JavaScript. HTML responses may appear empty to standard scrapers.

3️⃣ Mitigation and Ethical Handling Strategies

Here’s how I address those challenges responsibly and ethically:

Rate Limiting → Mitigation:

Add time delays between requests (time.sleep()).

Randomize request intervals.

Use pagination carefully.

Avoid parallel/mass scraping.

Ethics: Follow the website’s robots.txt file to respect scraping permissions.

User-Agent Detection → Mitigation:

Send realistic browser headers:

headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:122.0) Gecko/20100101 Firefox/122.0"}


Rotate between a few common browser agents.

Ethics: Avoid disguising the scraper as a malicious bot — only simulate normal browser access.

JavaScript Rendering → Mitigation:

Use Selenium or Playwright to load pages and capture rendered HTML.

Alternatively, analyze network calls from browser developer tools to find public JSON APIs.

Ethics: Minimize browser automation only for educational or fair-use purposes, and avoid login-based scraping.

4️⃣ Scraping Modern, Dynamic Websites (e.g., Netflix or Amazon Prime Video)

Websites like Netflix and Prime Video are heavily protected and rely on JavaScript-based rendering and authentication, which makes direct scraping extremely difficult.
Here’s how I would ethically approach determining streaming availability:

✅ Approach:

Official Data Sources:
Use OMDb API or JustWatch API instead of scraping directly.
These provide legal, structured access to streaming data.

Alternative Fallback:
Perform a Google search query like:

"Interstellar site:netflix.com OR site:primevideo.com OR site:disneyplus.com"


Then analyze result snippets using BeautifulSoup to detect platform names.

Dynamic Rendering Tools:
If absolutely required:

Use Selenium or Playwright to open pages and extract visible streaming platform info.

Control request rate and use headless browsing to simulate user activity ethically.

Ethics & Legality:

Respect each platform’s Terms of Service.

Avoid accessing login-protected pages or copyrighted metadata directly.

Use APIs or aggregators (like JustWatch) for reliable data.

5️⃣ Designing a Resilient and Robust Scraping Script

A strong scraper should not break easily and should gracefully handle all types of errors.
Here’s how I design mine:

✅ 1. Network Resilience

Wrap all requests in try-except blocks:

try:
    response = requests.get(url, headers=headers, timeout=10)
    response.raise_for_status()
except requests.exceptions.RequestException as e:
    print(f"⚠️ Network error: {e}")


Use retries (for loops or requests.adapters.Retry).

✅ 2. Handle HTML Structure Changes

Use CSS selectors and conditional checks instead of absolute element positions.

Implement fallback logic:

title = soup.find("h1") or soup.select_one(".title")

✅ 3. Manage Missing or Partial Data

Provide default placeholders ('N/A') for missing fields:

director = details.get("Director", "N/A")

✅ 4. Logging & Debugging

Log all successful and failed scrapes for traceability.

Print URLs or error codes when unexpected responses appear.

✅ 5. Maintain Ethical Scraping Practices

Limit request frequency.

Respect robots.txt.

Identify the purpose of data collection (research, education, or evaluation).

✅ Summary of Best Practices
Aspect	Strategy
Performance	Limit to top 10 results, short timeouts
Reliability	Use API (OMDb) + fallback scraper
Ethics	Respect site policies, limit request frequency
Maintainability	Modular functions and clear documentation
🏁 Final Takeaway

This project demonstrates:

Strong practical understanding of Python-based web scraping

Hands-on use of APIs (OMDb) and HTML parsing (BeautifulSoup)

Ethical and professional approach to automation

Code that is resilient, modular, and production-ready
