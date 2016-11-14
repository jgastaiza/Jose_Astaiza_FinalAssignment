
# Analysis of the relation between demand deposits and risks in the American banking sector

[José Gabriel Astaiza]

Noviembre-2016

<img src="/figures/intro.jpg">

---

## Description and motivation

USBankLocations.com makes public a compilation of statistics about Tier 1 risk-based capital ratios for all US banks, as well as a compilation of demand deposits statistics for each bank. These statistics are originally collected by various government agencies and USBankLocations.com obtain the data from these government agencies under the Freedom of Information Act. 

For this project I scraped those statistics, which include 6058 banks, and analyzed them using Python.  

Some questions/issues that motivated the project are:

- In the process of issuing deposits and granting loans, financial institutions transform assets characterized by short maturities, small amounts and low risks (deposits) into assets of longer maturities, greater amounts and higher risks (loans).
- Since an important fraction of the illiquid loans of banks are financed through the demand deposits of the uninformed public, then there is always the possibility that depositors excessively withdraw their deposits (i.e., the possibility of a bank run) and the bank face both a liquidity shortage and a higher probability of failure.
- Although bank runs could have a speculative cause, they could also have a fundamental cause, i.e., they could be caused by the bank asset quality.
- The tier 1 capital ratio is the comparison between a banking firm's core equity capital and its total risk-weighted assets. A firm's core equity capital is known as its tier 1 capital and is the measure of a bank's financial strength based on the sum of its equity capital and disclosed reserves, and sometimes non-redeemable, non-cumulative preferred stock. A firm's risk-weighted assets include all assets that the firm holds that are systematically weighted for credit risk.
- What do basic descriptive statistics of the data tell us about the risks of US banks?
- What do basic descriptive statistics of the data tell us about the deposits of US banks?
- Is there a clear relation between the risks and the level of deposits in the United States?

## Methods used

1. Scraping
    - For each bank, the data of demand deposits and the tier 1 capital ratios are available online in the two following websites.
        - Demand deposits:  http://www.usbanklocations.com/bank-rank/demand-deposits---totaldeposits--td-ddt.html
        - Tier 1 capital ratio: www.usbanklocations.com/bank-rank/tier-1-risk-based-capital-ratio---performanceratios--pcr-rbc1rwaj.html
    - To scrape the two websites I used the 'BeautifulSoup' library.
    - The whole Python code is available [here](scraper_batches_1-2.ipynb) and [here for batch 3](scraper_batch_3.ipynb).
<br><br>
2. Extracting the data from 'BeatifulSoup' objects:
    - Both to scrape the raw text and to extract the data from it, I wrote helper functions to: get htmls; get urls to speeches; get year, month, and day information from the text; get the title of the speech; remove html tags; and get the location of the speech; get all the elements of a speech in a structured object.
    - Helper functions are available [here](scraper_helper.ipynb).
<br><br>
3. Managing, storing, and further cleaning the data:
    - I used 'Pandas' to create a data frame for each batch of speeches, and exported each to a 'pickle' file for storage.
    - I consolidated the three data frames into one and furthered cleaned the data using 'Pandas' methods, 'string' methods, regular expressions, etc.
    - Using 'string' and 'nltk' libraries I stripped speeches from punctuation, converted to lowercase, tokenized text, dropped stopwords (in Spanish), etc.
    - Code is available in [here](consolidate_clean.ipynb).


## Findings

All code for analysis available [here](speeches_analysis.ipynb).

- Number of unique speeches: 2,651.
- Number of days in office: 2,041.
- Number of days in which at least one speech was given: 1,442
- Maximum number of speeches in a day: 6 (twice)

Here some visualizations of key findings:

<img src="images/hist_daily.png">

<img src="images/line_month.png">

The vertical blue line indicates the month in which the Law of Electoral Guarantees was enacted. This law limited the President's  interventions, as he announced running for reelection.

<img src="images/paz_terroristas_month.png">

The vertical blue line indicates the official start of peace talks with FARC.

<img src="images/topics_total.png">

<img src="images/dispersion1.png">

<img src="images/dispersion2.png">

---
