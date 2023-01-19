<h1># SpringBoard-Swatcloud</h1>

<h3>Data Collection:</h3>

Data scraping is not allowed by job searching websites such as Indeed and LinkedIn. Therefore our main job description data source is the careers website from each individual company.
Data scraping using BeautifulSoup is an efficient way to download jobs data from various company careers websites and was the main tool used in this project. But sometimes Selenium was used when we couldn’t effectively use BeautifulSoup on a particular website.
Here is how the job data scraping process works:
On a company careers site, the search results page may span across 20-50 pages for a particular category, like ‘software engineering’. Each page contains about 15 job titles and their links to the detailed job description page. The first part of our code will iterate over the 20-50 pages and scrape the job titles and the job description page links.
There will be a job description page for each job posting. Therefore, if there are a total of 1000 job postings, the job description information will be on 1000 different web pages. The second part of the code iterates over the links to scrape the “qualifications/requirements” section from each page.
Issues encountered in scraping:
The structure of the html file for different companies is not the same, therefore we need a separate script for each company. 
In most cases, the html file format is inconsistent within the same company’s website among different job positions. This is especially seen on the job descriptions pages. So we need to handle them with different codes. 
For each job category, the job searching was done using keywords, such as software engineer, marketing, data science etc.. It’s common that some searching results may have low relevance with the provided keywords. These need to be corrected to avoid wrong labels which will impact model performance if supervised machine learning is to be carried out later on.
Sometimes non-English postings are seen in the job listings. We tried to manually detect  and remove them.
After we scrape the data, sometimes we notice identical job titles and job descriptions posted several times. Therefore, we remove duplicates at the end. We also perform any major cleaning as needed before we add the new data to the existing data.
So far, job data is scraped from:

1. Amazon, SW Engineer, Data Science / Data Analytics, Marketing, Reusable, no human intervention
2. Google, SW Engineer, Data Science / Data Analytics, Marketing, Reusable, no human intervention
3. Microsoft, SW Engineer, Reusable, no human intervention
4. Meta, SW Engineer, Data Science / Data Analytics, Marketing, Have to login to see job display
5. Tesla, SW Engineer, Marketing, Only load 53 jobs, have to scroll down to load more data (no button click)
6. JnJ, Data Science / Data Analytics
7. Deloitte, Marketing, Jobs are not listed on separate pages. Currently we manually click ‘view more” button and save the html
8. KPMG, Marketing, Reusable, no human intervention
9. Visa, Marketing, Need to click ‘load more’ button
10. Dell, SW Engineer, Data Science / Data Analytics, Marketing
11. Walmart, SW Engineer, Data Science / Data Analytics, Marketing
12. Cisco, SW Engineer, Data Science / Data Analytics, Marketing
13. Infosys, SW Engineer, Data Science / Data Analytics, Marketing, Reusable, no human intervention


<h3>Model with keywords matching:</h3>


<h3>Model with description cosine similarity:</h3>
