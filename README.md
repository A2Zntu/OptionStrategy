# OptionStrategy
 
## Description

Install
--------------
 * Install Package:
    ```
    $ pip install py_vollib      
    ```

Motivation
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

```python
print("max Payoff: " , opt_strat1.get_maxPayoff())
opt_strat1.portfolio_payoff(fileName = "Short Strangle")
```
 ![alt text](https://github.com/A2Zntu/OptionStrategy/blob/master/Graph/Short%20Strangle.png "Short Strangle")



Improvement
-------------- 
* The Delta-Netural and Gamma Netrual Strategies are selected subjectively. 
* Could be imporved with some solver like scipy.optimize
