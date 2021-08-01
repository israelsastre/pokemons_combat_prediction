# POKEMONS PREDICTION COMBAT - A MACHINE LEARNING PROJECT

This project is based on the Kaggle Dataset:
https://www.kaggle.com/shubhamchambhare/pokemons-and-there-stats

Created by https://www.kaggle.com/shubhamchambhare

It's a Dataset **with 1045 Pokemons** and these characteristics: *name, total, attack, defense, hit points, speed, special attack and special defense*

The idea is to create a predictive model to find out who would be the winner in a fight between two Pokemons.

For this I have carried out the following processes:

1- Transformation of original data by adding one more characteristic: **Category**, based on the score in the 'Total' column of the dataset.

2- Creation of a class called **Fight**. This class receives the index number of 2 pokemons from the dataset and returns the result of the combat.

  * The rules of combat are not those established in the cards game, but I have created a system based on the statistics provided by the database, in addition to a random component in relation to the percentages of damage from attacks and from defense blocking as well as percentages of probability of attacks and special defenses **(detailed explanation in section 2.5)**.
  * The result object has the quantitative differences between the values ​​of each Pokemon and the winner of the combat. Another parallel DF has the same data and the random statistics generated **(detailed explanation in section 2.5)**.

3- That object will be used to create our ML model, for this we create a dataset with a loop that will generate 186,750 combats. We will divide this Dataset into one with 40% of the confrontations to train and predict the models and the remaining 60% we will leave it unseen to evaluate the 3 best models **more information in sections 2.6 and 2.7**. This leaves us with a supervised learning binary classification problem.

4- We will carry out tests with different models and ensembles

5- We will evaluate the models based on several metrics and we will select the 3 best ones.

6- With the best 3 we will fit with the entire 40% training set and we will see the performance in two ways:
  * The accuracy of the model predicted at the unseen df (60% from Total combats)
  * We will do CrossValidation with the useen dataset (60% from Total combats. In Cv it will test n-times spliting the dataset n-times in training and test sets)
  * The winning model will be the one that obtains the best average between both values

7- With the winning model we will make a **fitting with the entire database** (60% unseen + 40% Training). We will simulate as if it was in production with a small interface through a form.

In this form we will also simulate as if the model itself learned with the new fights in such a way that every 30 fights it performs two actions:
  * Monitor with these new fights if the model continues to maintain good predictions; if not, it issues a warning.
  * New fitting to the model with the complete dataset and the new 30 predictions.

In addition there are two final appendices

**Appendix 1**: Code to tune and evaluate all the models at once

**Appendix 2**: Using the winning model, here is the code to make the predictions with the dataset that includes the random statistics generated in the combat. Although these statistics are impossible to know beforehand, it is a good exercise to observe **the importance of randomness** in the performance of the model.

**IMPORTANT**

**the selected models and parameter tunnig are by my choice. I understand that there may be other options. My best result is 88.64% accuracy. If someone wants to try and find better precision, it would be apreciated. In the Kaggle repositories I leave the databases created to download, in addition to being able to work with the same data**

**NOTE**
* Many of the variable names are in Spanish since initially it is the language in which I made it and changing them all thinking that there will not be a problem at some point is too optimistic. That is why I have translated the texts and prints, but not the names of variables, columns and indexes. I hope it is understood *
