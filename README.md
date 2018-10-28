# data_512-a2
Bias in English Wikipedia Assignment
see: https://wiki.communitydata.cc/Human_Centered_Data_Science_(Fall_2018)/Assignments#A2:_Bias_in_data

The goal of this analysis is to assess the bias in English Wikipedia politician articles by country. I analyzed the number of articles about politicians on English Wikipedia as well as the quality of the articles. The deliverables for this analysis are four tables (listed below) and a reflection on the analysis.

1. The top 10 countries with the **highest** proportion of politician articles to the country's population.
2. The top 10 countries with the **lowest** proportion of politician articles to the country's population.
3. The top 10 countries with the **highetst** proportion of high quality articles.
4. The top 10 countries with the **lowest** proportion of high quality articles.

There are four files in this repository.
1. **page_data.csv** - This is a csv file of English Wikipedia articles about politicians by country. This data was pulled using the Wikimedia API, and the code and data for this are licensed under CC-BY-SA. Here is where the data and code for the data pull can be found. https://figshare.com/articles/Untitled_Item/5513449
2. **WPDS_2018_data.csv** - This is a csv file of the world population by country. It can be found here: https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0
3. **hcds-a2-bias.ipynb** - This is a notebook using Python 3 for my analysis. It includes all steps for my analysis and comments. An additional step in this anlaysis was getting the predicted artilce quality of each article using **ORES**. See below for more information on **ORES**. In this notebook, I show the headers of each table I used. The four required tables write up reflecting on the anaysis are included in this notebook. 
4. **en-wikipedia_bias_data.csv** - This .cvs file is a table that consists of the merged **page_data.csv**, **WPDS_2018_data.csv**, and the **ORES** query data. I removed rows that had NaN values (values that don't have matching countries in the page data or the population data, or the ORES query and page data didn't have matching revision ids). 

I used **ORES** to gather the article quality prediction. Essentially, **ORES** is a machine learning algorithm that predicts the quality of articles. The article quality is rated in 6 catagories: **FA**, **GA**, **B**, **C**, **Start**, and **Stub**. (see: https://wiki.communitydata.cc/Human_Centered_Data_Science_(Fall_2018)/Assignments#Getting_article_quality_predictions). For this analysis, *high quality* articles have a rating of **FA** or **GA**. 

More information can be found here about **ORES**: https://www.mediawiki.org/wiki/ORES. 
**ORES** documentation can be found here: https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model

The high level steps I took for this anaysis are:
1. Read in the source files *page_data.csv* and *WPDS_2018_data.csv*.
2. Collect the article predictions from **ORES** using a for-loop. **ORES** only allows 50 to 100 rev_ids to be passed into the API before it runs into issues. More information on what I did is in the notebook.
3. Strip the **ORES** query of everything but the article and the prediciton. None of the other outputs are necessary for this analysis
4. Merge *page_data.csv* and *WPDS_2018_data.csv* using the country column.
5. Merge that table with the **ORES** data using the rev_id column.
6. Remove the rows that has missing data. 
7. Calcualte the number of articles per country, the proportion of articles to the population by country, and the proportion of high quality articles by country.
8. Create the following tables:
  * The top 10 countries with the **highest** proportion of politician articles to the country's population.
  * The top 10 countries with the **lowest** proportion of politician articles to the country's population.
  * The top 10 countries with the **highetst** proportion of high quality articles.
  * The top 10 countries with the **lowest** proportion of high quality articles.
9. Refelct on my anaysis and any potiential biasis in the data.


