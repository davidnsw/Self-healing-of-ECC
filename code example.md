```python
for train_index, test_index in cv.split(X_data):
    X_train,y_train = X_data[train_index],y_target[train_index]
    X_test, y_test = X_data[test_index], y_target[test_index]
    with open('04TESTInput_New.txt','a+') as f:
        f.write(f'{X_test}\n');
    with open('04TestTarget_New.txt','a+') as f:
        f.write(f'{y_test.tolist()}\n')
    for names, methods in methodDict.items():
        print(names)
        retr = methods
        retr.fit(X_train, y_train)
        prediction = retr.predict(X_test)
        prediction = prediction.clip(0)
        with open('04PreditcTarget_New.txt','a+') as f:
            f.write(f'{names},{prediction}\n')
        MAE = mean_absolute_error(y_test,prediction)
        RMSE = sqrt(mean_squared_error(y_test,prediction))
        score_R2 = r2_score(y_test,prediction)
        print(MAE,RMSE,score_R2)
        statcs.append([names,MAE,RMSE,score_R2])

        with open('04statistic_New.txt','a+')as f:
            f.write(f'{names},{MAE:.3f},{RMSE:.3f},{score_R2:.3f}\n')
df = pd.DataFrame(statcs,columns = ['methods','MAE','RMSE','R2'])
```

