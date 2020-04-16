# OptionStrategy
 
Member
--------------
I-Fan Chiang


Install
--------------
 * Install Package:
    ```
    $ pip install py_vollib      
    ```

Description
-------------- 
* To Plot the implied volatility curve. (Implied_Volatility.ipynb)
* To build the option strategies with max payoff and breakeven points. (Option_Greeks.ipynb)
* To Calculate the greek letters of these strategies and plot the payoff. (Option_Greeks.ipynb)

Usage
-------------- 
```python
%run Implied_Volatility.ipynb
%run Option_Greeks.ipynb

d_option1 = {'現貨價格': '11386', '到期日': '20200219', '買賣權': 'Call', '履約價': '11300', 
             '今日': '20200130', '部位': '-1', '結算價': '245.0', 'IV': '0.196352'}
d_option2 = {'現貨價格': '11386', '到期日': '20200219', '買賣權': 'Put', '履約價': '11500', 
             '今日': '20200130', '部位': '-1', '結算價': '265.0', 'IV': '0.179389'}

df_options_strangle = pd.DataFrame([d_option1, d_option2])
opt_strat1 = Options_strategy(df_options_strangle)
greeks_strat1 = opt_strat1.get_greeks()
opt_strat1.describe_portfolio()
```
 ![alt text](https://github.com/A2Zntu/OptionStrategy/blob/master/Graph/Greeks_example.PNG "Greek letters")

```python
print("max Payoff: " , opt_strat1.get_maxPayoff())
opt_strat1.portfolio_payoff(fileName = "Short Strangle")
```
 ![alt text](https://github.com/A2Zntu/OptionStrategy/blob/master/Graph/Short%20Strangle.png "Short Strangle")

Compliment
-------------- 

From the below graph, we could tell that the Call-Put Implied Volatility Spread(CPIV) is almost Positive. 
Implies that, people might be more positive toward the market. 
![alt text](https://github.com/A2Zntu/OptionStrategy/blob/master/Graph/CPIV%20Spread_0130.png "CPIV 0130")

If we expect the market would be bull tomorrow, we could construct a bull spread. 
In this example, we could buy a Call@11300 and Sell a Call@11400. 
![alt text](https://github.com/A2Zntu/OptionStrategy/blob/master/Graph/Bull%20Spread.png "Bull Spread")

Improvement
-------------- 
* The Delta-Netural and Gamma Netrual Strategies are selected subjectively. 
* Could be imporved with some solver like scipy.optimize
