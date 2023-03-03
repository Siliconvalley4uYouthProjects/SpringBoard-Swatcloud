<h1># SpringBoard-Swatcloud</h1>

<h3>Data Collection:</h3>
<p>All scraping is done by one notebook called 'web_scraper_master_script.ipynb'. The original scraping notebooks for individual companies are under "web_scraping" folder.</p>
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
<li>Amazon, all jobs, Reusable, no human intervention</li>
<li>Google, all jobs, Reusable, no human intervention</li>
<li>Microsoft, all jobs, Reusable, no human intervention</li>
<li>JnJ, all jobs, Reusable, no human intervention</li>
<li>Deloitte, all jobs, Reusable, no human intervention</li>
<li>KPMG, all jobs, Reusable, no human intervention</li>
<li>Accenture, all jobs, Reusable, no human intervention</li>
<li>Dell, SW Engineer, Data Science / Data Analytics, Marketing</li>
<li>Walmart, SW Engineer, Data Science / Data Analytics, Marketing</li>
<li>Cisco, SW Engineer, Data Science / Data Analytics, Marketing</li>
<li>Infosys, SW Engineer, Data Science / Data Analytics, Marketing, Reusable, no human intervention</li>
<li>Collabera, all jobs, Reusable, no human intervention</li>
<li>IBM, all jobs, Reusable, no human intervention</li>
<li>Texas Instruments, all jobs, Reusable, no human intervention</li>
<li>Oracle, all jobs, Reusable, no human intervention</li>
<li>HP, all jobs, Reusable, no human intervention</li>
<li>Intel, all jobs, Reusable, no human intervention</li>
<li>Expedia, all USA jobs, Reusable, no human intervention</li>
<li>State Farm, all jobs, Reusable, no human intervention</li>
<li>Fox News, all jobs, Reusable, no human intervention</li>
<li>Apple, all jobs, Reusable, no human intervention</li>
<li>Vistra, all jobs, Reusable, no human intervention</li>  
<li>Vizient, all jobs, Reusable, no human intervention</li>  
  </ol>

<h3>FORMATTING FOR EACH CSV FILE IS AS FOLLOWS:</h3>
<li>Column 1: Company</li>
<li>Column 2: Job Title</li>
<li>Column 3: Qualifications</li>
<li>Column 4: Job Link URL</li>
<li>Column 5: Job Description</li>

<h3>Recommendation Model Part 1 - Cosine Similarity:</h3>
<li>This model works by taking all of the job descriptions and converting them into a matrix of word tokens using Sklearn's CountVectorizer. A user then provides some input (e.g. user's resume and/or list of technical skills) and the model calculates the cosine similarity between the input and all of the job descriptions. The top scoring matches are then recommended to the user along with their respective descriptions and a qualitative indicator of the degree of similarity. </li>


<h3>Recommendation Model Part 2a - Data Preprocessing (Industry Labeling):</h3>
<li>For the second model, we first begin by assigning industry labels to all of the job descriptions. The methodology for doing so is as such: </li>
<li> Step 1: A CountVectorizer is created and then the most common words/phrases are identified from the list of job titles </li>
<li> Step 2: These common keywords/phrases are assigned to selected industry labels and then the model runs through each job posting looking to assign an industry label to each posting based on the keyword that shows up the most (first prioritizing the job title and then if no matches are found it moves on to identify keywords in the job descriptions) </li>

<h3>Recommendation Model Part 2b - NLP Model:</h3>
<li>This model is built using Keras to train an NLP model from our job posting dataset wherein the model learns how to recognize the industry labels we assigned from the data preprocessing stage based on the job descriptions we provide for each of these industries. This model has an approximate testing accuracy of ~71% and has plenty of room to improve (an immediate area for improvement is the industry labeling: more industries can be added/taken away and the delineation between various industries is always subject to clearer definition). Once trained, this model then takes user inputs and presents a "closeness match" on a percentage scale.  </li>
