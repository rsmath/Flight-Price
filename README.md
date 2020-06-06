# **FLIGHT PRICE** [![HitCount](http://hits.dwyl.com/ramanshsharma2806/Flight-Price.svg)](http://hits.dwyl.com/ramanshsharma2806/Flight-Price)


### **DESCRIPTION**

---

This is a project I am working on for the **[mia](1)** startup which focusses on making Machine Learning models accessible for the general public with its easy-to-use web interface. People can go to the [http://miamarketplace.com/](http://miamarketplace.com/) and chose a prebuilt model that they wish to use. Inside the model's page, they can chose their values for different parameters and see the specific output on the browser itself within seconds!

### **Motivation**


---

Flight prices are unpredictable. We can see the same airline charging us different prices for the same flight on the same day because of unknown factors. In an effort to mitigate that confusion, I have made a flight price estimator in this project that is trained on data acquired from [this](2) Kaggle dataset.


### **METHODOLOGY**


One of the hardest challenges I faced in this project was dealing with categorical and continuous variables in the same neural network.

*More information upcoming regarding this.*


---


### **NETWORK ARCHITECTURE**

![Network architecture](nn_graph.png?raw=true "network architure")

---

Some hyperparameters that are taking me a long time to manually tune are

+ Learning rate
+ Batch size
+ Embedding size
+ Dense layer size
+ Number of Dense layers
+ Optimizer

As of now, the best combination I have come up with is

```python
learning_rate = 0.1
batch_size = 512

# The best optimizer as of now is Adam
optimizer = Adam(learning_rate=0.1)
model.compile(optimizer=optimizer, loss='mse', metrics=['mse'])

# 20% of training data is used as validation data while training
history = model.fit(
    [train_continuous, train_categorical],
    Y_train,
    batch_size=512,
    epochs=500,
    validation_split=0.2,
    callbacks=[call, training_stop]
)
```

### **RESULTS AND FUTURE WORK**

As of *June 6th, 2020*, the best accuracy I have scored is:

Training set: 54.27%
Test set: 53.52%

with an epsilon price of $70 as the margin.

Below is the graph of the training and validation costs as the model trained in its best scenario.

![costs](costs.png?raw=true "costs")

---


### **LIVE CODE**

---

In this repository, I have presented by code as a Jupyter notebook. But I originally coded in Google colab. I am providing the link to the colab for viewing and making it public.

Link - [https://bit.ly/flightpricemodel](https://bit.ly/flightpricemodel)

### **CONTACT**

---

If you have any concern or suggestion regarding this project, feel free to email me at [sharmar@bxscience.edu](sharmar@bxscience.edu).




[1]: http://miamarketplace.com/
[2]: https://www.kaggle.com/zernach/2018-airplane-flights
