# model-stacking-blending

Ensemble learning methods does enhances significantly the accuracy of the model and they have been excessively used to win kaggle and zindi competitions.

We are going to follow these two great blogs: [Stacking and Blending — An Intuitive Explanation](https://medium.com/@stevenyu530_73989/stacking-and-blending-intuitive-explanation-of-advanced-ensemble-methods-46b295da413c) and [Introduction to Ensemble Methods in Machine Learning](https://towardsdatascience.com/introduction-to-ensemble-methods-in-machine-learning-e72c6b9ff4bc) in order to implement model stacking and model blending. Both are pretty similar but with some differences.


blending is used to describe the specific application of stacking where the meta-model is trained on the predictions made by base-models on a hold-out validation dataset. In this context, stacking is reserved for a meta-model that is trained on out-of fold predictions during a cross-validation procedure

## Stacking

Stacking or stacked generalisation was introduced by Wolpert. In the essence, stacking makes prediction by using a meta-model trained from a pool of base models — the base models are first trained using training data and asked to give their prediction; a different meta model is then trained to use the outputs from base models to give the final prediction. The process is actually quite simple. To train a base model, K-fold cross validation technique is used.

* **You have Train Data and Test Data. Assume we are using 4-fold cross validation to train base models, the train_data is then divided into 4 parts.**

![1_yesnizWjGSNGsUmlkhX18w](https://user-images.githubusercontent.com/50111205/171964253-ec74a830-cc9d-4e29-8393-724be779e64b.png)

* **Using the 4-part train_data, the 1st base model (assuming its a decision tree) is fitted on 3 parts and predictions are made for the 4th part. This is done for each part of the training data. At the end, all instance from training data will have a prediction. This creates a new feature for tain_data, call it pred_m1 (predictions model 1).**

![1_yYFpm4Duauymbqmcs7pqTA](https://user-images.githubusercontent.com/50111205/171964421-d1817095-fa9a-4fbd-9c01-debd6c6a6289.png)

![1_zpYK59ERadLpks69gxANAw](https://user-images.githubusercontent.com/50111205/171964527-ffce52e8-7819-4fcd-8491-97040bdab053.png)

* **Model 1 (decision tree) is then fitted on the whole training data — no folding is needed this time. The trained model will be used to predict Test Data. So test_data will also have pred_m1.**

![1_66ItWo6uyEvindU-0S9nnQ](https://user-images.githubusercontent.com/50111205/171964607-a03d768e-fc2e-41b2-8c3e-6e152e4edda0.png)


## Blending

blending is relatively easier than stacking, it does not require k-fold cross-validation. the following pictures illustrates how it is performed.

Blending is very similar to Stacking. It also uses base models to provide base predictions as new features and a new meta model is trained on the new features that gives the final prediction. The only difference is that training of the meta-model is applied on a separate holdout set (e.g 10% of train_data)rather on full and folded training set.


* **train_data is split into base_train_data and holdout_set.**

![1_5RXUF92qwpx-1BkcTejIoQ](https://user-images.githubusercontent.com/50111205/171749521-0fd9ee50-7113-4a15-883f-5d5722357985.png)

* **Base models are fitted on base_train_data, and predictions are made on holdout_set and test_data. These will create new prediction features.**

![1_pvGUnMAycqvsYAwVe2LpHw](https://user-images.githubusercontent.com/50111205/171749687-2dcc0246-0183-4679-8377-94aa8b5bdc99.png)
