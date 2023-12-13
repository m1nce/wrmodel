# League Win-Lose Prediction Model
By Minchan Kim and David Moon

This project was made for DSC80 at UCSD where we took data from professionally played League of Legends matches in 2022 to clean, analyze, and make a prediction model in order to see whether a team will win or not based on different features. The purpose of this website is to report our findings and our tests. Our exploratory data analysis page can be found [here](https://m1nce.github.io/Gold-Lead-Analysis/). We will be using the same dataset and most of our data will be cleaned the same way we did in our analysis so make sure to check out that page to understand what columns we removed and saved.

# Introduction / Framing the Problem

In every game, players play to the best of their abilities to secure even a small advantage against their opponents to increase the odds of winning. But is this really the case? Can small advantages such as a gold lead at a mere 10 minutes or them securing the first herald or dragon really indicate whether or not they will win a game?

In this analysis, we will look at the dataset for all of the competitive league matches in the LCK (the best region) in order to predict whether a team will win or not.

In every game, there are only two possible outcomes for each team. It will either result in them winning or losing the game. Since there are only two possible outcomes, we will use a binary classification model as a multiclass classification model predicts when there are multiple outcomes when we are only interested in whether or not a team wins or not.

As stated earlier, our response variable will be **result**, which is whether or not a team wins or loses. We will code it to make it so that a win will represent the number “1” and a loss will represent the number “0”. As far as our metrics, we have four possible metrics, which are precision, F-1 score, precision, recall, and accuracy.

We have chosen accuracy as our metric for evaluating our model. This decision was made  because our dataset is considered to be balanced. By 'balanced,' we refer to the equal distribution of wins and losses. For each match in our dataset, there is only one win and loss recorded. Given this structure, the dataset inherently aligns the number of positive and negative cases, allowing for a straightforward interpretation of accuracy. In this context, the trade-off between false positives and false negatives is relatively neutral. This means neither type of error (incorrectly predicting a win when it's a loss, or vice versa) is more critical than the other. Therefore, accuracy is the most relevant and informative metric, providing a clear and direct measure of our model's overall predictive performance in comparison to F-1 score, precision, and recall.

As far as the “time of prediction,” we would have access to all of the information because all of the data would be recorded before the game has concluded (and as the game is going on) so we would know all of the information before the game “officially” ends. The features we mostly focus on are from the beginning of the match like team differences (ex. gold, experience, creep score) and securing the first objective (ex. dragon, herald).

# Baseline Model

For our baseline model, we wanted to predict a team's outcome (win or loss) depending on a couple of features. We used the `'golddiffat10'`, `'firstherald'`, `'firstdragon'`, `'firstblood'`, `'xpdiffat10'`, and `'csdiffat10'` columns in order to predict the outcome.

Quantitative Features: `'golddiffat10'`, `'xpdiffat10'`, and `'csdiffat10'`
Nominal Features: `'firstherald'` ('1' indicating the team secured the first Rift Herald, and '0' otherwise.)
, `'firstdragon'` (‘1' indicating the team secured the first dragon, and '0' otherwise.)
, `'firstblood'` (‘1' indicating the team secured first blood, and '0' otherwise.)
, and `‘side’` (‘1’ indicating red side, and ‘0’ indicating blue side)

Response Variable: Win or loss (‘1’ indicating a win, ‘0’ indicating a loss)

All of the columns in our categorical features  except for our `'side'` column were technically already hot encoded so all we have to hot encode ourselves manually would be the `'side'` column and we will do so by making ‘1’ being the red side and ‘0’ being the blue side. We also just leave the quantitative features alone.

Conclusion from Baseline:

After running our model, we had an accuracy of about 0.68. This means that our model is getting there, but definitely still has some work to do. We think that the our model isn’t necessarily the best but also not the worst. We believe that having small leads by getting the first dragon or herald, and in gold, experience, and/or creep score have some indication on predicting a teams’ outcome but these leads may not be decisive factors in determining the final result. Crucial game-changing events like obtaining the Baron, securing the Dragon Soul, or winning significant teamfights typically occur later in the game. Therefore, while our model captures some aspects of early game dynamics, it may not fully account for the more impactful events that happen later on into the game.
