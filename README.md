# Revenue-Optimizing-in-Energy (US)

Idea of Problem
### Trying to Optimize Revenue for Battery Storage
**Problem**: To calculate TB2 revenue ($) of a 1MW/2MWh BESS with 100% charge/discharge efficiency, you take sum of top 2 priced hours (T2) at any point in the day and the sum of bottom 2 priced hours (B2) at any point in the day and calculate T2 minus B2.

This method does not ensure SOC feasibility as one of the T2 hours may come at a time when you have no energy in the battery or the B2 hours may come at a time when you have a full state of charge and thus no ability to charge.

But TBn Method not ensure SOC% feasability

So have to modified it such that it take care battery charge in mind
**For SOS feasibility**  - Ensure that when battery have no energy it only have one option which is to charge it first. Similarly, when battery is fully charged, it directly have to for discharge state.

1MW/2MWh BESS which means 

Charge time or Store Duration = 2MWh/1MW = 2 hours needed to charge discharge it.

There are 3 options which depends how much SOC(%) initially it on-
1.SOC=0%

2.SOC=50%

3.SOC=100%
As mostly, initially battery is not charged i.e. 0% SOC

In this case, firstly battery have to be charge means I need price at lower term. After that 2 options, Charge it or discharge it. From this similar two options will appear. But in end it needs to be Discharge.

Options are B T B T  or   B B T T
From this, I can conclude that – First steps B and Last Steps T

Means I can put this condition to find our desired answer.

Last steps as I needed to maximise revenue (TB2 maximum)

I have find sum(T1+T2)-sum(B1+B2) and this has to maximise.
![image](https://github.com/KartiKothari/Revenue-Optimizing-in-Energy_US/assets/147384232/50a6c952-cc2f-476a-9032-0f33209bfa66)

### Code which write this logic
## **Assumption**

1.Assume that energy loss is zero

2.Amount taken to charge or discharge is 2 Hours

3.Initally SOC% can be 0 to 100 which will affect what I need first like we have buy or sell power

4.If battery is fully charged or fully depeleted i.e. 100% or 0% then either charge it or discharge it.0

5.Good options - charge two times then sell 2 times - need to maximise TB2 revenue so have to constanly cheking T2-B2.

6.First I will locate top and bottom 2 values then I will optimise with SOC% and find the best way for max(revenue) in a given day.

7.In this I am only finding for one day without checking data of next day which can created more variables.

8.I can also calculated from point 8 but it will be more complicated. I can all arrange all prices and dates in one single string and then calculate a way which can maximise revenue. In this we will find for 365*24.

9.In this we can only calulate for 1 hr for which buy at lower price and sell it higher price.

## Actions for this problem - Testing to Solution
1.First finding 4-5 top and bottom values

2.Then sum of 4 values (2 values each time) also their index in both cases top and bottom separetely

3.and compared then with given that index sum of bottom is lower then top index sum

4.Find maximum T2-B2 append that in list add that in dataframe with unique date
