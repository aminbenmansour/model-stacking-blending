# model-stacking-blending

Ensemble learning methods does enhances significantly the accuracy of the model and they have been excessively used to win kaggle and zindi competitions.

We are going to follow these two great blogs: [Stacking and Blending — An Intuitive Explanation](https://medium.com/@stevenyu530_73989/stacking-and-blending-intuitive-explanation-of-advanced-ensemble-methods-46b295da413c) and [Introduction to Ensemble Methods in Machine Learning](https://towardsdatascience.com/introduction-to-ensemble-methods-in-machine-learning-e72c6b9ff4bc) in order to implement model stacking and model blending. Both are pretty similar but with some differences.


blending is used to describe the specific application of stacking where the meta-model is trained on the predictions made by base-models on a hold-out validation dataset. In this context, stacking is reserved for a meta-model that is trained on out-of fold predictions during a cross-validation procedure
