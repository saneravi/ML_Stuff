## Purpose

Check performance if we have a skip connection / more convolutional layers.


## Results

77.42% accuracy is to be beaten.

```
Epoch 00700: val_loss did not improve from 0.80535
16992/16992 [==============================] - 1s 88us/step

acc: 79.31%

real    10976,90s
user    14532,04s
sys    1080,42s
```

and

```
__________________________________________________________________________________________________
Layer (type)                    Output Shape         Param #     Connected to                     
==================================================================================================
input_1 (InputLayer)            (None, 32, 32, 1)    0                                            
__________________________________________________________________________________________________
conv2d_1 (Conv2D)               (None, 32, 32, 16)   160         input_1[0][0]                    
__________________________________________________________________________________________________
max_pooling2d_1 (MaxPooling2D)  (None, 16, 16, 16)   0           conv2d_1[0][0]                   
__________________________________________________________________________________________________
conv2d_2 (Conv2D)               (None, 16, 16, 16)   2320        max_pooling2d_1[0][0]            
__________________________________________________________________________________________________
activation_1 (Activation)       (None, 16, 16, 16)   0           conv2d_2[0][0]                   
__________________________________________________________________________________________________
conv2d_3 (Conv2D)               (None, 16, 16, 16)   2320        activation_1[0][0]               
__________________________________________________________________________________________________
activation_2 (Activation)       (None, 16, 16, 16)   0           conv2d_3[0][0]                   
__________________________________________________________________________________________________
add_1 (Add)                     (None, 16, 16, 16)   0           activation_1[0][0]               
                                                                 activation_2[0][0]               
__________________________________________________________________________________________________
max_pooling2d_2 (MaxPooling2D)  (None, 8, 8, 16)     0           add_1[0][0]                      
__________________________________________________________________________________________________
conv2d_4 (Conv2D)               (None, 8, 8, 16)     2320        max_pooling2d_2[0][0]            
__________________________________________________________________________________________________
activation_3 (Activation)       (None, 8, 8, 16)     0           conv2d_4[0][0]                   
__________________________________________________________________________________________________
conv2d_5 (Conv2D)               (None, 8, 8, 16)     2320        activation_3[0][0]               
__________________________________________________________________________________________________
activation_4 (Activation)       (None, 8, 8, 16)     0           conv2d_5[0][0]                   
__________________________________________________________________________________________________
add_2 (Add)                     (None, 8, 8, 16)     0           activation_3[0][0]               
                                                                 activation_4[0][0]               
__________________________________________________________________________________________________
max_pooling2d_3 (MaxPooling2D)  (None, 4, 4, 16)     0           add_2[0][0]                      
__________________________________________________________________________________________________
conv2d_6 (Conv2D)               (None, 4, 4, 16)     2320        max_pooling2d_3[0][0]            
__________________________________________________________________________________________________
activation_5 (Activation)       (None, 4, 4, 16)     0           conv2d_6[0][0]                   
__________________________________________________________________________________________________
conv2d_7 (Conv2D)               (None, 4, 4, 16)     2320        activation_5[0][0]               
__________________________________________________________________________________________________
activation_6 (Activation)       (None, 4, 4, 16)     0           conv2d_7[0][0]                   
__________________________________________________________________________________________________
add_3 (Add)                     (None, 4, 4, 16)     0           activation_5[0][0]               
                                                                 activation_6[0][0]               
__________________________________________________________________________________________________
flatten_1 (Flatten)             (None, 256)          0           add_3[0][0]                      
__________________________________________________________________________________________________
dense_1 (Dense)                 (None, 512)          131584      flatten_1[0][0]                  
__________________________________________________________________________________________________
activation_7 (Activation)       (None, 512)          0           dense_1[0][0]                    
__________________________________________________________________________________________________
dense_2 (Dense)                 (None, 369)          189297      activation_7[0][0]               
__________________________________________________________________________________________________
activation_8 (Activation)       (None, 369)          0           dense_2[0][0]                    
==================================================================================================
Total params: 334,961
Trainable params: 334,961
Non-trainable params: 0
__________________________________________________________________________________________________
None
16992/16992 [==============================] - 2s 129us/step

acc: 79.53%
```