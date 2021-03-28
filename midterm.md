## Answers and corrections for midterm (questions I got wrong are in bold)

15. The answer for this was “MedInc”, which I got through getting the correlation coefficient of each feature and then manually comparing them. I did this by doing the following:

`print("MedInc:")
print(np.corrcoef(test['MedInc'], test.target))
print("HouseAge:")
print(np.corrcoef(test['HouseAge'], test.target))
print("AveRooms:")
print(np.corrcoef(test['AveRooms'], test.target))
print("AveBedrms:")
print(np.corrcoef(test['AveBedrms'], test.target))
print("Population:")
print(np.corrcoef(test['Population'], test.target))
print("AveOccup:")
print(np.corrcoef(test['AveOccup'], test.target))
print("Latitude:")
print(np.corrcoef(test['Latitude'], test.target))
print("Longitude:")
print(np.corrcoef(test['Longitude'], test.target))`

16. The answer for this was “True”, which I got through comparing my findings to the last question. I did this by doing the following:

`X = data.data
X_names = data.feature_names
X_df = pd.DataFrame(data = X, columns=X_names)


ss = StandardScaler()
X_scaled = ss.fit_transform(X_df)
X_scaled_df = pd.DataFrame(X_scaled, columns=X_names)


print("MedInc:")
print(np.corrcoef(X_scaled_df['MedInc'], test.target))
print("HouseAge:")
print(np.corrcoef(X_scaled_df['HouseAge'], test.target))
print("AveRooms:")
print(np.corrcoef(X_scaled_df['AveRooms'], test.target))
print("AveBedrms:")
print(np.corrcoef(X_scaled_df['AveBedrms'], test.target))
print("Population:")
print(np.corrcoef(X_scaled_df['Population'], test.target))
print("AveOccup:")
print(np.corrcoef(X_scaled_df['AveOccup'], test.target))
print("Latitude:")
print(np.corrcoef(X_scaled_df['Latitude'], test.target))
print("Longitude:")
print(np.corrcoef(X_scaled_df['Longitude'], test.target))`


**17. The answer is 0.47. Originally, I got 0.42. This was because I figured that I could use the specific sklearn command “coef_”, and simply specify that I only wanted median income, or lin_reg.coef_[0]. I did this because the note on the test said it could be done in one line. Now, I realize that I went about this the wrong way. This is because I didn’t use the numpy command corrcoef(), nor did I specify the specific feature I wanted by name, but just tried to use its index. Additionally, I forgot to square the value, and set the specific rounding I desired. The difference between my original answer and the new one is due to these differences.**

18. The answer for this was **, which I got. I did this by setting up a function called DoKFold(model, X, y, k, standardize=False, random_state=146), then calling it as: 

`train_scores, test_scores = DoKFold(lin_reg,X1,y1,20,True)`

The default random state was 146, but I set k to 20, and shuffle to true.

19. The answer for this was **, which I got. I did this by **.
20. The answer for this was **, which I got. I did this by **.
21 and 22:

For these two questions, I refit a linear, Ridge, and Lasso regression to the entire dataset. I then plotted the results of each in-terms of coefficient for each variable (compared to the target). From here, I looked at each plot, and manually compared the variable that was least correlated for question 21 (by looking at my earlier work for question 15), and did the same for question 22 using the variable that was most correlated (again from my earlier work in question 15). I used the following code:

`from sklearn.preprocessing import StandardScaler as SS
ss = SS()
Xs = ss.fit_transform(eX)
lin_reg.fit(Xs,why)
lin_coefs = lin_reg.coef_
a_range = np.linspace(0,1000,100)
rid_coefs = []
for a in a_range:
    rid_reg = Ridge(alpha=a)
    rid_reg.fit(Xs,y)
    rid_coefs.append(rid_reg.coef_)
plt.figure(figsize=(12,6))
plt.plot(a_range, rid_coefs)
plt.scatter([0]*len(lin_coefs), lin_coefs)
plt.legend(X_names, bbox_to_anchor=[1, 0.5], loc='center left')
plt.xlabel('$\\alpha$')
plt.ylabel('Coeff. Estimates')
plt.show()

a_range = np.linspace(1e-6,1,100)
las_coefs = []
for a in a_range:
    las_reg = Lasso(alpha=a)
    las_reg.fit(eX,why)
    las_coefs.append(las_reg.coef_)
plt.figure(figsize=(12,6))
plt.plot(a_range, las_coefs)
plt.scatter([0]*len(lin_coefs), lin_coefs)
plt.legend(X_names, bbox_to_anchor=[1, 0.5], loc='center left')
plt.xlabel('$\\alpha$')
plt.ylabel('Coeff. Estimates')
plt.show()



a_range = np.linspace(0,1000,100)
lin_coefs = []
for a in a_range:
    lin_reg.fit(Xs,y)
    lin_coefs.append(lin_reg.coef_)


plt.figure(figsize=(12,6))
plt.plot(a_range, lin_coefs)
plt.scatter([0]*len(lin_coefs), lin_coefs)
plt.legend(X_names, bbox_to_anchor=[1, 0.5], loc='center left')
plt.xlabel('$\\alpha$')
plt.ylabel('Coeff. Estimates')
plt.show()`

23. For this, I recreated the situation that it referred to, and found that they were in fact different values.

**24. The answer is 0.00186. That being said, originally, I got 0.00081. This was because I figured that in order to get the mean squared error for these scores, I would need to use both the training and testing score variables. I got this answer by making a list for testing scores that found a mean squared error for each testing and training scores. Now, I realize that I instead needed to take the mean of each testing and training score individually, and stick them into a respective list. My problem was that I both tried to apply MSE to each set of testing and training scores individually, and also that I did so using both testing and training scores together. 0.00186 is the answer once I correct my mistakes.**

Below was my code:

`for a in a_range:
    rid_reg = Ridge(alpha=a)
    train_scores,test_scores = DoKFold(rid_reg,X1,y1,k,standardize=True)
    difference = np.mean(train_scores) - np.mean(train_scores)
    avg_te_score1.append(mean_squared_error(train_scores, test_scores))
idx = np.argmin(avg_te_score1)
print('Optimal alpha value: ' + format(a_range[idx], '.10f'))
print('MSE' + format(avg_te_score1[idx], '.10f'))`


