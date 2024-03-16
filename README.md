# SigmaWedge
**Hackathon**

  
_First task_ given was to explore the Quantrocket platform and getfamiliar with the platform. And We were asked to pull the data of Apple Stock for a specified date.

<img width="219" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/81d63f3b-a387-454f-94f5-5f28bd2ebf35">


_Second task_ given was to find the states based on the returns. This was done using _**pct_change function**_. Using the returns we classified into three states 1.Bull(+1) 2.Flat(0) 3.Bear(-1)


<img width="207" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/cafca109-78dc-43a8-8acd-a4a9f7e75401">


Considering a markov chain with states Bull, Bear, Flat. I found the transition probability between the states.

<img width="216" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/e616578a-73f8-4c13-a948-e79bad85650b">

After finding the transition probabilities between the states I found the probability distibution for next state.

<img width="569" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/fc006ec5-dd05-4f50-8152-7ee44d4fbdfe">

Using the given conditions

<img width="332" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/dc574954-3794-4337-94cf-08d393f6f1df">

The final porfolio value obtained was 


<img width="208" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/baf9fbc2-0641-437a-98b9-ddea43d38677">

**Since the Actual Array is large. I am not able to show the all the elements 3 is the final portfolio value.**

## Visualization
To visualize I have used **Matplotlib**

<img width="350" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/0e1643c7-825c-42c0-bffe-6e4da3009eb0">


### Monte Carlo Simulation
It is a versatile and widely used technique that provides valuable insights into the behavior of complex systems, helps in decision-making under uncertainty, and supports the optimization of various processes and designs.We know that the rate of change of stock is very complex. To model problems which involve uncertainity we use **Monte Carlo Simulation**.

<img width="350" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/50155371-38df-412c-9429-7062ca6f0454">

 Monte Carlo simulation helps investors assess the risk associated with their investment decisions. It  helps investors make more informed investment decisions by providing a probabilistic framework for evaluating the potential outcomes of their investment strategies.


 ## Time Series Model
 _Libraries Used statmodels, pandas and numpy_
 ### ARIMA Model
The Autoregressive Integrated Moving Average (ARIMA) model is a popular time series analysis technique used to forecast future values based on past observations. It's particularly useful for modeling and forecasting stock prices, as stock prices typically exhibit time-dependent patterns and fluctuations.


<img width="500" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/1d69b51e-8b8b-4646-b755-08c0046d137c">

### SARIMA Model
The Seasonal Autoregressive Integrated Moving Average (SARIMA) model is an extension of the ARIMA model that incorporates seasonality into the time series analysis. SARIMA is particularly useful for modeling and forecasting time series data that exhibit both trend and seasonal patterns, such as quarterly or monthly data, including stock prices affected by seasonal trends.

<img width="500" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/a99e5028-f8c3-4a6d-8278-0d5290a504e9">

Apart from using **Quantrocket**. I have used yahoo finance also popularly known as yfinance to find visualize and  find the transition probability values.
From the platform we had only access close prices. From yfinance I was able to take the adjusted close price values which might help us calculate the returns and performence accurately.

**Close Price**
The price at which a particular stock traded at the end of a given trading session.It represents the last transaction price of the asset for that trading day.

**Adjusted Close Price**
The "Adjusted Close" price is similar to the close price but has been adjusted to reflect any corporate actions that occurred after the market closed. Common corporate actions that can affect the adjusted close price include _dividends, stock splits, rights offerings, and mergers/acquisitions_.
_**Adjusted close prices are often used to calculate returns and performance metrics over time accurately.**_

### Accessing Data Using Yfinance
<img width="428" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/c437e9ff-2514-451d-baef-5fed858a1cc0">


### Using the Adjusted Close Prices the Transition probability obtained was 
<img width="879" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/f2d8be51-66c6-4e63-a500-08bcba471415">

### Plotting Low vs High Price
<img width="350" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/0e49c498-f593-4003-b3c0-f1f1b0a27f06">

Similarly I plotted for both adjusted and Close Price.(Refer aapl_yfinance.ipynb)

### Monte Carlo Simulation 
**No of simulation in both the cases was 1000**
<img width="516" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/776a91df-642d-4277-b2dc-11fee2e50b86">



_All the plots in the above(yfinance) were calculated with regard to the adjusted close price._

Thank You for reading until the end :)


This was written by Bharathi Shankar J (21pd04).


















 

 


 














