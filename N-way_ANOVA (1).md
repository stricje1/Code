# N-way ANOVA

If you are looking for how to run code jump to the next section or if you would like some theory/refresher then start with this section.

ANOVA stands for analysis of variance and is an omnibus parametric test. Meaning it tests for an overall difference between the variables in the model, i.e. at least one of the groups is statistically significantly different than the others. However, if the ANOVA is significant one cannot tell which groups differ. In order to tell which groups are different planned or post-hoc comparisons need to be made. As with all parametric tests, there are certain assumptions that need to be met in order for the test results to be considerede reliable.

Recall that when working from the ANOVA framework, independent variables are sometimes referred to as factors and the number of groups within each variable are called levels, i.e. one variable with 3 categories could be reffered to as a factor with 3 levels. Since this is an N-way ANOVA there will be at least 2 variables - they don't both have to be categorical. Some variables can be categorical and others continuous, if this is the case, the analysis is called an analysis of covariance (ANCOVA). The approach with an ANCOVA is no different than an N-factor ANOVA, but nonetheless, ANCOVA has it's own demonstration.

Ideally one should be comfortable with conducting and interpreting an one-way, a.k.a one-factor, ANOVA before conducting the N-way, a.k.a N-factor, ANOVA. When analyzing a model where there are more than 2 factors the analysis can get complex quickly - a 3-factor ANOVA is not that much more complex, but anything over 3 is definitely complex. This will be seen shortly.

Before one can start analyzing the factors themselves, the overall model needs to be significant at the pre-determined significance level, a.k.a alpha level (
), which is commonly set to 0.05. The statistic being evaluated is the F-statistic.

## Parametric test assumptions
* Population distributions are normal
* Samples have equal variances
* Independence

## Hypothesis

$$H_0:\bar{x}_1=\bar{x}_2=\bar{x}_3=...=\bar{x}_k$$
$$H_A: \text{At least one of the groups means differ}$$

The test statistic is the F-statistic and compares the mean square between samples $(MS_{B})$ to the mean square within sample $(MS_{W})$. This $F$-statistic can be calculated using the following formula: 

$$F=\frac{MS_B}{MS_W}$$

Where,
 
$$MS_B=\frac{\text{Sum of squares between samples}(SS_B)}{k-1}$$
 
$$MS_W=\frac{\text{Sum of squares within sample}(SS_W)}{n_{T}-k}$$

$k$ is the number of groups
    
$n_T$ is the total number of observations

and where,
Sum of square between sample 
$$SS_B=\sum_{k}{n_{k}(\bar{x_k}-\bar{x})^2}$$

Sum of square within sample
$$SS_W=\sum_{i,k}{({x_{i,k}}-\bar{x_k})^2}$$

or can be calculated as $\sum_{k}{(n_{k}-1)s^{2}_{k}}$

One rejects the the null hypothesis, $H_0$, if the computed $F$-static is greater than the critical $F$-statistic. The critical $F$-statistic is determined by the degrees of freedom and alpha, $\alpha$, value.

$$\text{Reject } H_0 \text{ if calculated } F-statistic > \text{critical } F-statistic$$
 
Before the decision is made to accept or reject the null hypothesis the assumptions need to be checked. See this page on how to check the parametric assumptions in detail - how to check the assumptions for this example will be demonstrated near the end.le will be demonstrated near the end.le will be demonstrated near the end.ple will be demonstrated near the end.ail - how to check the assumptions for this example will be demonstrated near the end.ll be demonstrated near the end.

Data Table: DV = Systolic

| Variable | Groups | Sample Size | Sample Means |Sample Variance|
|:---------|:------:|:-----------:|:------------:|:-------------:|
|              | $1(k_1)$ | $15(n_1)$ | $26.07(\bar{x_1})$ | $136.35(s^2_1)$|
| Drug$(IV_1)$ | $2(k_2)$ | $15(n_2)$ | $25.53(\bar{x_2})$ | $134.98(s^2_2)$|
|              | $3(k_3)$ | $12(n_3)$ |  $8.75(\bar{x_3})$ | $100.39(s^2_3)$|
|              | $4(k_4)$ | $16(n_4)$ | $13.50(\bar{x_4})$ |  $86.93(s^2_4)$|
|              | $1(k_1)$ | $19(n_1)$ | $22.79(\bar{x_1})$ | $173.18(s^2_1)$|
| Drug$(IV_2)$ | $2(k_2)$ | $19(n_2)$ | $18.21(\bar{x_2})$ | $183.73(s^2_2)$|
|              | $3(k_3)$ | $20(n_3)$ | $15.80(\bar{x_3})$ | $127.75(s^2_3)$|
| Drug$(IV_3)$ |          | $58(n_T)$ | $18.88(\bar{x})$  | $1163.86(s^2)$|ar{x})$ |ar{x_1})$ |

Cross Tabulation Data Table: DV = Systolic

| $Drug(IV_1)$ | $Disease(IV_2)$ | Sample Size | Sample Means | Sample Variance|
|:-------------|:------------:|:-----------:|:------------:|:-----------:|
|              | $1(k_{2,1})$ | 6 | 29.33 | 169.46|
| $1(k_{1,1})$ | $2(k_{2,2})$ | 4 | 28.25 | 34.25|
|              | $3(k_{2,3})$ | 5 | 20.40 | 178.80|
|              | $1(k_{2,1})$ | 5 | 28.00 | 120.50|
| $2(k_{1,2})$ | $2(k_{2,2})$ | 4 | 33.50 | 4.33|
|              | $3(k_{2,3})$ | 6 | 18.17 | 156.97|
|              | $1(k_{2,1})$ | 3 | 16.33 | 201.33|
| $3(k_{1,3})$ | $2(k_{2,2})$ | 5 |  4.40 | 47.80|
|              | $3(k_{2,3})$ | 4 |  8.50 | 81.00|
|              | $1(k_{2,1})$ | 5 | 13.60 | 111.30|
| $4(k_{1,4})$ | $2(k_{2,2})$ | 6 | 12.83 | 106.96|
|              | $3(k_{2,3})$ | 5 | 14.20 | 79.70|| 5 | 14.20 || 5 | 14.20 || 5 | 14.20 || 5 | 14.20 || 5 | 14.20 |

Let's make sense of all these mathmatical terms. In order to do that, let's start with a generic ANOVA table excluding the factor information. The reason why the factors are being excluded for now is because there are various ways to calculate the sum of squares (SS) for the factors each with their own theoretical reasoning. The most common type is type III which is returned by default in Stata, SAS, and SPSS.

| Source of Variation | Sum of Squares (SS) | Degrees of Freedom (df) | Mean Squares {MS} |  F |
| :------------------ | :-----------: | :--------------------: | :----------------: | :------: |
| Between Sampes  | $SS_B$ | $k-1$ | $MS_B=\frac{SS_B}{k-1}$ | $F=\frac{MS_B}{MS_W}$|
| Error (or Residual) | $SS_W$ | $n_{T}-k$ | $MS_W=\frac{SS_W}{n_{T}-k}$ | |
| Total | $SS_T=SS_B+SS_W$ | $n_{T}-1$ | $T$ |   |

Now using the formulas and data from above, the ANOVA table can be filled in - the table below reports type III sum of squares. The sum of square calculations for the individual factors have been omitted since it is a bit out of scope for the topic at hand, an easy to read primer on the types of sum of squares can be found here. Ignore the code part since it's written for R, but the theory behind the different types are explained well.

Completed ANOVA Table

| Source of Variation | Sum of Squares (SS) | Degrees of Freedom (df) | Mean Squares {MS} |  F |
| :------------------ | :-----------: | :--------------------: | :----------------: | :------: |
| Between Samples  | 4259.34 | 11 | 387.21 | 3.51|
| Drug | 2997.47 | 3 | 999.16 | 9.05 |
| Disease | 415.87 | 2 | 207.94 | 1.88 |
| Drug Disease  | 707.27 | 6 | 117.88 | 1.07|
| Within Samples | 5080.82 | 46 | 110.45 |  |
| Total | 9340.16 | 57 | 163.86 |  |86 |  |86 |  |86 |  |

In order to tell if the calculated F-statistic is statistically significant, one would look up the F-statistic based on the degress of freedom and alpha level - using statistical software this doesn't need to be done since it'll be provided.

Fear not if math is not your strong suit. All this is being calucated when using the methods of a statistical software or programming language. It's good to know what is going on behind the scences. References for this section are provided at the end of the page.

## N-way ANOVA Approach
When conducting an ANOVA with multiple factors, like in the current demonstration, all factors should be tested for an interaction before looking at their individual main effects. If the interaction between the variables are non-significant, then remove a variable from the interaction and conduct the analysis again. First a 2-factor ANOVA example will be discussed then the discussion will be expanded to discuss a 3-factor ANOVA which will exemplify how complex ANOVAs can get when using multiple factors.

## 2-Factor ANOVA 
To discuss a 2-factor ANOVA a hypothetcal example will be provided. A researcher is testing if there is a difference in effect between drug types and disease types on systolic blood pressure. Here the systolic blood pressure is the dependent variable and drug type and disease type are the independent variables. The model will look like `

`systolic ~ drug + disease + drug:disease`

where drug:disease notes the test for an interaction between the two. If the interaction term is significant it indicates that the effect of the type of drug on systolic blood pressure is dependent on the type of disease. To determine which combination of drug and disease type are significantly different than the others, one has to conduct planned comparisons or post-hoc tests.

If the interaction is non-significant, then it is removed from the model and the model is re-run. The reduced model will now be

`systolic ~ drug + disease`

where one is now testing for the main effects of the independent variables themselves.themselves.

## 3-Factor ANOVA
To discuss a 3-factor ANOVA a hypothetical example will be provided. In this example a farmer wants to test the effects of different combinations of fertilizer, the amount of water, and amount of sunlight on crop yield. The farmer decided to bin the amount of water and sunlight into categories and simply label them as low, medium, and high failing to tell everyone else how much each category represents. Thus, this study looks like the following:


|Variable | Categories|
|:-------:|:---------:|
|            |  A  |
| Fertilizer |  B  |
|            | Low |
| Water      |Medium|
|            |High|
|            |Low|
| Sunlight   |Medium|
|            |High|
|Crop Yield|Continuous measure|

The first analysis will look at the interaction of the 3 factors

`crop_yield ~ fertilizer + water + sunlight + fertilizer:water:sunlight`

Crop Yield ANOVA Table

| Source of Variation | Sum of Squares (SS) | Degrees of Freedom (df) | Mean Squares {MS} |  F |
| :------------------ | :-----------: | :--------------------: | :----------------: | :------: |
| Between Samples  | ## | ## | ## | ##***|
| Fertilizer | ## | ## | ## | ## |
| Water | ## | ## | ## | ## |
| Sunlight  | ## | ## | ## | ## |
| Fertilizer:Water:Sunlight | ## | ## | ## | ##** |
| Within Samples | ## | # | # |  |
| Total | ## | # | # |  |# | # |  |# | # |  |

*The important rows are "between samples" and the interaction term row marked with *** and ** respectively. If the between samples F-statistic is significant it means the overal model explains a statistically significant amount of variance which then permits one to look at the interaction term. Coming from the ANOVA framework, not all packages report the model's F-statistic and only report the interaction of main effect F-statistic and associated p-value.*

If the interaction term is significant the next step would be to check the model's assumptions and proceed from there. However, if the interaction term is non-signifcant then the next step would be to break the interaction term down into multiple 2-way interactions. The next model ran would look like:

`crop_yield ~ fertilizer + water + sunlight + fertilizer:water + fertilizer:sunlight + water:sunlight`

The focus is now on the multiple interaction terms.

Crop Yield ANOVA Table

| Source of Variation | Sum of Squares (SS) | Degrees of Freedom (df) | Mean Squares {MS} |  F |
| :------------------ | :-----------: | :--------------------: | :----------------: | :------: |
| Between Samples  | ## | ## | ## | ##***|
| Fertilizer | ## | ## | ## | ## |
| Water | ## | ## | ## | ## |
| Sunlight  | ## | ## | ## | ## |
| Fertilizer:Water| ## | ## | ## | ##** |
| Fertilizer:Sunlight | ## | ## | ## | ##** |
| Fertilizer:Water:Sunlight | ## | ## | ## | ##** |
| Within Samples | ## | ## | ## |  |
| Total | ## | ## | ## |  |

*The important rows are "between samples" and the interaction terms rows marked with *** and ** respectively. If the between samples F-statistic is significant it means the overal model explains a statistically significant amount of variance which then permits one to look at the interaction term. Coming from the ANOVA framework, not all packages report the model's F-statistic and only report the interaction of main effect F-statistic and associated p-value.*

From here, if all the iteraction terms are statistically significant then one checks the assumptions and proceeds from there. However, if any of the interaction terms are non-significant then they need to be removed and the model needs to be re-run.

This process is completed until all non-significant interaction terms are removed. In the final model, if a factor is not in an interaction term then one can interprete the main effects of that factor, whereas if a factor is in an interaction term then that factor needs to be interpreted as such. A final crop yield table will be shown next and the interpretation will follow.

Final Crop Yield ANOVA Table

| Source of Variation | Sum of Squares (SS) | Degrees of Freedom (df) | Mean Squares {MS} |  F |
| :------------------ | :-----------: | :--------------------: | :----------------: | :------: |
| Between Samples  | ## | ## | ## | ##*|
| Fertilizer | ## | ## | ## | ## |
| Water | ## | ## | ## | ## |
| Sunlight  | ## | ## | ## | ##* |
| Fertilizer:Water| ## | ## | ## | ##* |
| Within Samples | ## | ## | ## |  |
| Total | ## | ## | ## |  |lpha$=$0.05$\alpha=0.05$\alpha=0.05$ | ## |  |

* Indicates statistical significance at $\alpha=0.05$

In the Final Crop Yield ANOVA Table the only remaining significant interaction is between fertilizer and water. This would indicate the effect of fertilizer and water on the crop yield is synergistic and that different combinations of the levels produce different crop yields. Whereas the effect of sunlight on crop yield is statistically significant but is not synergistic with the other factors.

## 3-way ANOVA with Python

Don't forget to check the assumptions before interpreting the results! First to load the libraries and data needed. Below, Pandas, Researchpy and the data set will be loaded. Specific libraries for each demonstrated method below will contain any further libraries that are need is using that demonstration.


```python
#pip install researchpy
```


```python
import pandas as pd
import researchpy as rp
import numpy as np
from scipy import stats
import statsmodels.api as sm
from statsmodels.base.model import *
```

Now to load the data set and take a high level look at the variables. This data is from Stata and is used in their ANOVA documentation. The data is similar to the above discussion on the 3-factor ANOVA, time to dive in. A study was designed to determine the optimal operating conditions to maximize yield. The study assessed temperature settings, chemical supply companies, and two mixing methods.


```python
manuf = "C:\\Users\\jeff\\Documents\\Data\\manuf.csv"
```


```python
manufac = pd.read_csv(manuf)
```


```python
manufac.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 36 entries, 0 to 35
    Data columns (total 4 columns):
     #   Column       Non-Null Count  Dtype
    ---  ------       --------------  -----
     0   temperature  36 non-null     int64
     1   chemical     36 non-null     int64
     2   method       36 non-null     int64
     3   yield        36 non-null     int64
    dtypes: int64(4)
    memory usage: 1.3 KB
    


```python
manufac.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>temperature</th>
      <th>chemical</th>
      <th>method</th>
      <th>yield</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>00:00:00</th>
      <th>00:00:00 Officially Xerox, but 0:0:0:0:0:0 is more common</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>00:00:01</td>
      <td>Xerox Xerox Corporation</td>
    </tr>
    <tr>
      <th>1</th>
      <td>00:00:02</td>
      <td>Xerox Xerox Corporation</td>
    </tr>
    <tr>
      <th>2</th>
      <td>00:00:03</td>
      <td>Xerox Xerox Corporation</td>
    </tr>
    <tr>
      <th>3</th>
      <td>00:00:04</td>
      <td>Xerox Xerox Corporation</td>
    </tr>
    <tr>
      <th>4</th>
      <td>00:00:05</td>
      <td>Xerox Xerox Corporation</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>48816</th>
      <td>FC:FB:FB</td>
      <td>Cisco Cisco Systems, Inc</td>
    </tr>
    <tr>
      <th>48817</th>
      <td>FC:FC:48</td>
      <td>Apple Apple, Inc.</td>
    </tr>
    <tr>
      <th>48818</th>
      <td>FC:FE:77</td>
      <td>HitachiR Hitachi Reftechno, Inc.</td>
    </tr>
    <tr>
      <th>48819</th>
      <td>FC:FE:C2</td>
      <td>Invensys Invensys Controls UK Limited</td>
    </tr>
    <tr>
      <th>48820</th>
      <td>FC:FF:AA</td>
      <td>IEEERegi IEEE Registration Authority</td>
    </tr>
  </tbody>
</table>
<p>48821 rows × 2 columns</p>
</div>




```python
manuf="https://raw.githubusercontent.com/n1snt/MacToManufacturer/main/manuf.csv"
```


```python
manufac=pd.read_csv(manuf)

manufac.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 48821 entries, 0 to 48820
    Data columns (total 2 columns):
     #   Column                                                     Non-Null Count  Dtype 
    ---  ------                                                     --------------  ----- 
     0   00:00:00                                                   48821 non-null  object
     1   00:00:00 Officially Xerox, but 0:0:0:0:0:0 is more common  48821 non-null  object
    dtypes: object(2)
    memory usage: 763.0+ KB
    


```python
rp.summary_cat(manufac[["temperature", "chemical", "method"]])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Variable</th>
      <th>Outcome</th>
      <th>Count</th>
      <th>Percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>temperature</td>
      <td>1</td>
      <td>12</td>
      <td>33.33</td>
    </tr>
    <tr>
      <th>1</th>
      <td></td>
      <td>2</td>
      <td>12</td>
      <td>33.33</td>
    </tr>
    <tr>
      <th>2</th>
      <td></td>
      <td>3</td>
      <td>12</td>
      <td>33.33</td>
    </tr>
    <tr>
      <th>3</th>
      <td>chemical</td>
      <td>1</td>
      <td>18</td>
      <td>50.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td></td>
      <td>2</td>
      <td>18</td>
      <td>50.00</td>
    </tr>
    <tr>
      <th>5</th>
      <td>method</td>
      <td>1</td>
      <td>18</td>
      <td>50.00</td>
    </tr>
    <tr>
      <th>6</th>
      <td></td>
      <td>2</td>
      <td>18</td>
      <td>50.00</td>
    </tr>
  </tbody>
</table>
</div>



Load data from the directory:

## 3-Factor ANOVA using StatsModels
The official documentation for conducting an ANOVA with StatsModels can be found here. Type 3 sum of squares is what is typically desired and is the default output for SPSS, SAS, and Stata. To get type 3 sum of squares, a minor extra step needs to be taken when using StatsModels - this step is specifying ", Sum" in the formula for the factors. Without specifying this, only Type I and Type II sum of squares will be calculated correctly.


```python
from statsmodels.formula.api import ols

manufac["Yield"] = manufac["yield"]

model = ols("Yield ~ C(temperature, Sum) + C(chemical, Sum) + C(method, Sum) + C(temperature, Sum)*C(chemical, Sum)*C(method, Sum)", data=manufac).fit()

aov_table = sm.stats.anova_lm(model, typ=3)
aov_table
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sum_sq</th>
      <th>df</th>
      <th>F</th>
      <th>PR(&gt;F)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Intercept</th>
      <td>2070.25</td>
      <td>1.0</td>
      <td>299.313253</td>
      <td>4.675019e-15</td>
    </tr>
    <tr>
      <th>C(temperature, Sum)</th>
      <td>30.50</td>
      <td>2.0</td>
      <td>2.204819</td>
      <td>1.321133e-01</td>
    </tr>
    <tr>
      <th>C(chemical, Sum)</th>
      <td>12.25</td>
      <td>1.0</td>
      <td>1.771084</td>
      <td>1.957540e-01</td>
    </tr>
    <tr>
      <th>C(method, Sum)</th>
      <td>42.25</td>
      <td>1.0</td>
      <td>6.108434</td>
      <td>2.093730e-02</td>
    </tr>
    <tr>
      <th>C(temperature, Sum):C(chemical, Sum)</th>
      <td>24.50</td>
      <td>2.0</td>
      <td>1.771084</td>
      <td>1.916714e-01</td>
    </tr>
    <tr>
      <th>C(temperature, Sum):C(method, Sum)</th>
      <td>87.50</td>
      <td>2.0</td>
      <td>6.325301</td>
      <td>6.216723e-03</td>
    </tr>
    <tr>
      <th>C(chemical, Sum):C(method, Sum)</th>
      <td>0.25</td>
      <td>1.0</td>
      <td>0.036145</td>
      <td>8.508161e-01</td>
    </tr>
    <tr>
      <th>C(temperature, Sum):C(chemical, Sum):C(method, Sum)</th>
      <td>3.50</td>
      <td>2.0</td>
      <td>0.253012</td>
      <td>7.785036e-01</td>
    </tr>
    <tr>
      <th>Residual</th>
      <td>166.00</td>
      <td>24.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



The interaction between temperature, chemical type, and method is statistically non-significant. This indicates that different level combinations of the factors do not produce a significant difference in the yield. Thus this term should be removed from the ANOVA model and re-ran looking at the 2-factor interactions.


```python
model = ols("Yield ~ C(temperature, Sum) + C(chemical, Sum) + C(method, Sum) + C(temperature, Sum):C(chemical, Sum) + C(temperature, Sum):C(method, Sum) + C(chemical, Sum):C(method, Sum)", data=manufac).fit()

aov_table = sm.stats.anova_lm(model, typ=3)
aov_table
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sum_sq</th>
      <th>df</th>
      <th>F</th>
      <th>PR(&gt;F)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Intercept</th>
      <td>2070.25</td>
      <td>1.0</td>
      <td>317.560472</td>
      <td>4.292571e-16</td>
    </tr>
    <tr>
      <th>C(temperature, Sum)</th>
      <td>30.50</td>
      <td>2.0</td>
      <td>2.339233</td>
      <td>1.163633e-01</td>
    </tr>
    <tr>
      <th>C(chemical, Sum)</th>
      <td>12.25</td>
      <td>1.0</td>
      <td>1.879056</td>
      <td>1.821599e-01</td>
    </tr>
    <tr>
      <th>C(method, Sum)</th>
      <td>42.25</td>
      <td>1.0</td>
      <td>6.480826</td>
      <td>1.717637e-02</td>
    </tr>
    <tr>
      <th>C(temperature, Sum):C(chemical, Sum)</th>
      <td>24.50</td>
      <td>2.0</td>
      <td>1.879056</td>
      <td>1.728955e-01</td>
    </tr>
    <tr>
      <th>C(temperature, Sum):C(method, Sum)</th>
      <td>87.50</td>
      <td>2.0</td>
      <td>6.710914</td>
      <td>4.467613e-03</td>
    </tr>
    <tr>
      <th>C(chemical, Sum):C(method, Sum)</th>
      <td>0.25</td>
      <td>1.0</td>
      <td>0.038348</td>
      <td>8.462683e-01</td>
    </tr>
    <tr>
      <th>Residual</th>
      <td>169.50</td>
      <td>26.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



The only 2-factor interaction that is statistically significant is between temperature and method, the other 2-factor interactions should be removed and the model needs to be re-ran.


```python
model = ols("Yield ~ C(temperature, Sum) + C(chemical, Sum) + C(method, Sum) + C(temperature, Sum):C(method, Sum)", data=manufac).fit()

aov_table = sm.stats.anova_lm(model, typ=3)
aov_table
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sum_sq</th>
      <th>df</th>
      <th>F</th>
      <th>PR(&gt;F)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Intercept</th>
      <td>2070.25</td>
      <td>1.0</td>
      <td>309.072072</td>
      <td>5.239664e-17</td>
    </tr>
    <tr>
      <th>C(temperature, Sum)</th>
      <td>30.50</td>
      <td>2.0</td>
      <td>2.276705</td>
      <td>1.206672e-01</td>
    </tr>
    <tr>
      <th>C(chemical, Sum)</th>
      <td>12.25</td>
      <td>1.0</td>
      <td>1.828829</td>
      <td>1.867181e-01</td>
    </tr>
    <tr>
      <th>C(method, Sum)</th>
      <td>42.25</td>
      <td>1.0</td>
      <td>6.307593</td>
      <td>1.784464e-02</td>
    </tr>
    <tr>
      <th>C(temperature, Sum):C(method, Sum)</th>
      <td>87.50</td>
      <td>2.0</td>
      <td>6.531532</td>
      <td>4.552060e-03</td>
    </tr>
    <tr>
      <th>Residual</th>
      <td>194.25</td>
      <td>29.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



The sum of squares that each factor accounted for did not change while removing non-significant factors from the model due to the nature of Type III sum of squares. The information that did change are the F-statistics and their respective p-values, as well as the residual sum of squares and the residual degrees of freedom.

## Interpretation
A study was designed to determine the optimal operating conditions to maximize yield. The study assessed temperature settings, chemical supply companies, and two mixing methods. The overall interaction between the three factors was statistically non-significant, F(2, 24.0)= 0.2530, p-value= 0.7786. After looking at the reduced model which included all possible 2-factor interactions, the only significant interaction was between temperature and method. The non-signifance interactions were removed and the final model showed that temperature and method have a statistically significant interaction effect on yield, F(2, 29)=6.5315, p-value= 0.0045.

**Note**: It's important to include the other model's in documentation to show full model results of all model's tested.

## Assumption Check and Post-hoc Testing
To see how to check the assumptions using an ANOVA model please refer to the assumption check section of the one-way ANOVA. For a more in-depth look at the assumptions and some potential remedies, please check out this page.

To see how to conduct post-hoc testing, please refer to the post-hoc testing section of the one-way ANOVA page. Before you leave and conduct post-hoc testing it should be noted that an easy way to test for group difference of the interaction term using StatsModels is to create a column in the data frame which represents the possible group combinations of the significant interaction term and use this instead of trying to use a groupby object. A quick demonstration is below, but still refer to the post-hoc testing page as mentioned for a more in-depth demonstration.


```python
import statsmodels.stats.multicomp as mc

interaction_groups = "Temp_" + manufac.temperature.astype(str) + " & " + "Method_" + manufac.method.astype(str)

comp = mc.MultiComparison(manufac["Yield"], interaction_groups)
post_hoc_res = comp.tukeyhsd()
post_hoc_res.summary()
```




<table class="simpletable">
<caption>Multiple Comparison of Means - Tukey HSD, FWER=0.05</caption>
<tr>
       <th>group1</th>            <th>group2</th>       <th>meandiff</th>  <th>p-adj</th>  <th>lower</th>   <th>upper</th>  <th>reject</th>
</tr>
<tr>
  <td>Temp_1 & Method_1</td> <td>Temp_1 & Method_2</td>   <td>-2.0</td>   <td>0.7717</td> <td>-6.6072</td> <td>2.6072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_1 & Method_1</td> <td>Temp_2 & Method_1</td>   <td>-1.5</td>   <td>0.9175</td> <td>-6.1072</td> <td>3.1072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_1 & Method_1</td> <td>Temp_2 & Method_2</td>    <td>1.5</td>   <td>0.9175</td> <td>-3.1072</td> <td>6.1072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_1 & Method_1</td> <td>Temp_3 & Method_1</td>   <td>-1.5</td>   <td>0.9175</td> <td>-6.1072</td> <td>3.1072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_1 & Method_1</td> <td>Temp_3 & Method_2</td>    <td>4.0</td>   <td>0.1184</td> <td>-0.6072</td> <td>8.6072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_1 & Method_2</td> <td>Temp_2 & Method_1</td>    <td>0.5</td>   <td>0.9994</td> <td>-4.1072</td> <td>5.1072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_1 & Method_2</td> <td>Temp_2 & Method_2</td>    <td>3.5</td>   <td>0.2213</td> <td>-1.1072</td> <td>8.1072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_1 & Method_2</td> <td>Temp_3 & Method_1</td>    <td>0.5</td>   <td>0.9994</td> <td>-4.1072</td> <td>5.1072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_1 & Method_2</td> <td>Temp_3 & Method_2</td>    <td>6.0</td>   <td>0.0052</td> <td>1.3928</td>  <td>10.6072</td>  <td>True</td> 
</tr>
<tr>
  <td>Temp_2 & Method_1</td> <td>Temp_2 & Method_2</td>    <td>3.0</td>   <td>0.3764</td> <td>-1.6072</td> <td>7.6072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_2 & Method_1</td> <td>Temp_3 & Method_1</td>    <td>0.0</td>     <td>1.0</td>  <td>-4.6072</td> <td>4.6072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_2 & Method_1</td> <td>Temp_3 & Method_2</td>    <td>5.5</td>   <td>0.0121</td> <td>0.8928</td>  <td>10.1072</td>  <td>True</td> 
</tr>
<tr>
  <td>Temp_2 & Method_2</td> <td>Temp_3 & Method_1</td>   <td>-3.0</td>   <td>0.3764</td> <td>-7.6072</td> <td>1.6072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_2 & Method_2</td> <td>Temp_3 & Method_2</td>    <td>2.5</td>   <td>0.5733</td> <td>-2.1072</td> <td>7.1072</td>   <td>False</td>
</tr>
<tr>
  <td>Temp_3 & Method_1</td> <td>Temp_3 & Method_2</td>    <td>5.5</td>   <td>0.0121</td> <td>0.8928</td>  <td>10.1072</td>  <td>True</td> 
</tr>
</table>



## References
Kutner, M. H., Nachtsheim, C. J., Neter, J., and Li, W. (2004). Applied linear statistical models (5th). New York, NY: McGraw-Hill Irwin.

Rosner, B. (2015). Fundamentals of Biostatistics (8th). Boston, MA: Cengage Learning.

Ott, R. L., and Longnecker, M. (2010). An introduction to statistical methods and data analysis. Belmon, CA: Brooks/Cole.


```python

```
