# The-Array-filter-method
given an array of stocks, select only those with the price larger than a certain value
filter is great when you want to apply test function to every item in array and create a new array with only those that pass the test

Function that demonstrates what the filter method does (a lot code!)

    // 1. create function that accepts an array of stocks and min price
    function getStocksOver(stocks, minPrice){
    // 4. create new array to hold all of results for those stocks larger or equal to min price
    var results = [];
    // 5. call forEach method to call once for each stock in array
    stocks.forEach(function(stock){
    // if stock price is greater than or equal to min price, push into results array
    // notice getStocksOver does not modify, it adds into a new array.
        if (stock.price >= minPrice) {  
        results.push(stock);
      }
    });
        return results;
      }
    // 2. new array of only those stocks that are expensive
    var expensiveStocks = getStocksOver(
      [
      { symbol: "LL", price: 220.22, volume: 24333},
      { symbol: "DIS", price: 155.12, volume: 35253},
      {symbol: "APL", price: 189.54, volume: 88744},
    ],
    190.00);
    // 3. log only expensive stocks to the console
    console.log(JSON.stringify(expensiveStocks));
    
Is there a shorter way? YES!

Use the filter method! how does it work?

    // filter method accepts a function called a "predicate", which accepts a value, returns true or false
    // mimics above
    Array.prototype.filter = function(predicate){
    var results = [];
    // call forEach on this or array, filters method on array, run operation on each item in array 
    this.forEach(function(item) {
      // if true, add to results
      if (predicate(item)) {
        results.push(item);
      }
    });
    return results;
    };
    
Now apply it to previous function to make it shorter

    function getStocksOver(stocks, minPrice){
      // pass in predicate function
        return stocks.filter(function(stock){
      // returns true or false depending on whether or not to keep stock
        return stock.price >= minPrice;
      });
    }
    //  new array of only those stocks that are expensive
    var expensiveStocks = getStocksOver(
    [
      { symbol: "LL", price: 220.22, volume: 24333},
      { symbol: "DIS", price: 155.12, volume: 35253},
      {symbol: "APL", price: 189.54, volume: 88744},
    ],
    190.00);

    // log only expensive stocks to the console
    console.log(JSON.stringify(expensiveStocks));

