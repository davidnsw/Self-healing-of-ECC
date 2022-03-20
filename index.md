## Welcome to ECC Self-healing GitHub Pages

You can use the [editor on GitHub](https://github.com/davidnsw/Self-healing-of-ECC/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Methods

#### Machine learning methods comparative analysis

![image-20220321043910940](https://raw.githubusercontent.com/davidnsw/2020images/1a34dc602c2c8e89389af373aad3812bc3e2eea1/Rsqure.png)

Average R 2 for performance of self-healing of ECC on all machine learn-
ing models



#### BPNN optimized with EA in structured tree and list

![](https://raw.githubusercontent.com/davidnsw/2020images/master/BPNN%20Chematic%20EC.png)

![](https://raw.githubusercontent.com/davidnsw/2020images/master/EA-BPNN.png)

Appendix B

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

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



For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Data

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/davidnsw/Self-healing-of-ECC/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.



### Code

Appendix A

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
