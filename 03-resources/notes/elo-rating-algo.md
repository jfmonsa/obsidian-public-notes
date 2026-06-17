---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
    - cs/ai
---

# ELO Algo

## What's ELO
+ Designed by Arpad Elo, chess master of USCF
+ Method for calculating the relative skill levels of players in zero-sum games such as chess or esports.
+ The difference in the ratings between two players serves as a predictor of the outcome of a match.
+ Two players with equal ratings who play against each other are expected to score an equal number of wins.
+ Two players with equal ratings who play against each other are expected to score an equal number of wins.
+ A player's Elo rating is a number which may change depending on the outcome of rated games played. After every game, the winning player takes points from the losing one
+ The difference between the ratings of the winner and loser determines the total number of points gained or lost after a game
+ If the higher-rated player wins, then only a few rating points will be taken from the lower-rated player
+  However, if the lower-rated player scores an upset win, many rating points will be transferred.
+ The lower-rated player will also gain a few points from the higher rated player in the event of a draw.
+ Elo ratings are comparative only, and are valid only within the rating pool in which they were calculated

## ELO Algo
These two players will have their corresponding Elo ratings, _Ra_, and _Rb_ respectively. Before the match, the difference between the Elo ratings of these two players should be small enough for them to be selected as good competitors

|Ra — Rb| ≤ M

After each match, the Elo rating of player A is updated according to the following formula _R’a = Ra + K*_(_Sa — Ea_)
A good starting value is _K_ = 32 with which you can start to experiment.

As we mentioned before, each match can have only three possible outcomes from the perspective of player A. This is reflected in the values that the variable _SA_ takes, in the case of victory _Sa_ = 1, in the case of loss, _Sa_ = 0, and in the case of a tie _Sa_ = 0.5.

0 _≤ Sa ≤_ 1 it follows that it would be nice that likewise 0 _≤ Ea ≤_ 1. Elo formula maps the expectation of the outcome of the match onto the interval (0,1). It is the logistic curve with base 10. It can be written as _Ea = Qa_ /(_Qa + Qb_), where _Qa =_ 10^(_Ra_/_c_) and _Qb =_ 10^(_Rb_/_c_).

The factor c is another of the magic numbers in this calculation and is usually taken to have the value of _c_ = 400. You can select any other value you want but if you are uncertain, 400 is a good start.

## ELO for new players
ELO for new players Let’s denote it as _Ra0_. A good value is _Ra0_ = 1500

Otras opciones:
* 1200 con K=20
* segun chat gpt entre 800 y 1400, 1200 ideal
```
/*
        K is the development coefficient.
        K = 40 for a player new to the rating list until he has completed events with at least 30 games
        K = 20 as long as a player's rating remains under 2400.
        K = 10 once a player's published rating has reached 2400 and remains at that level subsequently, even if the rating drops below 2400.
        K = 40 for all players until their 18th birthday, as long as their rating remains under 2300.

        K = 20 for RAPID and BLITZ ratings all players.
        */
```
## Prevent negative ELO
Finally, we do not want a player to have a negative Elo rating. The initial value Ra0 needs to be significantly larger than the scaling factor _K_, to allow for the player to play, and lose enough matches before eventually winning one so that his Elo rating would finally start to rise up.

Just to be on the safe side, and to limit negative user experience it is good to introduce a minimal Elo rating value, _Rmin_ below which the Elo rating of an individual player cannot drop. In other words, if _Ra = Rmin_ the player’s rating will be updated only upwards!

## Debo leer:
+ https://www.geeksforgeeks.org/elo-rating-algorithm/
+ https://mattmazzola.medium.com/understanding-the-elo-rating-system-264572c7a2b4
+ https://en.wikipedia.org/wiki/Elo_rating_system
+ https://www.chess.com/terms/elo-rating-chess
+ https://drive.google.com/file/d/17xD873DqYqccqDogxRuqiTq0dl_JgnEL/view

## References
+ https://stanislav-stankovic.medium.com/elo-rating-system-6196cc59941e - ELO for chess and for PvP games
