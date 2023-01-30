# Neural Networks and Deep Learning Models
A classwork example in which machine learning and neural networks are used to help create a binary classifier capable of predicting a 'success' or 'fail' classification for potential funding projects using Scikit-Learn, Python/ Pandas, Tensorflow, and Matplotlib for visualization.

---

# Overview
This is where the overview will go

## Purpose
This is where the purpose will go

---

# Results 
## Original Model
![Original model code](/Resources/original_model_code.png)
*Original model code*

In the original model code, both columns "EIN" and "NAME" are dropped in the clean up phase. "APPLICATION_STATUS" and "CLASSIFICATION" are binned to minimize the amount of rare values in the final model. After preprocessing, the data is split into feature and target arrays with the binary column "IS_SUCCESSFUL" being the target column and the remaining columns as features. THe data is split into testing and training data, it is scaled, and fit into a model with two hidden layers and one output layer. (RELU) and (SIGMOID) models are used. The model is then compiled before a callback checkpoint is made and the model is trained. 

![Original trained model code](/Resources/original_trained_model_code.png)
*Original trained model code*

The model was run for 25 Epochs due to the model hitting minimal loss and peak accuracy within very few Epoch runs.

![Original accuracy lossh results](/Resources/original_accuracy_loss.png)
*Original accuracy and loss results*

The original model had 76.70705914497375% loss and 51.31195187568665% accuracy. This model has poor performance whether that be for the input data values, number of hidden layers, or number of neurons in those layers. 

![Original accuracy history](/Resources/original_accuracy_history.png)
*Original accuracy history*

This is a graphic depiction of the accuracy history throughout the Epoch sessions.

![Original loss history](/Resources/original_loss_history.png)
*Original loss history*

This is a graphic depiction of the loss history throughout the Epoch sessions.

---

# Summary
After viewing the results of the model and my manually created optimizations, I would recommend using an automated optimized such as the keras-tuner package. The keras-tuner package would optimally select which activation function to use, how many neurons would be in the first hidden layer, and the number of subsequent hidden layers as well as the neurons within those layers. 
After creating a keras-tuner optimization function and running the training data through the tuning model, it can return the best hyperparameters and best models to use based on the parameters set in the function. We could then run the testing data against the best models to receive a model with high accuracy and low loss. It would be possible to store and rerun the model after this process. 
We would need to be wary of overfitting based on training data, but dilligence and attention can help gaurd against this possibility. This method would also not help with the preparation of the input data, meaning there are some data points that could be excluded to make a more efficienct model.
