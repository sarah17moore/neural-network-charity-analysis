# Neural Networks and Deep Learning Models
A classwork example in which machine learning and neural networks are used to help create a binary classifier capable of predicting a 'success' or 'fail' classification for potential funding projects using Scikit-Learn, Python/ Pandas, Tensorflow, and Matplotlib for visualization.

---

# Overview
This is where the overview will go

## Purpose
This is where the purpose will go

---

# Results 
This is where the results will go

---

# Summary
After viewing the results of the model and my manually created optimizations, I would recommend using an automated optimized such as the keras-tuner package. The keras-tuner package would optimally select which activation function to use, how many neurons would be in the first hidden layer, and the number of subsequent hidden layers as well as the neurons within those layers. After creating a keras-tuner optimization function and running the training data through the tuning model, it can return the best hyperparameters and best models to use based on the parameters set in the function. We could then run the testing data against the best models to receive a model with high accuracy and low loss. It would be possible to store and rerun the model after this process. We would need to be wary of overfitting based on training data, but dilligence and attention can help gaurd against this possibility. 
