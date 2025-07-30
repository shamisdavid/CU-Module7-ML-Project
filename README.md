# CU Boulder Module 7: Supervised Learning Project

# Exploratory Data Analysis (EDA): Impact of Tweet Sentiments on Stock Prices

### Project Overview

This analysis investigates how tweet sentiment affects stock prices using a dataset containing stock return data and tweet sentiment scores. The dataset was processed, cleaned, and visualized to understand relationships between sentiment polarity, stock returns, trading volume, and tweet counts. New features were also added through engineering before applying Machine Learning techniques like Linear Regression and Random Forest Regression.

### Data Cleaning and Preprocessing

- Dropped unnecessary columns.
- Converted date columns to appropriate datetime formats.
- Handled missing values.
- Ensured numeric columns were correctly formatted for analysis.

### Key Insights

#### 1. Distribution of Sentiment Scores
![download](https://github.com/user-attachments/assets/ae6d1f1f-b128-4a0a-91ac-622c4b687c9e)

##### The lstm_polarity column represents the sentiment polarity of tweets as determined by a Long Short-Term Memory (LSTM) neural network model. The LSTM model reads the text of each tweet and derive a sentiment score, typically denoting positive, negative, or neutral sentiment.
##### Textblob_polarity column represents sentiment polarity of tweets as analyzed using TextBlob library. TextBlob is a Python library for processing textual data with APIs for language processing like sentiment analysis. Polarity score returned by TextBlob ranges from -1 to 1, with:
##### -1: Represents an extremely negative sentiment.
##### 0: Represents a neutral sentiment.
##### 1: Represents an extremely positive sentiment.

#### Findings:

- LSTM and TextBlob sentiment polarities show different distributions.
- The polarity scores generally center around neutral values.

#### 2. Stock Returns Comparison: 1-Day vs. 7-Day
![download](https://github.com/user-attachments/assets/f4328c95-cfd8-46ae-84d1-5b1d3a089b72)

#### Findings:

- 7-day returns are more spread out than 1-day returns.
- The data suggests that short-term fluctuations do not always translate into long-term movement.

#### 3. Sentiment Scores vs. 1-Day Stock Returns
![download](https://github.com/user-attachments/assets/e501a568-d6f4-4868-a4ef-6e7835470657)

#### Findings:

- Weak correlation observed between sentiment polarity and 1-day stock returns.
- Some extreme sentiment scores correspond to higher volatility in returns.

#### 4. Sentiment Scores vs. 7-Day Stock Returns
![download](https://github.com/user-attachments/assets/6dfbdc90-e9c2-4a92-afc3-a5e5669e8eb9)


#### Findings:

- Similar weak correlation as seen in 1-day returns.
- Longer-term returns may be influenced by additional market factors beyond sentiment.

#### 5. Actual vs. Predicted Returns: Linear Regression

As a baseline model to measure how well sentiment and stock-related attributes can predict stock returns, Linear Regression was chosen because it is simple to interpret, and can determine whether these attributes are linearly related to stock price movement. Since financial data often follow complex patterns, this model is a good initial choice before trying more complex techniques like Random Forest.

![download](https://github.com/user-attachments/assets/f077d8d4-fa65-4c4e-994a-a8e4baa23fc7)

#### Findings:
- Predictions are spread wide apart, indicating low predictive power.
- The R² value means that our selected features (sentiment, volume, volatility) don't explain stock returns well using a linear model.
- Stock returns can't always have a strictly linear relationship with sentiment data.

### 6. Actual vs. Predicted Returns: Random Forest

The poor performance of Linear Regression led to trying Random Forest Regression, a more general model that can detect non-linear patterns of stock price movement. Random Forest employs an ensemble of decision trees and is therefore more capable of handling datasets that consist of many interacting variables. When used, this model found much improved accuracy, with an R² of 0.8670 compared to Linear Regression's 0.0063. This means that sentiment, tweet activity, and volatility are related in ways that cannot be represented by a linear model. The fact that the model does better means that non-linear relationships and other context variables, such as market conditions and overall economic indicators, must be considered when looking at the impact of sentiment on stocks.

![download](https://github.com/user-attachments/assets/47962c15-6bfc-4ead-85ff-dcf64057d591)

#### Findings:
- Predictions are much closer to actual returns compared to Linear Regression.
- Random Forest captures some of the nonlinear relationships and thus has greater accuracy.
- The model's high R² value shows that adding more financial or fundamental indicators can further boost performance.

### Model Performance Comparison
| Model | R² Score | Mean Squared Error (MSE) |
|--------|-----------|-----------------|
| **Linear Regression** | 0.0063 | 0.000511 |
| **Random Forest Regression** | 0.8670 | 0.000068 |

- Future studies should include macroeconomic variables. Combining sentiment with other factors such as interest rates, earnings announcements, and global economic conditions may enhance predictability and provide a more comprehensive overview of the market.
- Sentiment may affect volatility more so than direction. While the models were unable to predict exact price movements, they suggest that surges in sentiment do correlate with higher trading volumes and market action.

### Financial Implications & Investment Insights

- Short-Term Trading Strategies: The findings from Random Forest show that non-obvious patterns in the direction of stock movement can be detected by machine learning algorithms. Short-term traders can potentially use sentiment information with technical indicators like volatility and momentum.
- Risk Management: Volatility analysis shows that highly volatile stocks remain so in the longer term. Sentiment trends can be utilized by investors to anticipate changes and hedge against them in advance.


### Next Steps & Future Improvements

#### 1. Hyperparameter Tuning
- Optimize the Random Forest model by adjusting tree depth, number of trees, and features.
- Try other Machine Learning models like Gradient Boosting to enhance predictive power.

#### 2. Improving Deep Learning
- Employ LSTM models to identify sequential patterns between sentiment shifts and stock price movements.
- Investigate whether deep learning techniques are superior to tree-based models for this application.

#### 3. Incorporating Market Activity
- Include wider financial indicators (S&P 500 price movement, economic news, interest rate changes).
- Test if adding sentiment together with macroeconomic features improves predictions.

#### 4. More Feature Engineering
- Understand sentiment "momentum" features by seeing how fast the sentiment is changing and not just its raw value.
- Include tweet engagement features (likes, retweets) to give weight to how impactful high-visibility tweets are.


### Repository Structure

- CU_Boulder_Module7_SupervisedLearning.ipynb: Jupyter Notebook with full EDA analysis and ML.
- Images/: Folder containing images of generated plots.
- Data/: Folder containing the dataset.
- README.md: Full EDA

### Sources

- https://www.kaggle.com/datasets/thedevastator/tweet-sentiment-s-impact-on-stock-returns/data
