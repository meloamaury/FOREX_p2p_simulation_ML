
================================================================================
        FOREX Marketplace Simulation, Analysis and Predictions
                 --- README / Introduction ----
                Amaury de Melo Souza May - 2016
================================================================================

MOTIVATION: This project simulates a peer-to-peer currency marketplace of two currencies. 
The idea is to have a platform where users in different parts of the world can choose they
own exchange rate to exchange their money, without any bank intermidiating the process.
When the two users agree on a exchange rate between them, a "matching" will occur and the 
transaction will take place.

PLATFORM CHARACTERISTICS: A range of market characteristics, e.g. exchange rate variations,
trade frequency and trade amounts, can be chosen and the impact on the marketplace then studied. 
The first part of the project is dedicated to build the code that creates virtual peer-to-peer
marketplace. The second part is dedicated on exploratory data analysis and feature engineering. 
The last part is to demonstrate how Machine Learning techniques can be used to predict whether
an advertised sale placed on the market will be bought or not, and if so how long it takes
for the sale to occur. Finally, a summary of the project is provided.

================================================================================
         BRIEF EXPLANATION OF THE WORK FLOW AND ASSUMPTIONS MADE 
================================================================================
1) INITIALIZING THE DATA: 
a) Currency exchange rate varies over time: in order to simulate the exchange rate 
varying over time, I assume that the
exchange rate follows a brownian motion type of curve %(see ER_generator.m).
The exchange rate could automatically be obtained from the internet to get
the real time IBR from %http://www.fxstreet.com/rates-charts/forex-rates/.
However, I assume that there is no internet access to run the code.

%b) For every simulated time step, a random number of traders (following a 
%normal distribution) come to the system on both sides of the market. The 
%average of traders can be chosen by USER. The important fact is that, the 
%average will change automatically following the inter-bank exchange rate.
%In other words, if the IBR decreases for the trader in the GPB market,
%there will be a smaller average number of traders coming into the system,
%whereas an increase in the average number of traders in the Euro market 
%would be observed. 

%c) Traders with quicktrader status are also included in the list of
%traders and they are identified with a logical index.

%c) For every trader, there is a random generator (following a uniform dist.)
%for his amount of money on both markets. The mininum allowed is 100 (either
%GBP or Euros) and the maximum allowed is 500000 in multiples of 100.

%3)The initial Euro to Pounds exchange rate is the latest given by the
%european central bank ER(Euro/GBP= 0.77483). Likewise, the exchange rate 
%between Pounds and Euro is ER(GBP/Euro)=1/0.77483=1.2906. 
An outline of the project is shown below, the recommended reading order is

	Part 1: MarketPlace_Simulator.ipynb
		      /Soure_Code.tar (This folder contains all the files need to perform the calculations)
	Part 2: Exploratory_data_analysis.ipynb
	              /Extra_graphics.tar (This folder contains extra graphics in order to explain the matching system implemented in the code.
  
	Part 3: Prediction.ipynb

================================================================================
                      SET OF FILES AND THEIR DESCRIPTION:
================================================================================
All the Mablab and Python files to run the marketplace and ML, respectively, if found in the "Source_Code" Directory. Here is a short description of each file to give an overview of all the generators needed for the marketplace.

ER_generator.m: This function generates the inter-bank rate using a browining motion model.

ER_user.m: This function generates the traders exchange rate for both sides of the market.

Num_users.m: This function generates the number of new traders on both sides of the market.

QuickTrade_gen.m: This function generates randomly generates a logical index for quick-trade 
with a given probability.

Market.m: This function builds the markets for GBP and Euro and calculates the rate available
and the amount of money availabe.

Matching_system.m: This function contains all the conditions considered for matching between
traders on both sides of the market.

TradeLOG_generator.m: This function generates the trade log for all the matching events.
