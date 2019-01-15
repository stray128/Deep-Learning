*Prediction of stock trends Using Recurrent Neural Networks*
-----------------------------------------------------------------

Using the stock details of google untill 2016 dec, we predict the stock trends of that in 2017 january month.
Here in this RNN we use LSTM layers in the sequential model from keras with tensorflow backend.

Training the RNN model on training dataset with number of epochs = 100 and batch size = 32
```python
regressor.fit(X_train, y_train, epochs = 100, batch_size = 32)
```
![screenshot 63](https://user-images.githubusercontent.com/37619070/51173670-eb886600-18db-11e9-9262-44b05c1d37f8.png)

Visualizing results
```python
# Visualising the results
plt.plot(real_stock_price, color = 'red', label = 'Real Google Stock Price')
plt.plot(predicted_stock_price, color = 'blue', label = 'Predicted Google Stock Price')
plt.title('Google Stock Price Prediction')
plt.xlabel('Time')
plt.ylabel('Google Stock Price')
plt.legend()
plt.show()
```
![screenshot 65](https://user-images.githubusercontent.com/37619070/51173728-09ee6180-18dc-11e9-9771-203b7e9cae62.png)

As we can see the trends or the momentum of the stock is averagely similar.

Additional Readings:
--------


*-(Movie written by AI algo using RNN's)https://arstechnica.com/gaming/2016/06/an-ai-wrote-this-movie-and-its-strangely-moving/

*-http://www.jmlr.org/proceedings/papers/v28/pascanu13.pdf

*-http://people.idsia.ch/~juergen/lstm2003tutorial.pdf
