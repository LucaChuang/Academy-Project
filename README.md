# Project One Red Wine Quality analysis
Author: Team 1
* 2863031 Yunan Chen
* 2863088 Shen-Wei Chuang
* 2868872 Simeng Deng
* 2854110 Zhuo Chen
## Data source: 
https://www.kaggle.com/uciml/red-wine-quality-cortez-et-al-2009

## Introduction/ Motivation/ Literature Review
Before the pandemic, sales of wine have already slowed down. Older customers drink less as they age and winemakers find it hard to attract young consumers as some of them tend to seek a healthier lifestyle without drinking and others have multiple choices for beverages like beer and spirits.[1] US Industry data shows that Millennials consume more liquor and beer than wine. Besides, hard seltzer also becomes more and more popular among young consumers. [2] Traditional winemakers need to develop products that appeal to young customers, like single-serve packing and special flavors, to cope with the fierce competition.

Right now, in the post-pandemic era, customer trends have shifted dramatically in the wine industry. Consumers tend to drink at home to avoid infection, so the demand for on-premise choices and off-premise section totally reversed and sales of off-premise retail channels increased largely. Except for this opportunity, due to the economic shock caused by the pandemic, most people would curtail unnecessary expenses, so expensive wine is absolutely not a desired option.[3] Normally, the gross margin of wineries is 50%. However, under the situation of low demand, the profit margins of wineries decline as fixed cost still remains the same.[4] To maintain profitability, on the one hand, wineries need to develop charming products to expand the younger market. On the other hand, taking advantage of high-tech could avoid unnecessary loss and achieve desirable results. As in-line detection is still not promoted in the wine industry, post-production evaluation and off-site laboratory analysis could not detect the fermentation issues in time to avoid economic losses.[5] The usage of sensors to record fermentation parameters make it possible to detect problems immediately and shape wine character deliberately.[6]

Precise prediction on desired wine quality based on physicochemical parameters would give wine producers insights about essential elements to achieve a certain quality class. Thus, defective products would possibly reduce and cost decline either. The red wine dataset was firstly built to support the wine certification and quality assessment, both of which are essential to assure wine quality and help with setting prices. [7] It contains fundamental properties of wine. For example, attributes relate to taste including acidity(fixed acidity/ volatile acidity/ citric acid/ pH), sweetness (residual sugar), salty( chlorides) and alcohol.[8] Most of these attributes could be controlled during the production process to achieve desirable wine quality. Take pH for example, the wine’s pH is fundamental for flavour and for preventing microbiological spoilage. [9] The desired pH for red wines is around  3.4 . If we want to lower the pH, the most natural way is to add tartaric acid. To increase the pH is just the opposite, tartaric acid need to be decreased and it is achieved through using deacidifying agent such as carbonate salts.[10] Overall, during the fermentation management process, our model would be a good reference for wineries.


## Data Dictionary

**Acid Types and Measures**
* **fixed acidity**: Fixed acids include tartaric, malic, citric, and succinic acids which are found in grapes.
* **volatile acidity**: These acids are to be distilled out from the wine before completing the production process..
* **citric acid**: This is one of the fixed acids which gives a wine its freshness.
* **pH**: Solutions with a pH less than 7 are acidic, while solutions with a pH greater than 7 are basic. With a pH of 7, pure water is neutral. Most wines have a pH between 2.9 and 3.9 and are therefore acidic.

**Sweetness Measure:**
* **residual sugar**: Natural sugar remains from grapes after the fermentation process stops.

**Salty Measure:**
* **chlorides**: Chloride concentration in the wine is influenced by terroir and its highest levels are found in wines coming from countries where irrigation is carried out using salty water or in areas with brackish terrains. 

**Sulfites Measure:**
* **sulphates**: These are mineral salts containing sulfur. 
* **free sulfur dioxide**: This is the part of the sulphur dioxide that when added to a wine is said to be free after the remaining part binds. 
* **total sulfur dioxide**: The sum total of the bound and the free sulfur dioxide. This is mainly added to kill harmful bacteria and preserve quality and freshness. The legal limitation for sulfur levels is regulated. Excess of it can even kill good yeast and give out undesirable odour.

**Body Measure:**
* **density**: This can be represented as a comparison of the weight of a specific volume of wine to an equivalent volume of water. It is generally used as a measure of the conversion of sugar to alcohol. 

**Alcohol**
* **Alcohol**: Alcohol is formed as a result of yeast converting sugar during the fermentation process. It's usually measured in % vol or alcohol by volume (ABV).

**Quality**: Wine experts graded the wine quality between 0 (very bad) and 10 (very excellent). The eventual quality score is the median of at least three evaluations made by the same wine experts.

## Results and Discussion 
**Training and Validation Accuracy:**

From the training and validation accuracy plots we can see that the accuracy of the training has a trend of increasing while the accuracy of the validation is fluctuating severely, especially for the models with class weight modifiication and models with oversampling. The reason for fluctuation of validation accuracy from these models is that we force the net to pay attention to minorities or we change the distribution of input variables, which is not consistent with the reality. And we can only make changes on training dataset because we want to keep the reality of validation and test dataset. Then the inconsistency influences the accuracy greatly.


**Training and Validation Loss:**

We can know that during the process of the training of the neural network, all the models, except models with class weight modification, have a almostly continuous downward training loss curve and a fluctuating validation loss curve which is as we expected. 

As we all know, the FFNN uses gradient to update the weight. And the smoother the gradient is, the flatter the loss will be. If we modify the class wight, increasing the weight of the minority and the influence of them on gradient, the gradient will fluctuate, even vanishing or exploding. As a result, the training loss of models with class weight modification is also fluctuating.


**Confusion Matrix and Classification Report:**

1. Model vs Baseline
All of our models are better than baseline.
2. Classification vs Regression
There is no much difference between these two methods. Performances of them are both good at predicting majorities but not good for the minorities.
3. Original Sample vs Oversampling
Though oversampling decrease the total accuracy a little bit, it can make our model better at predicting minorities than the original one. 
4. Original Variables vs VIF
Not so much difference between these two methods. However, when the dataset is much too larger than what we have now, maybe VIF method can help you save the time for traning the model by decreasing the complexity of your net and still keeping the accuracy.
5. Original Class Weight vs Modified Class Weight
After modifying the class weight, the total accuracy can be higher than the original one. But in the meanwhile, the accuracy for majoities will decrease because of more attention to the minorities.
6. Original Class vs Decoded Class
We decrease the class to make the distribution of the quality more normal. The result shows that we actually can use this method to increase our total accuracy. The inspiration of decodeing target is that we want to focus on the accuracy of quality class higher than 5.


## Business Value
Whinries or wine dealers are always willing to save time and reduce cost to get more money. So our model can help them to monitor and evaluate their products before they sell wine.

Most importantly, different whinries or wine dealers have different target customers. We have suggestions on choosing models to predict as well:

For those whose target customers are people not rich or just want to take a taste, they don't want to dry low quality wine. And for rich people or experts, they typically favor high quality wine. In this case, we recommend using model with oversampling or class weight modification because they have better performance on distinguish the minority class from others. Then develop manufacturing technique to produce proper products.


For those big factories, we recommend VIF model as a result of simplicity, which can save you a lof time and cost with your large dataset.

For those some wine dealers whose requirements are not so high, we recommend using the original network due to its accuracy to help you avoid making mistakes.


## Reference
[1] Growth is Slowing but Consumer Trends Present Opportunities for the Wine Industry

https://www.winebusiness.com/news/?go=getArticle&dataId=224817

[2]How winemakers are adapting to reach young consumers

https://www.capitalpress.com/ag_sectors/orchards_nuts_vines/how-winemakers-are-adapting-to-reach-young-consumers/article_4fb6d96e-5e44-11ea-add6-cf4290c3f7df.html

[3]How will coronavirus affect wine consumption?

https://www.beveragedaily.com/Article/2020/04/07/How-coronavirus-is-shifting-consumer-trends-in-the-wine-industry

[4]Wine Industry Growth Rate & Wine Profit Margins

https://home.binwise.com/blog/wine-industry-growth-rate#:~:text=The%20industry%20standard%20for%20profit,of%20selling%20directly%20to%20consumers.

[5]Cavaglia, J., Schorn-García, D., Giussani, B., Ferré, J., Busto, O., Aceña, L., ... & Boqué, R. (2020). ATR-MIR spectroscopy and multivariate analysis in alcoholic fermentation monitoring and lactic acid bacteria spoilage detection. Food Control, 109, 106947.

https://www.sciencedirect.com/science/article/pii/S0956713519305365

[6]Technology used in red wine production

https://blog.drinktec.com/wine/technology-used-in-red-wine-production/#:~:text=2.,CO2%20or%20alcohol%20extraction.

[7]Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). Modeling wine preferences by data mining from physicochemical properties. Decision Support Systems, 47(4), 547-553.

https://www.sciencedirect.com/science/article/pii/S0167923609001377?via%3Dihub#aep-bibliography-id29

[8]Wine Type and Quality Classification

https://www.kaggle.com/mgmarques/wines-type-and-quality-classification-exercises

[9]Optimizing wine quality in Australia, Coonawarra wine region: vinification and fermentation control management in Shiraz wine. Internship report.

https://www.repository.utl.pt/handle/10400.5/19578

[10]Monitoring & Adjusting pH

https://winemakermag.com/technique/1650-monitoring-adjusting-ph#:~:text=To%20increase%20pH%2C%20use%20a,%2C%20high%2Dmalic%20acid%20wines.
