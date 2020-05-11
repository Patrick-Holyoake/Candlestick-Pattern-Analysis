# Candlestick-Pattern-Analysis
Here is the source code that I have used to analyse the bullish engulfing candle on the daily timeframe in USDCAD in python.  

    import csv
    with open('OANDA_USDCAD.csv') as f:
        reader = csv.DictReader(f)
        candles = list(reader)
        print(candles)
    
    def is_bearish_candlestick(candles):
        return candles['close'] < candles['open']
    
    def is_bullish_engulfing(candles, index):
        current_day = candles[index]
        previous_day = candles[index-1]
        two_days_prior = candles[index-2]
    
        if is_bearish_candlestick(two_days_prior) \
        and is_bearish_candlestick(previous_day) \
        and current_day['low'] < previous_day['low'] \
        and current_day['close'] > previous_day['high']:
            return True
    
        return False
    
    for i in range(1, len(candles)):
        print (candles[i])
    
        if is_bullish_engulfing(candles, i):
            print("This is a bullish engulfing")
            
     count = 0
       
     def is_bullish_engulfing_next_candle(candles, index):
       three_days_prior = candles[index-3]
       two_days_prior = candles[index-2]
       previous_day = candles[index-1]
       current_day = candles[index]
    
       if is_bearish_candlestick(three_days_prior) \
       and is_bearish_candlestick(two_days_prior) \
       and two_days_prior['low'] > previous_day['low'] \
       and two_days_prior['high'] < previous_day['close'] \
       and current_day['open'] < current_day['close']:
           return True
    
        return False
        
        for i in range(3, len(candles)):
            print(candles[i])
    
            if is_bullish_engulfing_next_candle(candles, i):
                print("The next candle after the bullish engulfing has closed above its open") 
                
        for i in range(1, len(candles)):
    
    
            if is_bullish_engulfing_next_candle(candles, i):
                count += 1

         count
    
         16 / 34

       
        
    
    
    
    
