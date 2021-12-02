# Craiglist scrapper  (DEMO)

Scrapper for Craiglist site
----

# Features:

- Filtering by sites (US,EU,...), states/country, cities, see https://www.craigslist.org/about/sites 
- Extraction of jobs and services, including filter by jobs type, search nearby and only in titles
- Generate .csv and .xlsx 
- Parallel execution

### Sample 1

Searching "python" jobs (fulltime and partime) in Europe site, restricting to Austria and Germany, saving output to csv file 'eu_jobs.csv' and stdout, 4 parallel request, random delay between 1 and 5 sec, info log level,  
```
$  craiglist_scrapper -co EU -st Austria Germany -W 4 -w 5 -j 1 2 -C jobs -q "python" -LI  -fc eu_jobs.csv -s
INFO:ktxo.scrapper.craiglist:craiglist_scrapper v0.1.0 (2021-12-01) by ktxo
INFO:ktxo.scrapper.craiglist:Python version 3.8.11 (default, Aug  3 2021, 15:09:35) [GCC 7.5.0]
INFO:ktxo.scrapper.craiglist:BeautifulSoup version 4.8.2
INFO:ktxo.scrapper.craiglist:Starting pid=462081
INFO:ktxo.scrapper.craiglist:Using args Namespace(category='jobs', cities=None, countries=['EU'], craiglist_config=None, exclude_domain_list=None, exclude_domain_pattern=None, file_csv='eu_jobs.csv', file_xlsx=None, job_types=[1, 2], load_location=None, log=None, log_level='I', only_in_titles=False, pages=1, query='python', save=True, save_location=False, search_nearby=False, show_config=False, silent=False, states=['Austria', 'Germany'], version=False, wait_value=5, workers=4)
INFO:ktxo.scrapper.craiglist:Getting from Austria-['vienna']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['berlin']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['bremen']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['cologne']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['dresden']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['dusseldorf']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['essen / ruhr']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['frankfurt']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['hamburg']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['hannover']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['heidelberg']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['kaiserslautern']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['leipzig']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['munich']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['nuremberg']
INFO:ktxo.scrapper.craiglist:Getting from Germany-['stuttgart']
INFO:ktxo.scrapper.craiglist:Got 4 items
-  --  -------  ---------  ----------------  -------------  --------------------------------------------------------  ---------------------------------------------------------------------------------------
0  EU  Austria  vienna     2021-10-22 11:36  muc > München  BUSINESS INTELLIGENCE ANALYST (m/w/d) | 100%| SAUSALITOS  https://munich.craigslist.org/fbh/d/business-intelligence-analyst-w-100/7397509284.html
1  EU  Germany  dresden    2021-10-22 11:36  muc > München  BUSINESS INTELLIGENCE ANALYST (m/w/d) | 100%| SAUSALITOS  https://munich.craigslist.org/fbh/d/business-intelligence-analyst-w-100/7397509284.html
2  EU  Germany  munich     2021-10-22 11:36  München        BUSINESS INTELLIGENCE ANALYST (m/w/d) | 100%| SAUSALITOS  https://munich.craigslist.org/fbh/d/business-intelligence-analyst-w-100/7397509284.html
3  EU  Germany  nuremberg  2021-10-22 11:36  muc > München  BUSINESS INTELLIGENCE ANALYST (m/w/d) | 100%| SAUSALITOS  https://munich.craigslist.org/fbh/d/business-intelligence-analyst-w-100/7397509284.html
-  --  -------  ---------  ----------------  -------------  --------------------------------------------------------  ---------------------------------------------------------------------------------------

```
CSV
```
# Extracted: 2021-12-02 18:34:41.465590 UTC
SITE,LOCATION,CITY,DATETIME,EXRA,DESCRIPTION,URL
EU,Austria,vienna,2021-10-22 11:36,muc > München,BUSINESS INTELLIGENCE ANALYST (m/w/d) | 100%| SAUSALITOS,https://munich.craigslist.org/fbh/d/business-intelligence-analyst-w-100/7397509284.html
EU,Germany,dresden,2021-10-22 11:36,muc > München,BUSINESS INTELLIGENCE ANALYST (m/w/d) | 100%| SAUSALITOS,https://munich.craigslist.org/fbh/d/business-intelligence-analyst-w-100/7397509284.html
EU,Germany,munich,2021-10-22 11:36,München,BUSINESS INTELLIGENCE ANALYST (m/w/d) | 100%| SAUSALITOS,https://munich.craigslist.org/fbh/d/business-intelligence-analyst-w-100/7397509284.html
EU,Germany,nuremberg,2021-10-22 11:36,muc > München,BUSINESS INTELLIGENCE ANALYST (m/w/d) | 100%| SAUSALITOS,https://munich.craigslist.org/fbh/d/business-intelligence-analyst-w-100/7397509284.html
```


### Sample 2
Listing states in US site, warning log level

```
$ craiglist_scrapper -C states -co US -LW
{
    "US": [
        "Alabama",
        "Alaska",
        "Arizona",
        "Arkansas",
        "California",
        "Colorado",
        "Connecticut",
        "Delaware",
        "District of Columbia",
        "Florida",
        "Georgia",
        "Hawaii",
        "Idaho",
        "Illinois",
        "Indiana",
        "Iowa",
        "Kansas",
        "Kentucky",
        "Louisiana",
        "Maine",
        "Maryland",
        "Massachusetts",
        "Michigan",
        "Minnesota",
        "Mississippi",
        "Missouri",
        "Montana",
        "Nebraska",
        "Nevada",
        "New Hampshire",
        "New Jersey",
        "New Mexico",
        "New York",
        "North Carolina",
        "North Dakota",
        "Ohio",
        "Oklahoma",
        "Oregon",
        "Pennsylvania",
        "Rhode Island",
        "South Carolina",
        "South Dakota",
        "Tennessee",
        "Texas",
        "Utah",
        "Vermont",
        "Virginia",
        "Washington",
        "West Virginia",
        "Wisconsin",
        "Wyoming",
        "Territories"
    ]
}

```


### Sample 2
Listing cities in Canda site, Ontario state, warning log level

```
$ craiglist_scrapper -C cities -co CA -st Ontario -LW
{
    "CA": {
        "Ontario": {
            "barrie": "https://barrie.craigslist.org/",
            "belleville": "https://belleville.craigslist.org/",
            "brantford-woodstock": "https://brantford.craigslist.org/",
            "chatham-kent": "https://chatham.craigslist.org/",
            "cornwall": "https://cornwall.craigslist.org/",
            "guelph": "https://guelph.craigslist.org/",
            "hamilton-burlington": "https://hamilton.craigslist.org/",
            "kingston": "https://kingston.craigslist.org/",
            "kitchener-waterloo-cambridge": "https://kitchener.craigslist.org/",
            "london": "https://londonon.craigslist.org/",
            "niagara region": "https://niagara.craigslist.org/",
            "ottawa-hull-gatineau": "https://ottawa.craigslist.org/",
            "owen sound": "https://owensound.craigslist.org/",
            "peterborough": "https://peterborough.craigslist.org/",
            "sarnia": "https://sarnia.craigslist.org/",
            "sault ste marie": "https://soo.craigslist.org/",
            "sudbury": "https://sudbury.craigslist.org/",
            "thunder bay": "https://thunderbay.craigslist.org/",
            "toronto": "https://toronto.craigslist.org/",
            "windsor": "https://windsor.craigslist.org/"
        }
    }
}
```