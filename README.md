<h1># SpringBoard-Swatcloud</h1>

<h3>Data Collection:</h3>

<p>Data scraping is not allowed by job searching websites such as Indeed and LinkedIn. Therefore our main job description data source is the careers website from each individual company.</p>
<p>Data scraping using BeautifulSoup is an efficient way to download jobs data from various company careers websites and was the main tool used in this project. But sometimes Selenium was used when we couldn’t effectively use BeautifulSoup on a particular website.</p>
<p>Here is how the job data scraping process works:</p>
<ul><li>
On a company careers site, the search results page may span across 20-50 pages for a particular category, like ‘software engineering’. Each page contains about 15 job titles and their links to the detailed job description page. The first part of our code will iterate over the 20-50 pages and scrape the job titles and the job description page links.</li>
<li>There will be a job description page for each job posting. Therefore, if there are a total of 1000 job postings, the job description information will be on 1000 different web pages. The second part of the code iterates over the links to scrape the “qualifications/requirements” section from each page.
Issues encountered in scraping:</li>
<li>The structure of the html file for different companies is not the same, therefore we need a separate script for each company. 
<li>In most cases, the html file format is inconsistent within the same company’s website among different job positions. This is especially seen on the job descriptions pages. So we need to handle them with different codes.</li>
<li>Sometimes non-English postings are seen in the job listings. We tried to manually detect  and remove them.</li>
<li>After we scrape the data, sometimes we notice identical job titles and job descriptions posted several times. Therefore, we remove duplicates at the end. We also perform any major cleaning as needed before we add the new data to the existing data.</li>
</ul></br>
<span>So far, job data is scraped from:</span>
</br>
<ol>
<li>Amazon, SW Engineer, Data Science / Data Analytics, Marketing, Reusable, no human intervention</li>
<li>Google, SW Engineer, Data Science / Data Analytics, Marketing, Reusable, no human intervention</li>
<li>Microsoft, SW Engineer, Reusable, no human intervention</li>
<li>Meta, SW Engineer, Data Science / Data Analytics, Marketing, Have to login to see job display</li>
<li>Tesla, SW Engineer, Marketing, Only load 53 jobs, have to scroll down to load more data (no button click)</li>
<li>JnJ, Data Science / Data Analytics</li>
<li>Deloitte, Marketing, Jobs are not listed on separate pages. Currently we manually click ‘view more” button and save the html</li>
<li>KPMG, Marketing, Reusable, no human intervention</li>
<li>Visa, Marketing, Need to click ‘load more’ button</li>
<li>Dell, SW Engineer, Data Science / Data Analytics, Marketing</li>
<li>Walmart, SW Engineer, Data Science / Data Analytics, Marketing</li>
<li>Cisco, SW Engineer, Data Science / Data Analytics, Marketing</li>
<li>Infosys, SW Engineer, Data Science / Data Analytics, Marketing, Reusable, no human intervention</li>
<li>Collabera, all jobs, Reusable, no human intervention<li>
  </ol>


<h3>Model with keywords matching:</h3>


<h3>Model with description cosine similarity:</h3>
