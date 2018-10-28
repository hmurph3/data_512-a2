# data_512-a2
Bias in English Wikipedia Assignment
see: https://wiki.communitydata.cc/Human_Centered_Data_Science_(Fall_2018)/Assignments#A2:_Bias_in_data

The goal of this analysis is to assess the bias in English Wikipedia politician articles beween countries. I analyzed the number of articles about politicians on English Wikipedia as well as the quality of the articles. The deliverables for this analysis is four tables.

1. The top 10 countries with the **highest** proportion of politician articles to the country's population.
2. The top 10 countries with the **lowest** proportion of politician articles to the country's population.
3. The top 10 countries with the **highetst** proportion of high quality articles.
4. The top 10 countries with the **lowest** proportion of high quality articles.

There are four files in this repository.
1. **page_data.csv** - This is a csv file of English Wikipedia articles about politicians by country. This data was pulled using the Wikimedia API, and the code and data for this are licensed under CC-BY-SA. Here is where the data and code for the data pull can be found. https://figshare.com/articles/Untitled_Item/5513449
2. **WPDS_2018_data.csv** - This is a csv file of the world population by country. It can be found here: https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0
3. **hcds-a2-bias.ipynb** - This is a notebook using Python 3 for my analysis. It includes all steps for my analysis and comments. An additional step in this anlaysis was getting the predicted artilce quality of each article using **ORES**. See below for more information on **ORES**. In this notebook, I show the headers of each table I used. The four required tables are shown in this notebook. 
4. **en-wikipedia_bias_data.csv** - This .cvs file is a table that consists of the merged **page_data.csv**, **WPDS_2018_data.csv**, and the **ORES** query data. I removed rows that had NaN values (values that don't have matching countries in the page data or the population data, or the ORES query and page data didn't have matching revision ids). 

I used **ORES** to gather the article quality prediction. Essentially, **ORES** is a machine learning algorithm that predicts the quality of articles. The article quality is rated in 6 catagories: **FA**, **GA**, **B**, **C**, **Start**, and **Stub**. (see: https://wiki.communitydata.cc/Human_Centered_Data_Science_(Fall_2018)/Assignments#Getting_article_quality_predictions). For this analysis, *high quality* articles have a rating of **FA** or **GA**. 

More information can be found here about **ORES**: https://www.mediawiki.org/wiki/ORES. 
**ORES** documentation can be found here: https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model
