## Welcome to ECC Self-healing GitHub Pages

The aim of this research is to evaluate the self-healing behaviour of ECC when incorporated with diﬀerent minerals, focusing on self-healing capability, repeatability and modelling prediction. In addition, it is expensive and time-consuming to quantify self-healing capability by conducting experiments, and diﬃcult to mathematically predict self-healing based on available data.  Therefore, an accurate and reliable self-healing prediction model will be designed to reduce time and costs for enhancing the durability design of ECC.

### Methods

#### Machine learning methods comparative analysis

![image-20220321043910940](https://raw.githubusercontent.com/davidnsw/2020images/1a34dc602c2c8e89389af373aad3812bc3e2eea1/Rsqure.png)

Average R 2 for performance of self-healing of ECC on all machine learning models

The comparative analysis showed all 13 models came with expected accuracy and predictability. The BPNN model was prominent in the individual models in terms of forecast error, Root Mean Square Error (RMSE) and accuracy, R 2 .  Stacking model was superior to all other individual or ensemble models on the basis of all three performance measures.



#### BPNN optimized with EA in structured tree and list

![](https://raw.githubusercontent.com/davidnsw/2020images/master/BPNN%20Chematic%20EC.png)

The BPNN model is further optimized by the Evolutionary Algorithm (EA) in structured tree and list to construct two predictive tools to model the self-healing repeatability of ECC for improving the prediction performance.  The proposed EA-based BPNN models overcame the drawback of BPNN with slow convergence and getting trapped in local minima.

![](https://raw.githubusercontent.com/davidnsw/2020images/master/EA-BPNN.png)

Especially, the EA-based BPNN in structured tree model ensures genetic diversity and keep ﬁt solutions guaranteeing quality children of following generations, and is more space eﬃcient leading to quick searching and convergence. 

### Data

[Click here](https://github.com/davidnsw/Self-healing-of-ECC/blob/634cb4597fe66e291a79affb4fa31843f78ce682/Crack.txt) to download the crack data this project. The txt file contains the correspondence between the mix composition and the cracks, which can be called in by python directly (source code provided). For details please refer to [Appendix A of this reference](https://github.com/davidnsw/Self-healing-of-ECC/blob/634cb4597fe66e291a79affb4fa31843f78ce682/Main.pdf).

#### Reference 1

If using or improving the source code in this project, please add the following references

[1] Chen, G. Repeatability of self-healing in ECC with various mineral admixtures. PhD thesis, School of Architecture and Built 663
Environment, University of Newcastle, Australia, 2021. 

**BibTex**

```latex
@misc{Charles2013,
  author = {Chen, G.W.},
  title = {Self-healing of ECC},
  year = {2021},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/davidnsw/Self-healing-of-ECC}},
}
```

---

#### Reference 2

If you use the above experimental ideas or use the relevant data of this project, please use the following citations:

[2] Chen, G. Self-healing of ECC. GitHub repository, https://github.com/davidnsw/Self-healing-of-ECC, 2021. 

**BibTex**

```latex
 @phdthesis{chen_2021, 
 title={Repeatability of self-healing in ECC with various mineral admixtures}, 
 year = {2021},
 publisher = {University of Newcastle},
 author={Chen, Guangwei}, year={2021}
 } 
```

#### SEM / XRD Data

---

### Code

[Click here](https://github.com/davidnsw/Self-healing-of-ECC/raw/634cb4597fe66e291a79affb4fa31843f78ce682/Main.pdf) to download the source code in of this project. (Appendix A and Appendix B)

`Example:`

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



### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://davidnsw.wufoo.com/forms/leave-a-message-to-david-chen/) and we’ll help you sort it out.
