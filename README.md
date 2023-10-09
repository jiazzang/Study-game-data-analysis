# 게임 데이터 분석
kaggle, Dacon 등 AI 플랫폼이나 OpenAPI를 통해 무료로 공개된 게임 데이터를 분석한 내용을 기록합니다.


## 1. PUBG 배틀그라운드 게임 데이터 분석
PUBG Developer에서 공개한 배틀그라운드 데이터를 활용한 분석 프로젝트입니다. EDA, 전처리, 시각화를 위주로 분석을 진행했고, 플레이어 등급의 최종 배치를 예측하는 RandomForest 모델도 basic하게 만들어보았습니다. 


<details>
<summary>활용 데이터</summary>
<div markdown="1">       

* train 데이터(.csv)  
-Rows X Columns: 4446966 X 29  
-각 행은 플레이어 한 명의 게임(match) 통계를 나타냄  
-Target variable: 플레이어 등급의 최종 배치(`winPlacePerc`)

</div>
</details>


<details>
<summary>활용 데이터 출처</summary>
<div markdown="1">       

* [Kaggle - PUBG Finish Placement Prediction (Kernels Only)](https://www.kaggle.com/competitions/pubg-finish-placement-prediction/data)

</div>
</details>


<details>
<summary>활용 변수</summary>
<div markdown="1">

|변수명|변수 설명|
|----|----------|
|DBNOs|Number of enemy players knocked.|
|assists|Number of enemy players this player damaged that were killed by teammates.|
|boosts|Number of boost items used.|
|damageDealt|Total damage dealt. Note: Self inflicted damage is subtracted.|
|headshotKills|Number of enemy players killed with headshots.|
|heals|Number of healing items used.|
|Id|Player’s Id|
|killPlace|Ranking in match of number of enemy players killed.|
|killPoints|Kills-based external ranking of player. (Think of this as an Elo ranking where only kills matter.) If there is a value other than -1 in rankPoints, then any 0 in killPoints should be treated as a “None”.|
|killStreaks|Max number of enemy players killed in a short amount of time.|
|kills|Number of enemy players killed.|
|longestKill|Longest distance between player and player killed at time of death. This may be misleading, as downing a player and driving away may lead to a large longestKill stat.|
|matchDuration|Duration of match in seconds.|
|matchId|ID to identify match. There are no matches that are in both the training and testing set.|
|matchType|String identifying the game mode that the data comes from. The standard modes are “solo”, “duo”, “squad”, “solo-fpp”, “duo-fpp”, and “squad-fpp”; other modes are from events or custom matches.|
|rankPoints|Elo-like ranking of player. This ranking is inconsistent and is being deprecated in the API’s next version, so use with caution. Value of -1 takes place of “None”.|
|revives|Number of times this player revived teammates.|
|rideDistance|Total distance traveled in vehicles measured in meters.|
|roadKills|Number of kills while in a vehicle.|
|swimDistance|Total distance traveled by swimming measured in meters.|
|teamKills|Number of times this player killed a teammate.|
|vehicleDestroys|Number of vehicles destroyed.|
|walkDistance|Total distance traveled on foot measured in meters.|
|weaponsAcquired|Number of weapons picked up.|
|winPoints|Win-based external ranking of player. (Think of this as an Elo ranking where only winning matters.) If there is a value other than -1 in rankPoints, then any 0 in winPoints should be treated as a “None”.|
|groupId|ID to identify a group within a match. If the same group of players plays in different matches, they will have a different groupId each time.|
|numGroups|Number of groups we have data for in the match.|
|maxPlace|Worst placement we have data for in the match. This may not match with numGroups, as sometimes the data skips over placements.|
|winPlacePerc|The target of prediction. This is a percentile winning placement, where 1 corresponds to 1st place, and 0 corresponds to last place in the match. It is calculated off of maxPlace, not numGroups, so it is possible to have missing chunks in a match. => 예측해야 하는 변수|


</div>
</details>


#### 분석 코드: [PUBG_Battlegrounds_game_data_analysis.ipynb](https://github.com/jiazzang/Study-game-data-analysis/blob/main/PUBG_Battlegrounds_game_data_analysis.ipynb)
