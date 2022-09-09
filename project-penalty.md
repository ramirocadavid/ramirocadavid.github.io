---
layout: page
title: Penalty Shoot-out Game
permalink: /projects/penalty
---
*Ramiro Cadavid*

[GitHub project](https://github.com/ramirocadavid/world_cup)

*A Python penalty shoot-out game, bulit to be played in the shell*

<img src="/assets/images/penalty.jpg" width="900">

## Game description

"A penalty shoot-out (officially kicks from the penalty mark) is a method of determining which team advances or is awarded the championship of an association football match that cannot end in a draw but where the score is tied after the regulation playing time as well as extra time (if used) have expired. In a penalty shoot-out, each team takes turns attempting a specified number of shots on the goal from the penalty mark (5 in FIFA-governed football) that are defended only by the opposing team's goalkeeper, with the team that makes more successful kicks being declared the winner of the match." Source: [Wikipedia][1]

[1]: https://en.wikipedia.org/wiki/Penalty_shoot-out_(association_football)

## User experience

The game will ideally be played by two players, but it can be played by up to twelve, grouped in two teams. The user experience of the players involved will follow the process described below.

**Configuration**
1. Create at least two teams (two are automatically created by default)
1. Create at least 6 players per team (one goalkeeper and five shooters)

**Match setup**
1. Select the two teams that will play the game
1. Select at least 5 players per team

**Game**:
1. There will be initially 5 pairs of penalty kicks, where the teams will take turns to kick the penalty or catch it.
1. In each kick, if the ball ends up inside the goal, one point will be scored to the kicker's team.
1. If after 5 pairs of kicks the teams end up with the same amount of points, they will move to play one pair of kicks. They will keep playing one pair of kicks until one of the teams misses and the other scores in one of these pairs.

## Skills

Python, object-oriented programming, software design
