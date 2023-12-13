# Relative Strength Expert Advisor

## Description
The Relative Strength Expert Advisor is a trading algorithm that uses the Relative Strength Index (RSI) indicator to identify overbought and oversold conditions in the market. When the RSI value goes above a certain threshold, it triggers a sell trade, and when it goes below a certain threshold, it triggers a buy trade.

## Usage
To use this Expert Advisor, follow these steps:
1. Include the necessary libraries: Trade.mqh and Indicators.mqh.
```c++
#include <Trade\Trade.mqh>
#include <Indicators\Indicators.mqh>
```
2. Define the required constants. In this code, the symbol is set to 'EURUSD', the period is set to M5, and the RSI period is set to 14. The overbought level is set to 70, and the oversold level is set to 30.
```c++
#define SYMBOL 'EURUSD'
#define PERIOD_PERIOD_CURRENT 0
#define PERIOD_M5 5
#define RSI_PERIOD 14
#define RSI_OVERBOUGHT_LEVEL 70
#define RSI_OVERSOLD_LEVEL 30
```
3. Initialize the Expert Advisor by implementing the OnInit() function. This function sets the necessary indicator parameters, subscribes to the symbol and timeframe, and prints the Expert name and version.
```c++
int OnInit()
{
    // Set necessary indicator parameters
    IndicatorSetInteger(INDICATOR_DIGITS, 5);
    IndicatorSetString(INDICATOR_SHORTNAME, 'RSI');

    // Subscribe to necessary symbol and timeframe
    SymbolSelect(SYMBOL, true);
    PeriodSelect(PERIOD_M5);

    // Print expert name and version
    Print('Expert: Relative Strength');
    Print('Version: 1.0');

    return(INIT_SUCCEEDED);
}
```
4. Implement the OnDeinit() function to unsubscribe from the symbol when the Expert Advisor is stopped.
```c++
void OnDeinit(const int reason)
{
    // Unsubscribe from symbol
    SymbolSelect(SYMBOL, false);
}
```
5. In the OnTick() function, calculate the RSI value based on average gains using the iRSI() function. Then, check if the RSI is above the overbought level or below the oversold level. If it is, execute the corresponding trade by calling the Buy() or Sell() function.
```c++
void OnTick()
{
    // Calculate RSI based on average gains
    double rsi = iRSI(SYMBOL, PERIOD_PERIOD_CURRENT, RSI_PERIOD, PRICE_CLOSE, MODE_PLUSDI);

    // Check if RSI is overbought or oversold
    if (rsi > RSI_OVERBOUGHT_LEVEL)
    {
        // Execute sell trade
        Sell();
    }
    else if (rsi < RSI_OVERSOLD_LEVEL)
    {
        // Execute buy trade
        Buy();
    }
}
```
6. Implement the Buy() function to open a buy trade. Set the lot size, stop loss, and take profit levels. Then, use the OrderSend() function to execute the trade.
```c++
void Buy()
{
    double lotSize = 0.01; // Set lot size
    double stopLoss = 50; // Set stop loss in pips
    double takeProfit = 100; // Set take profit in pips

    // Open buy trade
    OrderSend(SYMBOL, OP_BUY, lotSize, Ask, 0, Ask - stopLoss * _Point, Ask + takeProfit * _Point);
}
```
7. Implement the Sell() function to open a sell trade. Set the lot size, stop loss, and take profit levels. Then, use the OrderSend() function to execute the trade.
```c++
void Sell()
{
    double lotSize = 0.01; // Set lot size
    double stopLoss = 50; // Set stop loss in pips
    double takeProfit = 100; // Set take profit in pips

    // Open sell trade
    OrderSend(SYMBOL, OP_SELL, lotSize, Bid, 0, Bid + stopLoss * _Point, Bid - takeProfit * _Point);
}
```

## Product Description
The Relative Strength Expert Advisor is a powerful trading tool developed by Forex Robot Easy Team. This Expert Advisor utilizes the popular Relative Strength Index (RSI) indicator to identify potential trading opportunities in the Forex market.

The RSI is a momentum oscillator that measures the speed and change of price movements. It provides valuable insights into overbought and oversold conditions, helping traders make informed trading decisions.

With the Relative Strength Expert Advisor, you can automate your trading strategy based on RSI signals. The Expert Advisor continuously monitors the RSI value and executes trades when the RSI reaches predefined levels. It automatically opens sell trades when the RSI is overbought and buy trades when the RSI is oversold.

Key Features:
- Automated trading based on RSI signals
- Customizable RSI period, overbought level, and oversold level
- Adjustable lot size, stop loss, and take profit levels
- Works on the popular EURUSD currency pair
- Designed for the M5 timeframe

By using the Relative Strength Expert Advisor, you can take advantage of RSI signals without the need for manual analysis and execution. It saves you time and effort, allowing you to focus on other aspects of your trading strategy.

Please note that ForexRobotEasy is not the official developer of this product. We are providing this code as a sample that demonstrates how the Relative Strength Expert Advisor can work. For detailed reviews and trading results of this product, please visit [Forex Robot Review - Relative Strength Forex Software](https://forexroboteasy.com/forex-robot-review/relative-strength-forex-software-ichimoku-cloud-review/).

To find the official developer of this product and obtain the complete and updated version, please visit the MQL5 website.

Disclaimer: Trading the Forex market involves risks, and past performance is not indicative of future results. Always use caution and consult with a qualified financial advisor before making any investment decisions.
