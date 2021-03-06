# orders-fee-distribution
Exploratory statistics and graphs on fee amount for more than 9,000 orders

The analysis, done on Google Sheets, can be accessed [here](https://docs.google.com/spreadsheets/d/1dR5GL0U3g_2uSffhfSIGWqDqYnpy4r-DnCD0MrC30hQ/edit?usp=sharing).

The Fee feature was adjusted for inflation and FeeInf was created. 9,393 orders included a fee.

The initial frequency distribution was highly positively skewed. An outlier analysis using inter-quartile range identified 71 outliers (comprising less than 1% of orders with fees ), ranging from $591 to $5,775.

The high boundary was calculated using one-and-a-half times the inter-quartile range, as in the following, where column B contained FeeInf:

```
QUARTILE($B$2:$B,3) +
(
  QUARTILE($B$2:$B,3) -
  QUARTILE($B$2:$B,1)
) *
1.5
```

After filtering out the outliers, the distribution became more normal, decreasing skew and kurtosis. However, the distribution contained major peaks at $80, $180, and $330, binned at steps of 10.

![FeeInf distribution](https://raw.githubusercontent.com/oberljn/orders-fee-distribution/master/FeeInf%20distribution.png)

It was hypothesized that the type of the order, mostly characterized by the report form, ie the variable labeled Form, would reveal more about the three peaks.

The top four most frequent forms were selected, comprising 88% of the orders with fees. The FeeInf by Form values were binned and graphed in a stacked bar chart.

![FeeInf by Form](https://raw.githubusercontent.com/oberljn/orders-fee-distribution/master/FeeInf%20distribution%20by%20top%20four%20most%20frequent%20Form%20types.png)

The first peak is primarily comprised of NULL type forms, ie the observation had no form attribute. The second peak was of tightly distributed ELOC's. And the third peak was of URAR's. 2055 Form type was more widely spread, peaking with ELOC's and at the lower end of the URAR distribution.

