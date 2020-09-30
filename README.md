# lab2
1.Обучение нейронной сети с разными темпами обучения

    model = tf.keras.applications.MobileNetV2(
    input_shape=None, alpha=1.0, include_top=True, weights=None,
    input_tensor=None, pooling=None, classes=6, classifier_activation='softmax'
    
а.lr = 0.000001

![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_categorical_accuracy%200.000001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%200.000001.svg)

b.lr = 0.00001
   
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_categorical_accuracy%200.00001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%200.00001.svg)

c.lr = 0.0001

![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_categorical_accuracy%200.0001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%200.0001.svg)

2.Применяем процедуру модификации весов согласно метода градиентного
спуска ко всей нейронной сети

    base_model = tf.keras.applications.MobileNetV2(
                                    include_top=False, 
                                    weights='imagenet')
    global_average_layer =  tf.keras.layers.GlobalAveragePooling2D()     
    prediction_layer =    tf.keras.layers.Dense(6, activation=tf.keras.activations.softmax)
    

    inputs = tf.keras.Input(shape=(224, 224, 3))
    x = base_model(inputs, training=False)
    x = global_average_layer(x)
    x = tf.keras.layers.Dropout(0.2)(x)
    outputs = prediction_layer(x)
    model = tf.keras.Model(inputs, outputs)
    
a.lr = 0.0000001
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_categorical_accuracy%201%200.0000001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%201%200.0000001.svg)
b.lr = 0.000001
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_categorical_accuracy%201%200.000001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%201%200.000001.svg)
c.lr = 0.00001
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_categorical_accuracy%201%200.00001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%201%200.00001.svg)

3.Применяем процедуру модификации весов согласно метода градиентного
спуска только к слоям классификатора и сохраняем сеть

a.lr = 0.0000001
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch__categorical_accuracy%202%200.0000001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%202%200.0000001.svg)
b.lr = 0.000001
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch__categorical_accuracy%202%200.000001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%202%200.000001.svg)
c lr = 0.00001
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch__categorical_accuracy%202%200.000001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%202%200.000001.svg)

4. Применяем процедуру модификации весов согласно метода градиентного
спуска ко всей нейронной сети, предобученной в пункте 4:
a.lr = 0.000001
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_categorical_accuracy%203%200.000001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%203%200.000001.svg)
b.lr = 0.00001
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_categorical_accuracy%203%200.00001.svg)
![Image alt](https://github.com/maggiemmae/lab2/blob/master/epoch_loss%203%200.00001.svg)

