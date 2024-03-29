## Purpose

AutoKeras is a framework which automatically creates a neural network topology,
given only the dataset.


## Results MNIST

```
time python3 mnist_example.py
Using TensorFlow backend.

Initializing search.
Initialization finished.


+----------------------------------------------+
|               Training model 0               |
+----------------------------------------------+
Using TensorFlow backend.

No loss decrease after 5 epochs.


Saving model.
+--------------------------------------------------------------------------+
|        Model ID        |          Loss          |      Metric Value      |
+--------------------------------------------------------------------------+
|           0            |   1.4756227307021619   |         0.9904         |
+--------------------------------------------------------------------------+
/usr/lib/python3.6/multiprocessing/semaphore_tracker.py:143: UserWarning: semaphore_tracker: There appear to be 1 leaked semaphores to clean up at shutdown
  len(cache))


+----------------------------------------------+
|               Training model 1               |
+----------------------------------------------+
/home/moose/.local/lib/python3.6/site-packages/autokeras/bayesian.py:151: UserWarning: Predicted variances smaller than 0. Setting those variances to 0.
  warnings.warn("Predicted variances smaller than 0. "
Using TensorFlow backend.

No loss decrease after 5 epochs.


+--------------------------------------------------------------------------+
|    Father Model ID     |                 Added Operation                 |
+--------------------------------------------------------------------------+
|           0            |           ('to_add_skip_model', 1, 5)           |
+--------------------------------------------------------------------------+

Saving model.
+--------------------------------------------------------------------------+
|        Model ID        |          Loss          |      Metric Value      |
+--------------------------------------------------------------------------+
|           1            |   1.5098872095346452   |        0.99192         |
+--------------------------------------------------------------------------+
/usr/lib/python3.6/multiprocessing/semaphore_tracker.py:143: UserWarning: semaphore_tracker: There appear to be 1 leaked semaphores to clean up at shutdown
  len(cache))

Loading and training the best model recorded from the search.

No loss decrease after 30 epochs.

99.39

real    11255,74s
user    7872,08s
sys    3510,83s
```


## Result HASY


.8419844632768362:  98%|███████▊| 1160/1182 [09:19<0Epoch-10, Current Metric - 0.8419844632768362:  99%|███████▉| 1170/1182 [09:23<0Epoch-10, Current Metric - 0.8419844632768362: 100%|███████▉| 1180/1182 [09:28<0Epoch-10, Current Metric - 0.8419844632768362: 1190 batch [09:33,  2.05 batch/s]2018-11-12 08:31:56.549838: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA
Traceback (most recent call last):
  File "main.py", line 52, in <module>
    print("\n%s: %.2f%%" % (model.metrics_names[1], scores[1] * 100))
AttributeError: 'ImageClassifier' object has no attribute 'metrics_names'

real    56213,36s
user    38999,59s
sys    18253,24s
 ✘ moose@pc07  ~/GitHub/algorithms/ML/50-mlps/04-autokeras   master ●  python3 evaluate_main.py
Using TensorFlow backend.
2018-11-12 23:45:13.984031: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA
/home/moose/.local/lib/python3.6/site-packages/keras/engine/saving.py:269: UserWarning: No training configuration found in save file: the model was *not* compiled. Compile it manually.
  warnings.warn('No training configuration found in save file: '
__________________________________________________________________________________________________
Layer (type)                    Output Shape         Param #     Connected to
==================================================================================================
input_1 (InputLayer)            (None, 32, 32, 1)    0
__________________________________________________________________________________________________
activation_1 (Activation)       (None, 32, 32, 1)    0           input_1[0][0]
__________________________________________________________________________________________________
conv2d_1 (Conv2D)               (None, 32, 32, 64)   640         activation_1[0][0]
__________________________________________________________________________________________________
batch_normalization_1 (BatchNor (None, 32, 32, 64)   256         conv2d_1[0][0]
__________________________________________________________________________________________________
activation_6 (Activation)       (None, 32, 32, 64)   0           batch_normalization_1[0][0]
__________________________________________________________________________________________________
conv2d_5 (Conv2D)               (None, 32, 32, 64)   36928       activation_6[0][0]
__________________________________________________________________________________________________
batch_normalization_5 (BatchNor (None, 32, 32, 64)   256         conv2d_5[0][0]
__________________________________________________________________________________________________
activation_5 (Activation)       (None, 32, 32, 64)   0           batch_normalization_5[0][0]
__________________________________________________________________________________________________
activation_9 (Activation)       (None, 32, 32, 64)   0           batch_normalization_1[0][0]
__________________________________________________________________________________________________
conv2d_4 (Conv2D)               (None, 32, 32, 64)   36928       activation_5[0][0]
__________________________________________________________________________________________________
conv2d_8 (Conv2D)               (None, 32, 32, 64)   4160        activation_9[0][0]
__________________________________________________________________________________________________
batch_normalization_4 (BatchNor (None, 32, 32, 64)   256         conv2d_4[0][0]
__________________________________________________________________________________________________
batch_normalization_8 (BatchNor (None, 32, 32, 64)   256         conv2d_8[0][0]
__________________________________________________________________________________________________
add_1 (Add)                     (None, 32, 32, 64)   0           batch_normalization_4[0][0]
                                                                 batch_normalization_8[0][0]
__________________________________________________________________________________________________
max_pooling2d_1 (MaxPooling2D)  (None, 16, 16, 64)   0           add_1[0][0]
__________________________________________________________________________________________________
activation_2 (Activation)       (None, 16, 16, 64)   0           max_pooling2d_1[0][0]
__________________________________________________________________________________________________
conv2d_2 (Conv2D)               (None, 16, 16, 64)   36928       activation_2[0][0]
__________________________________________________________________________________________________
batch_normalization_2 (BatchNor (None, 16, 16, 64)   256         conv2d_2[0][0]
__________________________________________________________________________________________________
activation_12 (Activation)      (None, 16, 16, 64)   0           batch_normalization_2[0][0]
__________________________________________________________________________________________________
conv2d_11 (Conv2D)              (None, 16, 16, 64)   36928       activation_12[0][0]
__________________________________________________________________________________________________
batch_normalization_11 (BatchNo (None, 16, 16, 64)   256         conv2d_11[0][0]
__________________________________________________________________________________________________
concatenate_1 (Concatenate)     (None, 16, 16, 128)  0           batch_normalization_11[0][0]
                                                                 batch_normalization_2[0][0]
__________________________________________________________________________________________________
activation_13 (Activation)      (None, 16, 16, 128)  0           concatenate_1[0][0]
__________________________________________________________________________________________________
conv2d_12 (Conv2D)              (None, 16, 16, 64)   8256        activation_13[0][0]
__________________________________________________________________________________________________
batch_normalization_12 (BatchNo (None, 16, 16, 64)   256         conv2d_12[0][0]
__________________________________________________________________________________________________
max_pooling2d_4 (MaxPooling2D)  (None, 16, 16, 64)   0           batch_normalization_4[0][0]
__________________________________________________________________________________________________
activation_7 (Activation)       (None, 16, 16, 64)   0           batch_normalization_12[0][0]
__________________________________________________________________________________________________
activation_10 (Activation)      (None, 16, 16, 64)   0           max_pooling2d_4[0][0]
__________________________________________________________________________________________________
conv2d_6 (Conv2D)               (None, 16, 16, 128)  73856       activation_7[0][0]
__________________________________________________________________________________________________
conv2d_9 (Conv2D)               (None, 16, 16, 128)  8320        activation_10[0][0]
__________________________________________________________________________________________________
batch_normalization_6 (BatchNor (None, 16, 16, 128)  512         conv2d_6[0][0]
__________________________________________________________________________________________________
batch_normalization_9 (BatchNor (None, 16, 16, 128)  512         conv2d_9[0][0]
__________________________________________________________________________________________________
add_2 (Add)                     (None, 16, 16, 128)  0           batch_normalization_6[0][0]
                                                                 batch_normalization_9[0][0]
__________________________________________________________________________________________________
max_pooling2d_2 (MaxPooling2D)  (None, 8, 8, 128)    0           add_2[0][0]
__________________________________________________________________________________________________
activation_3 (Activation)       (None, 8, 8, 128)    0           max_pooling2d_2[0][0]
__________________________________________________________________________________________________
conv2d_3 (Conv2D)               (None, 8, 8, 64)     73792       activation_3[0][0]
__________________________________________________________________________________________________
batch_normalization_3 (BatchNor (None, 8, 8, 64)     256         conv2d_3[0][0]
__________________________________________________________________________________________________
max_pooling2d_5 (MaxPooling2D)  (None, 8, 8, 128)    0           batch_normalization_6[0][0]
__________________________________________________________________________________________________
activation_8 (Activation)       (None, 8, 8, 64)     0           batch_normalization_3[0][0]
__________________________________________________________________________________________________
activation_11 (Activation)      (None, 8, 8, 128)    0           max_pooling2d_5[0][0]
__________________________________________________________________________________________________
conv2d_7 (Conv2D)               (None, 8, 8, 64)     36928       activation_8[0][0]
__________________________________________________________________________________________________
conv2d_10 (Conv2D)              (None, 8, 8, 64)     8256        activation_11[0][0]
__________________________________________________________________________________________________
batch_normalization_7 (BatchNor (None, 8, 8, 64)     256         conv2d_7[0][0]
__________________________________________________________________________________________________
batch_normalization_10 (BatchNo (None, 8, 8, 64)     256         conv2d_10[0][0]
__________________________________________________________________________________________________
add_3 (Add)                     (None, 8, 8, 64)     0           batch_normalization_7[0][0]
                                                                 batch_normalization_10[0][0]
__________________________________________________________________________________________________
max_pooling2d_3 (MaxPooling2D)  (None, 4, 4, 64)     0           add_3[0][0]
__________________________________________________________________________________________________
flatten_1 (Flatten)             (None, 1024)         0           max_pooling2d_3[0][0]
__________________________________________________________________________________________________
dropout_1 (Dropout)             (None, 1024)         0           flatten_1[0][0]
__________________________________________________________________________________________________
dense_1 (Dense)                 (None, 64)           65600       dropout_1[0][0]
__________________________________________________________________________________________________
activation_4 (Activation)       (None, 64)           0           dense_1[0][0]
__________________________________________________________________________________________________
dense_2 (Dense)                 (None, 369)          23985       activation_4[0][0]
==================================================================================================
Total params: 455,089
Trainable params: 453,297
Non-trainable params: 1,792
__________________________________________________________________________________________________
None
16992/16992 [==============================] - 77s 5ms/step

acc: 0.28%
