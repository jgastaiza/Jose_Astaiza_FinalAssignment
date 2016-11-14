
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
    - The whole Python code is available [here](FinalAssignment_Jose_Astaiza.ipynb)
<br><br>
2. Extracting the data from 'BeatifulSoup' objects:
    - Both to scrape the raw text and to extract the data from it, I wrote codes to get urls to deposits and risks; get the names of banks; remove unnecesary symbols; transform the string digits into floats; get the names sorted alphabetically mantaining for each bank the corresponding data.
<br><br>
3. Managing, storing, and further cleaning the data:
    - I created lists with the data of banks names, demand deposits and risks and furthered cleaned the data using 'Pandas' methods, regular expressions, etc.
    - I used 'Pandas' to create a data frame with the information of banks, demand deposits, log demand deposits and risks.
    - The complete database or data frame in csv format is available [here](base_completa)
    - There was an importan outlier that was identified and droped using the .drop and .index methods.  

## Findings

All code for analysis is available [here](FinalAssignment_Jose_Astaiza.ipynb).
 
- Two samples were analysed: the complete sample and the sample without the outlier. This was a strange value correspondig to risk. The  risk outlier is in the position 2768 of the complete data frame and is asociated to HSBC,Delaware (36197%,500.000$). It is important to notice that the second highest risk is just 868.6%.

- Las estadísticas descriptivas de la base completa son:
<pre>
             Riesgo      Depositos  LogDepositos
count   6058.000000    6058.000000   6058.000000
mean      25.402773     260.465357     16.823795
std      465.535237    4658.603264      2.944915
min        1.594700       0.000000     -4.605170
25%       12.478850      12.457000     16.337793
50%       15.109700      25.842000     17.067512
75%       19.728750      55.820250     17.837647
max    36197.297300  258094.000000     26.276590 
</pre>
- Las estadísticas descriptivas de la base sin outlier son:
<pre>
            Riesgo      Depositos  LogDepositos
count  6057.000000    6057.000000   6057.000000
mean     19.430857     217.897496     16.822234
std      25.922823    3275.228433      2.942652
min       1.594700       0.000000     -4.605170
25%      12.478500      12.457000     16.337793
50%      15.109400      25.839000     17.067396
75%      19.724400      55.815000     17.837553
max     868.623800  144521.000000     25.696691
</pre>


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
