# Deepfake-Duel-Truth-vs-Trickery by Code Crafters

The description aims our approach for solving the tasks on classification using transfer Learning.

**Accuracy**

=>**99.93%** on validation dataset in one epoch- Accuracy for labels-predicting classes: Animals, Human faces, vehicles.

=>Accuracy for predicting fake vs Real

![image](https://github.com/user-attachments/assets/1d43cfc6-164f-49d1-850c-53e0a92315c5)

REF img- https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.analyticssteps.com%2Fblogs%2Fhow-transfer-learning-done-neural-networks-and-convolutional-neural-networks&psig=AOvVaw1sWy1gSb1Lwj8Oe3cSaDY4&ust=1744627645534000&source=images&cd=vfe&opi=89978449&ved=0CAMQjB1qFwoTCKCS8oDr1IwDFQAAAAAdAAAAABAE

Inner layers are kept frozen and the upper layers are trainable. 

**Approach**

We used two separate models for training. One for training classes and another to train deep or fake.

1)We used the **transfer learning** approach for model training. We used the Xception(for the classification of Animals, Human faces, vehicles) and VGG-16 (for classification of Deep vs Fake) model from Keras.

![image](https://github.com/user-attachments/assets/d50d55ec-28fd-4cce-8095-cd67eaa6ee69)

2)Freeze the weights and keep model.trainable=False. We included top layers, which were the trainable layers

3)Preprocessed images. For this, we used preprocess_input from keras.Xception

4) Used flow_from_directory and augmentation for training from keras which creates the image on flow without requiring extra storage. This helped to generalize the model well. Because of this we get good accuracy on both train and validation.

**Augmentation**

![image](https://github.com/user-attachments/assets/35582ea3-3ed0-43cf-ad26-d653ba1494b2)

**Model Summary**

1) Xception

![image](https://github.com/user-attachments/assets/d264366b-9466-439e-8381-5a763892e61e)

REF image- https://www.researchgate.net/figure/Proposed-structure-of-Xception-network-used-within-each-stream-of-CNN_fig2_355098045

-Total params: 21,912,107

-Trainable params: 1,050,627 (only in custom head)  

-Non-trainable params: 20,861,480 (frozen Xception using learned weights from Imagenet).

2) VGG-16

![image](https://github.com/user-attachments/assets/5e49d437-05da-4a07-9c55-1578b16b828b)

REF image- https://medium.com/@mygreatlearning/everything-you-need-to-know-about-vgg16-7315defb5918

-Total params: 70,297,410 

-Trainable params: 55,582,722 (only in custom head) 

-Non-trainable params: 14,714,688 (frozen Xception using learned weights from Imagenet)

**Hyperparameters**

Batch size-512

Learning Rate- 0.001

Activation- RELU

Activation Last Layer- Softmax

Optimiser- Adam

Callbacks and earlystoppings of 6 used

**Augmentation for generalising the model**

rotation_range=30, 

vertical_flip=True,

horizontal_flip=True,

width_shift_range=0.1,  

height_shift_range=0.1,

shear_range=0.1,

zoom_range=0.3,  

brightness_range=[0.3, 1.7]

**Difficulties faced**

The dataset was very large. It took hours to train the model. We also cannot keep the learning rate that much small(our learning rate was 0.001). Even the batch size was 512. Keeping the batch size large as 1024 was giving an error of OOM(Out of memory). 

For predicting deep vs fake, it was very difficult as the images were indistinguishable even with the naked eye.

We trained on Google Colab because we were facing errors on Kaggle. Our loss function was getting to infinite during training. 

On colab, the time is very limited, so we used two different accounts for two sub-tasks i.e, predicting fake vs real and predicting the three classes.

**Learnings**

We understood the working of CNN architecture and how to use the concept of transfer learning. We also learned about augmentation. This we learned during our Computer Vision class. It was challenging but we had a lot of fun doing this task.

**Future works**

To explore more CNN architecture for predicting deep vs fake images. Will also look into any preprocessing step helps or not. We were not able to look at the more approaches and research paper because of shortage of time and computational limitations.





