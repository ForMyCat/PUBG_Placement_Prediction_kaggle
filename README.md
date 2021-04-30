# PUBG_Placement_Prediction_kaggle
 This repo includes all my dataset and notebooks used for RPI 2021 Spring Intro to Machine Learning class with professor Lydia Manikonda

Pubg Game Prediction
Website: https://www.kaggle.com/c/pubg-finish-placement-prediction

Interesting Notebooks:
https://www.kaggle.com/mynextstep16/beginner-1st-model    XGB,LinearReg
https://www.kaggle.com/hegab7/pubg-note       DecisionTree
https://www.kaggle.com/muhammedabdulazeem/pubg-full-eda-and-predication-different-ml-models				Very Thorough EDA, CGB, RandomForest



**EDA Note:**
Original DF len: 4446966 rows
47965 unique matches, select 4796 matches, 445296 rows in total
29 columns
stratified sampling for EDA random_state=1, frac=0.1, to get 444697 rows

**Cheater Statistics:**
https://www.reddit.com/r/PUBATTLEGROUNDS/comments/elo0vj/pubg_cheating_statistics/
cite:
Essentially, I'm estimating that for a 90 person match, the probability that you're going to be playing against someone who IS getting banned that week is 91.4% (1.0 - (0.9731 ^ 90))

world kill record: 
43 on AS server
34 on EU
26 on NA

Assumption: Anyone with 20 kills to be a cheater

**Selected Features for modeling:**
Explanatory: 'walkDistance', 'killPlace'(neg), 'boosts', 'weaponsAcquired','damageDealt','heals','kills','longestKill', and 'killStreaks'.
Target: 'winPlacePerc'

**Feature Columns:**

DBNOs - Number of enemy players knocked.

assists - Number of enemy players this player damaged that were killed by teammates.

boosts - Number of boost items used.

damageDealt - Total damage dealt. Note: Self inflicted damage is subtracted.

headshotKills - Number of enemy players killed with headshots.

heals - Number of healing items used.

Id - Player’s Id

killPlace - Ranking in match of number of enemy players killed.

killPoints - Kills-based external ranking of player. (Think of this as an Elo ranking where only kills matter.) If there is a value other than -1 in rankPoints, 
then any 0 in killPoints should be treated as a “None”.

killStreaks - Max number of enemy players killed in a short amount of time.

kills - Number of enemy players killed.

longestKill - Longest distance between player and player killed at time of death. This may be misleading, as downing a player and driving away may lead to a 
large longestKill stat.

matchDuration - Duration of match in seconds.

matchId - ID to identify match. There are no matches that are in both the training and testing set.

matchType - String identifying the game mode that the data comes from. The standard modes are “solo”, “duo”, “squad”, “solo-fpp”, “duo-fpp”, and “squad-fpp”; 
other modes are from events or custom matches.

rankPoints (Deprecated) - Elo-like ranking of player. This ranking is inconsistent and is being deprecated in the API’s next version, so use with caution. Value of -1 takes 
place of “None”.

revives - Number of times this player revived teammates.

rideDistance - Total distance traveled in vehicles measured in meters.

roadKills - Number of kills while in a vehicle.

swimDistance - Total distance traveled by swimming measured in meters.

teamKills - Number of times this player killed a teammate.

vehicleDestroys - Number of vehicles destroyed.

walkDistance - Total distance traveled on foot measured in meters.

weaponsAcquired - Number of weapons picked up.

winPoints - Win-based external ranking of player. (Think of this as an Elo ranking where only winning matters.) If there is a value other than -1 in rankPoints, 
then any 0 in winPoints should be treated as a “None”.

groupId - ID to identify a group within a match. If the same group of players plays in different matches, they will have a different groupId each time.

numGroups - Number of groups we have data for in the match.

maxPlace - Worst placement we have data for in the match. This may not match with numGroups, as sometimes the data skips over placements.

winPlacePerc - The target of prediction. This is a percentile winning placement, where 1 corresponds to 1st place, and 0 corresponds to last place in the match. 
It is calculated off of maxPlace, not numGroups, so it is possible to have missing chunks in a match.
