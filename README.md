# orderbook
Fast high performance Mini orderbook in C++ 11

An orderbook includes all securities that the institution is regularly buys and sells on the stock market. a bid is
the price that an institution is willing to buy and an offer is the price that an institution is willing to sell.

   Orderbook.h -> contains all the methods to insert/delete/update the book
   testOrder.cpp -> main functions that sends orders to insert/update/delete a quote
   Quotes are 5-tuple string containing QuoteID/{B/A}/{N|U|D}/Price/Volume
   
   Keeps the prices in vector for faster access
   
   - Mini Book then sortsthe offers and the bids from the quotes it receives
   - For offer, the best price is the lowest price and for bid, the best price is the highest price
   - The best price is the first price that is displayed
   - If two quotes have the same price, they are then sorted by volume ( form high to low )
   - If two quotes have the same price and volume, they are then ranked by times - most recent to least recent
   - QuoteID: alphanumeric string that uniquely identifies a quote
   - B / A- Bid/Ask
   - N/U/D : whether this is a new quote or an update or delete for a prev received quote. A quote update can either
             volume or price or both. A delete for a quote ide of "0" will delete the entire bok. 0/B/D/0/0 will delete
             the entire bid book and 0/A/D/0/0 will delete the entire offer book.
   - Price price associated with this quote. Max Price is 655.35$ ( Max for uint16_t which is what price array based out of ).
     This can be easily increased to uint32_t for example if your system has enough memory ( Not in my windows pc ).
   - Volume volume associated with this quote
   
   1) Build the order book using the solution csvProject.sln
   2) run Win32Project1.exe, note you can easily change the target name of this exe
