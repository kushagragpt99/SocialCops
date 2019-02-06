# Challenge 1: Agriculture Commodities, Prices & Seasons

Aim: Your team is working on building a variety of insight packs to measure key trends in the Agriculture sector in India. You are presented with a data set around Agriculture and your aim is to understand trends in APMC (Agricultural produce market committee)/mandi price & quantity arrival data for different commodities in Maharashtra.

## Objective:
1. Test and filter outliers.
2. Understand price fluctuations accounting the seasonal effect
3. Detect seasonality type (multiplicative or additive) for each cluster of APMC and commodities
  3.1. De-seasonalise prices for each commodity and APMC according to the detected seasonality type
  3.2. Compare prices in APMC/Mandi with MSP(Minimum Support Price)- raw and deseasonalised
4. Flag set of APMC/mandis and commodities with highest price fluctuation across different commodities in each relevant season, and year.

You can use the [editor on GitHub](https://github.com/kushagragpt99/SocialCops/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

## Description of frequently used variables

**data1** - Pandas dataframe with values from _'CMO_MSP_Mandi.csv'_
**data2** - Pandas dataframe with values from _'Monthly_data_cmo.csv'_
**matrix2** - Numpy representation of data2
**matrix1** - Numpy representation of data1
**commodity_dict** - Dictionary with the commodities from data2 as keys and information about the commodities as values. Information is stored as numpy arrays in the same structure as given in data2.                   
**APMC_dict** - Dictionary with the APMCs from data2 as keys and information about the APMCs as values. Information is stored as numpy arrays in the same structure as given in data2.   
**com_price** - dict with keys as commodities and values as their minimum support price.
**exceeding_msp** - list with entries exceeding MSP given in CMO_MSP_Mandi.csv
**data3** - storing fluctuation (max_price - min_price) in a column of data3, sorted in descending order of fluctuation
**max_fluctuation_list** - list with entries corresponding to maximum fluctuation among a group whose membership is decided by APMC, commodity and year i.e 3 degrees of freedom for membership.

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/kushagragpt99/SocialCops/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
