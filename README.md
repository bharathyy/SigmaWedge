# SigmaWedge Hackathon
## Second Round

_Note: This is a updated readme file for the second round_
## Steps Done 
### 1.Defined a MDP for the problem
### 2.Defined Transition Probability
### 3.Compute values based on Bellmans Equation 
### 4.Extracting the Optimal policy for each state
### 5.Applying Q Learning Algorithm 

## What is a MDP ?
MDP also known as Markov Decision Process which is a mathematical structure that is used to model problems where the outcomes are partially random and partially controllable.
Most of the natural event that happens around the world are stochastic. The stock price data are one such case where the outcomes are stochastic.

So, I implemented **Value Based Iteration** which is a dynamic programming algorithm used to find the optimal policy in a Markov Decision Process (MDP). 

According to the problem statement we know that there are three states **Bear(-1), Bull(+1) and Flat(0)**.

For the MDP the we define states, set of possible actions that we can take, rewards and initial transition probability.
In the case of defining initial transition probability I took two case where in one case I considered Uniform distribution and in the other case using the previous stock prices I calculated the transition probability.


<img width="337" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/d771afef-b60d-4e77-aaef-00e0b5cd8456">

So to explain the **reward dictionary** consider that you are **currently in state bear market** and you **sell** your stock and the **market goes to state bull**. This is **inturn a loss for us** so I have defined **our reward as negative that is -5**. Similarly for each and every case I have given positive rewards when my portfolio value tends to increase and negative in the case where it is reduced and zero when there is no change.

I considered discount factor as 0.8 as we value the future rewards more than the present rewards in the case of stocks.


Since Stock prices are stochastic I considered Uniform Distribution for the initial transition probability.
That is for each and every state action pair as 0.33



<img width="798" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/14ac4b0a-8466-4339-a3ee-e58190f0ddb6">

Considering the above I initilized **Value function** for all the states to zero intially.

I considered discount factor as 0.8 as we **value the future rewards more than the present rewards** in the case of stocks.

My tolerance value is small as smaller tolerance will lead to more iterations of the algorithm, potentially resulting in a more **accurate approximation** of the optimal values but requiring more computational resources.


<img width="215" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/fca50f5c-f4ce-4761-b9ff-3477c4e799fc">


SO now comes the iteration 
For each state s in the state space: we Compute the value of each possible action a in state s using the **Bellmans equation**:

<img width="299" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/7b6e95c7-95d6-401c-a117-c227f1c2fcbe">

Q(s,a) is  is the value of taking action a in state s.

T(s,a,s') is the transition probability from state s to state s' under action a .

R(s,a,s') is the immediate reward received after taking action a and getting transitioned to s'.

γ is the discount factor.

V(s') is the value of the next state.


Update the value function V for state s as the maximum value over all possible actions.
V(s)= max Q(s,a)

Repeat the iteration until the change in the value function ΔV is below a predefined threshold.

Once value iteration converges, extract the optimal policy by selecting the action with the highest value for each state:
pi(s)=argmax Q(s,a)

The optimal policy for each state was

<img width="282" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/95bf6eee-8702-4bf4-98aa-4f6229a82cfd">

The final value for each state

<img width="457" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/5502ddc2-0ac1-4b2b-8599-b107047d72b0">


For each iteration I am printing the all the states and optimal action

<img width="334" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/eeb7c689-327c-46d4-a678-edd3fa664ff8">


## Considering the history of appl stock prices for the transition probability

So in the above case I considered uniform distribution that but now Using the data that we pulled from the quantrocket platform .I found the transition probablity.
Using the matrix we perform the same value based iteration and results varied alot.

<img width="252" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/cda6ea70-294c-4f65-86e4-600b5430b41a">

This is the transition probability matrix based on **the history of aapl stock prices**.

<img width="217" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/11717693-611e-46d8-b364-4a878cdbcf67">


This was the optimal policy that  got when I used the initial transition probability calculated from the stock prices that I pulled.




## Q Learning Algorithm

<img width="286" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/64a82e05-c541-400c-8179-7e6be3087901">


Using the above optimal policy that we got from Value Iteration I changed the dimension of the rewards matrix and  define Q table as zero initially. 

For training I started with a random state and taking the action based on epsilon and by Bellamans Equation, I updated the Q table. And the final Q table value obtained was.


<img width="236" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/2118efc1-302b-4cf8-ba53-ac6d0b82df3d">

The Optimal Policy that we got from Q learning was **Similar to the result that we got from Value Iteration**.

<img width="296" alt="image" src="https://github.com/bharathyy/SigmaWedge/assets/89925746/64055ee3-59ab-4869-83fd-f2536f50bde1">

Using the Q table matrix I tried to test on our data. Due to some error the loop kept on running. I was unable to track where my code went wrong.


### References 
https://towardsdatascience.com/reinforcement-learning-an-easy-introduction-to-value-iteration-e4cfe0731fd5
https://medium.com/@ngao7/markov-decision-process-value-iteration-2d161d50a6ff
https://gibberblot.github.io/rl-notes/single-agent/value-iteration.html







### Old Task
  
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


















 

 


 














