[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)
[![Open In Collab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Naereen/badges)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

# Pet project 🐶 on Data Analysis, Regression, Clustering and Feature Importance👨🏻‍💻

This is my pet project to find a job as Data Analyst / Data Scientist.
<div style="text-align: justify">
I found on Kaggle a pretty good and small dataset to analyse  ([dataset online](https://www.kaggle.com/datasets/mirichoi0218/insurance)). Initial purpose was just to make some analysis, and explore the trendline, but once I started working with this dataset I decided to make a complete analysis.
<br><br>
My explorations consist of three major steps:

* Exploratory Data Analysis.📊
* Data Clustering.🎨
* Regression and Feature Importance Analysis.📈

And

* Research Conclusion

The next few passages will explain briefly what I've done to obtain complete understanding of data, which techniques are used and with help of which packages. So, let's get started!

## 📊 **Exploratory data Analysis**
To be concise, two most important points are that we see clear division of our clients in three groups into: smokers, non-smokers and mixed. Smokers charge much more money then people which follow healthy lifestyle. But _amount of smokers in data are much less than healthy_ clients. Features `sex`, `region`, `age` are roughly uniformal distributed, `bmi` is  normaly distributed (as expected), and a large portion of clients have no `children` or 1, or 2.
<br>**In Conclusion:** old clients with high bmi that smoke - charge the most money out of our company, so we would say that this clients are least welcome to have a nice insurance package (it is my personal recomendation).
<br>For more information visit `data_exploration.ipynb`.

## 🎨 **Data Clustering**
After `Exploratory Data Analysis` we are still not sure if we can group our clients by smoking status. To better understand that, I decided to run **Cluster Analysis**.
<br> After experiments with _Agglomerative Clustering_, _K-Means_ and _Spectral Clustering_ we can make an inference that we have aproximately from _**3 to 5 clusters**_. And by looking at results from _K-Means_ and _Spectral Clustering_ we see that ML algorithm decided to divide clients not by smoking stutus, but by age and this make sense too. So, right now we see that we have two candidates to be most significant features, those are `smoker` and `age`.
<br>For more information visit `data_clustering.ipynb`.

## 📈 **Regression and Feature Importance Analysis**
Before runing regression models, I dicided to look at correlation matrix, and saw that three most correlated features with `charges` were `smoker`, `age` and `bmi` respectively. That is once more approves over previous assumptions. To be sure that there are no multicolinearity I calculated _Variance Influence Factor_ test, and all values were close to _1_, so there are no multicolinearity in data.
<br> Then, before running _Linear Regression_, I run _Principal Component Analysis_ and it show that 98% of information can be gained by leaving only 1 feature in dataset, and this feature is `age`, so to visualise data we can compress it just ot one feature.
<br>To run _Linear Regression_ I transformed target variable `charges` to normal distribution with _Quantile Transformer_. And with this we got that our _Linear Regression_ coefficients are all significant, model is adequate and residuals are normaly distributed. The accuracy of our model with $R^2=0.73$ on a test set, that is pretty decent result for a linear model. Additional I applied _Permutation Feautre Importance_ to identify most informative ones, and got that top three features are `smoker`, `age` and `bmi`.
<br>To produce better accuracy with $R^2$ I decided to apply _Random Forest_ algorithm to data, and got $R^2=0.83$ on a test set. _Permutation Importance_ yielded roughly same results.
<br>For more information visit `regression_modeling.ipynb`.

## **Research Conclusion**
We built a _Random Forest_ regression model and got accuracy by $R^2=0.83$.We analyzed our clients in most detailed maner, and we can clearly say that most unlikely clients for our company would be people that `smoke`, are `old` and have high `bmi`. What else we can say is that we can divide our customers into 3 to 5 groups based on `age` and maybe it could be reasonable to built individual regression models for each of these catagory of people. Thanks for your time!
</div>
