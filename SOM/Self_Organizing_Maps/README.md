*Self Organising Maps*
---------------------

A self-organizing map (SOM) or self-organizing feature map (SOFM) is a type of artificial neural network (ANN) that is trained using unsupervised learning to produce a low-dimensional (typically two-dimensional), discretized representation of the input space of the training samples, called a map, and is therefore a method to do dimensionality reduction.


Aim of this project is to detect of fraudulant credit card applications by this unsupervised algorithm developed by Giuseppe Vettigli

*MiniSom 1.0*:- https://test.pypi.org/project/MiniSom/


**input params for the minisom:**
            
            x,y - dimensions of the SOM
            
            input_len - number of the elements of the vectors in input
            
            sigma - spread of the neighborhood function (Gaussian), needs to be adequate to the dimensions of the map.
            (at the iteration t we have sigma(t) = sigma / (1 + t/T) where T is #num_iteration/2)
            
            learning_rate - initial learning rate
            (at the iteration t we have learning_rate(t) = learning_rate / (1 + t/T) where T is #num_iteration/2)
            
            decay_function, function that reduces learning_rate and sigma at each iteration
                            default function: lambda x,current_iteration,max_iter: x/(1+current_iteration/max_iter)
            
            random_seed, random seed to use.

Training the SOM on the train data X:
```python
# Training the SOM
from minisom import MiniSom
som = MiniSom(x = 10, y = 10, input_len = 15, sigma = 1.0, learning_rate = 0.5)
som.random_weights_init(X)
som.train_random(data = X, num_iteration = 100)
```

Visualizing Results:
```python
from pylab import bone, pcolor, colorbar, plot, show
bone()
pcolor(som.distance_map().T)
colorbar()
markers = ['o', 's']
colors = ['r', 'g']
for i, x in enumerate(X):
    w = som.winner(x)
    plot(w[0] + 0.5,
         w[1] + 0.5,
         markers[y[i]],
         markeredgecolor = colors[y[i]],
         markerfacecolor = 'None',
         markersize = 10,
         markeredgewidth = 2)
show()
```
![screenshot 68](https://user-images.githubusercontent.com/37619070/51175750-2c36ae00-18e1-11e9-94e8-9b67f729bd7d.png)

In the Map generated, lower the darkness of the region, higher is the chances of the person being fraud in that region.
red circle represents that the person in that region has not got the credit card approval.
green square represents that the person in that region has got the creditcard approval.

We can infer that the two white regions (8,1) and (6,8) are the regions for the outliers i.e., the region of frauds.

Now we can map the regions back to the data and find the frauds


*For more Readings:*
http://sci2s.ugr.es/keel/pdf/algorithm/articulo/1990-Kohonen-PIEEE.pdf
http://www.ai-junkie.com/ann/som/som1.html
