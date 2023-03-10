# Neural Networks and Deep Learning Models
A classwork example in which machine learning and neural networks are used to help create a binary classifier capable of predicting a 'success' or 'fail' classification for potential funding projects using Scikit-Learn, Python/ Pandas, Tensorflow, and Matplotlib for visualization.

---

# Overview
Alphabet Soup is a "humanitarian focused charity" that lends money to just causes to promote public health, safety, and sustainability. They have asked for a model to help make efficient and meaningful investments by testing whether their past investments have proven fruitful or sour. 

## Purpose
We are tasked to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup. 

---

# Results 
## Original Model
![Original model code](/Resources/original_model_code.png)
*Original model code*

In the original model code, both columns **"EIN" and "NAME" are dropped** in the clean up phase. "APPLICATION_STATUS" and "CLASSIFICATION" are binned to minimize the amount of rare values in the final model. After preprocessing, the data is split into feature and target arrays **with the binary column "IS_SUCCESSFUL" being the target column and the remaining columns as features.** The data is split into testing and training data, it is scaled, and fit into a model with **two hidden layers and one output layer.** **20 nodes are used in the first layer, with 5 nodes in the second layer, and 1 in the output layer.** **(RELU) and (SIGMOID) models are used.** The model is then compiled before a callback checkpoint is made and the model is trained. 

![Original trained model code](/Resources/original_trained_model_code.png)
*Original trained model code*

The model was run for 100 Epochs.

![Original accuracy loss results](/Resources/original_accuracy_loss.png)
*Original accuracy and loss results*

The original model had 75.28011798858643% loss and 53.43440175056458% accuracy. This model has poor performance whether that be for the input data values, number of hidden layers, or number of neurons in those layers. 

![Original accuracy history](/Resources/original_accuracy_history.png)
*Original accuracy history*

This is a graphic depiction of the accuracy history throughout the Epoch sessions.

![Original loss history](/Resources/original_loss_history.png)
*Original loss history*

This is a graphic depiction of the loss history throughout the Epoch sessions.

## Optimization Attempt #1 
In the first attempt to optimize the original model code, columns **"EIN", "NAME", "SPECIAL_CONSIDERATIONS", and "STATUS" are dropped** in the clean up phase. "SPECIAL_CONSIDERATIONS" and "STATUS" are both columns with binary (Yes or No) values. I was curious to see if removing these binary values would effect the accuracy of the model.  "APPLICATION_STATUS" and "CLASSIFICATION" are binned to minimize the amount of rare values in the final model. After preprocessing, the data is split, scaled, fit, and trained just as the original model was before. 

![t1 model code](/Resources/t1_trained_model_code.png)
*Test 1 trained model code*

The model was run for 25 Epochs due to the model hitting minimal loss and peak accuracy within very few Epoch runs.

![t1 accuracy loss results](/Resources/t1_accuracy_loss.png)
*Test 1 accuracy and loss results*

The original model had 76.70705914497375% loss and 51.31195187568665% accuracy. This model has poor performance whether that be for the input data values, number of hidden layers, or number of neurons in those layers. 

This is a graphic depiction of the accuracy and loss history throughout the Epoch sessions looked very similar to the original model.

## Optimization Attempt #2 
In the second attempt to optimize the original model code, column **"EIN" was dropped** in the clean up phase. I decided to **keep "NAME" and bin the values together** instead of dropping the column as it seems some companies apply for investment funding repeatedly. I binned names that appeared less than 10 times into an "Other" variable.  "APPLICATION_STATUS" and "CLASSIFICATION" are binned to minimize the amount of rare values in the final model. After preprocessing, the data is split, scaled, fit, and trained just as the original model was before. 

The model was run for **25** Epochs due to the model hitting minimal loss and peak accuracy within very few Epoch runs.

![t2 accuracy loss results](/Resources/t2_accuracy_loss.png)
*Test 2 accuracy and loss results*

The second optimization attempt model had 54.37097549438477% loss and 76.25656127929688% accuracy. This model has satisfactory performance. However, it is to note that accuracy at one point peaks high, and then returns to an average similar to the original average (53.17%).

![t2 accuracy history](/Resources/t2_accuracy_history.png)
*Test 2 accuracy history*

This is a graphic depiction of the accuracy history throughout the Epoch sessions.

## Optimization Attempt #3 
In the third attempt to optimize the original model code, column **"EIN" was dropped** in the clean up phase. I **keep "NAME" and bin the values together** as it seems some companies apply for investment funding repeatedly. **I binned names that appeared less than 5 times** into an "Other" variable.  "APPLICATION_STATUS" and "CLASSIFICATION" are binned to minimize the amount of rare values in the final model. After preprocessing, the data is split, scaled, fit, and trained just as the original model was before. **However, there is an additional hidden layer and nodes are changed to 12, 8 & 6 from 20 & 5. **

The model was run for **200** Epochs to see if any additional flattening would occur.

![t3 accuracy loss results](/Resources/t3_accuracy_loss.png)
*Test 3 accuracy and loss results*

The third optimization attempt model had 69.18411254882812% loss and 53.55101823806763% accuracy. This model has poor performance. 

---

# Summary
In short, the second optimization attempt was the most successful. I had one additional hidden layer, making the first layer have 20 nodes and the second layer have 5 nodes. I binned "NAME", "APPLICATION_STATUS", and "CLASSIFICATION" to ensure rare values were grouped efficiently. It seemed that grouping "NAME" together had the greatest impact, which means that experience, knowledge of the process, past success, or some other related factor may have some component in a company's success after landing investment funding. 

Additional layers and changing of the nodes did not have positive impacts on the model's performance. 

After viewing the results of the model and my manually created optimizations, I would recommend using an automated optimized such as the keras-tuner package. The keras-tuner package would optimally select which activation function to use, how many neurons would be in the first hidden layer, and the number of subsequent hidden layers as well as the neurons within those layers. 

After creating a keras-tuner optimization function and running the training data through the tuning model, it can return the best hyperparameters and best models to use based on the parameters set in the function. We could then run the testing data against the best models to receive a model with high accuracy and low loss. It would be possible to store and rerun the model after this process. 

We would need to be wary of overfitting based on training data, but dilligence and attention can help gaurd against this possibility. This method would also not help with the preparation of the input data, meaning there are some data points that could be excluded to make a more efficienct model.
