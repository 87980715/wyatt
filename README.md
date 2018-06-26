# [Wyatt](http://18.218.235.32/)
Above is a link to the log output of Wyatt (DEBUG level and higher) running connected to my personal Binance account.

Another link to the full log (all levels) is available [here](http://18.218.235.32/full.php)
### Logic
  * Gather recent data using [Binance-API](https://github.com/binance-exchange/binance-java-api)
  * Use data to find averages for vaious time intervals
  * Predict the next selling price using a few configured percentages
  * When current price is above target sell price, execute sell
  * Then, execute buy back immediately after for a configured percentage below the targeted sell price
  * Once decided, Wyatt sells at the current price not the target sell price
### Building
First clone and build the [Binance-API](https://github.com/binance-exchange/binance-java-api) repository to install the necessary packages into your local Maven repository (it is needed to build Wyatt)
  
To build Wyatt clone this repository and on the same level as pom.xml, execute 
```$xslt
mvn clean install
```
This will build and package two .jar files in the target directory. One of the .jar files end with "-jar-with-dependencies.jar" and includes all the libraries needed for independent execution.
### Executing
To run Wyatt, execute the following
```$xslt
java -jar target/wyatt-<REPLACE_VERSION>-jar-with-dependencies.jar <arg1> <arg2> <arg3> <arg4> <arg5> <arg6>
```
 * arg1 = Binance API Key
 * arg2 = Binance Secret Key
 * arg3 = Twitter OAUTH Consumer Key
 * arg4 = Twitter OAUTH Consumer Secret
 * arg5 = Twitter OAUTH Access Token
 * arg6 = Twitter OAUTH Access Token Secret

The Binance API Key absolutely MUST have approval to execute trades from Binance, but does not need approval to withdraw. 
