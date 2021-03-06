# Computational_Intelligence_In_Finance

Trend Indicators

Computational Intelligence in Business, Economics andFinance Assignment

Optimising trading strategies based ontechnical analysisDeliverables:zip file with project and other files on results, summary statistics, and presentation(project can be in Java or another language of your preference; you can use BlueJ or any other IDE you like)

Deadline:23:55 on Wednesday, December 15 2021 (Week 20)

Your  task  is  to  implement  a  Genetic  Algorithm  (GA)  to  optimise  a  trading  strategy  basedon technical indicators. You will need to first calculate the value of differenttechnical indicators andtrading signals. Then, you willuse a GA to combine their recommendations (BUY, HOLD and SELL signals)to createatrading strategy.For  this assessment,  you  should  use  the  Unilever.csv  fileas  the  source  of  prices βavailable  on Moodle.Part A: Implementing technical indicators and trading signalsFor this part, update the Unilever.csv file to include the information of technical indicators and trading signals.Task 1: Technical Indicators (10%)Task 1aThe Exponential MovingAverage (EMA) is a type of moving average that puts more emphasis on recent price data, while the standard moving average uses the same weight for all prices observations. 

The formula to calculate the EMA is given below:πΈππ΄(πΏ,π‘)=*π!β-π ππππ‘βπππ1+πΏ78+*πΈππ΄(πΏ,π‘β1)β-1βπ ππππ‘βπππ1+πΏ78

where π!is the priceat the day 

π‘, πΏis the period length (number ofdays)and the

 π ππππ‘βπππfactor is equal to 2.

 In other words, the EMA for the π‘-th day is the price at π‘multiplied by the smoothing term plus the EMA value of the previous day (π‘β1) multiplied by the smoothing term. To calculate the EMA for the first day after the interval πΏ(e.g., EMA at the 12thday for an 12-dayinterval), we use the value of the Simple Moving Average (SMA) as the EMA:πππ΄(πΏ,π‘)=βπ!"#$#%&πΏ

For example, if we are interested in calculating the 12-dayEMA, we will first calculate the 12-day SMA as the EMA on the 12thday; then use this value to calculate the EMA for the 13thday and so forth.Using the formulation above, calculate the 12-day and 26-day EMA. 

Task 1b Calculate the 24-daytrade break out rule (TBR), given theformula below.ππ΅π(πΏ,π‘)=π!βmax{π!"&,...,π!"$}max{π!"&,...,π!"$}where π!is  the  priceat  the  day π‘, πΏis  the  period  length  (24  days),  and  max{...}  returnsthe maximum price observed in the days{π‘β1, ..., π‘βπΏ} βi.e., the highest price in the 24 past days.Task 1cCalculate the 29-dayvolatility (VOL), given the formula below.πππ(πΏ,π‘)=π(π!"&,...,π!"$)πππ΄(πΏ,π‘)where πis the standard deviation for the prices in the given range, π!is the priceat theday π‘and πΏis the period length (29 days).Task 1dCalculate the 25-daymomentum (MOM), give the formula below.πππ(π₯,π‘)=π!βπ!"'where π!is the priceat the day π‘and π!"'is the priceat previousπ₯-th day(e.g., price at the π‘βπ₯day).Task 2: Trading signals (10%)Task 2aUse the two EMA indicators from above to generate buy and sell signals. For each indicator entry, you should compare 12-day EMA to 26-day EMA, and generate signals in the following manner:If12-day EMA>26-day EMA=>1 (buy)If12-day EMA<26-day EMA=>2(sell)If12-day EMA=26-day EMA=>0(hold)

Task 2bUse the TBR indicator above to generate signals in the following manner:If24-day TBR>β0.02 =>2 (sell)If24-day TBR<β0.02 =>1 (buy)If24-day TBR=β0.02 =>0 (hold)Task 2cUse the VOLindicator above to generate signals in the following manner:If29-day VOL>0.02 =>1 (buy)If29-day VOL<0.02 =>2 (sell)If29-day VOL=0.02 =>0 (hold)Task 2dUse the MOMindicator above to generate signals in the following manner:If25-day MOM>0 =>1 (buy)If25-day MOM<0 =>2 (sell)If25-day MOM=0 =>0 (hold)PART B: Genetic AlgorithmTask 1 (40%)Use  a  GA  to  combine  the  output  of  the  trading  signals  from  Task  2aβ2d.  For example,  the indicator may generate the following signals:Task 2a => BUYTask 2b => BUYTask 2c => HOLDTask 2d => SELLIn this case, you could choose to BUY since the majority of trading signals are recommending this action. We say that all signals have the same weight in this case.Your  task  is  to  implement  a  GA  to  evolve  a  set  of  weights  (one  for  each  trading  signal)  to determine an optimal trading action. Your individual representation should associate a numeric weight (between 0 and 1) to each trading signal:0.4 x Task 2a => BUY0.2 x Task 2b => BUY0.1 x Task 2c => HOLD0.8 x Task 2d => SELL
