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

## Code structure

<img src="/assets/images/penalty-code.jpg" width=800>

The classes that compose the game are described below. Details about contents of attributes and inner workings of methods are included when their names are not self-explanatory. The classes are classified into those used to setup the game (Configuration classes), to setup the match (Game setup classes) and to play the game (Game classes).

#### Team setup classes

**Team**: Represents a team that can be chosen to play in a match. Contains data of the team name, the players available and the times the team has won.
- Data attributes
    - Name: custom name given to each player
    - Players
    - Wins
- Methods
    - Init: initializes a team instance with its custom name
    - List teams

**Player**: Represents a player that can be included in a team. Contains name, ability, type and team.
- Data attributes
    - Init: initializes a player instance with its custom name
    - Name
    - Ability (randomly assigned)
    - Type: goalkeeper or shooter
- Methods
    - List players

#### Match setup classes

**Match**: represents the match in which the shootout will be played. Contains data on the setup of the games and keeps track of its status and results.
- Data attributes
    - Score
    - Number of kicks: tuple that indicates the kick number and the last team that shoot
    - Teams: tuple with participating teams
    - Score: Keeps score up to last kick
    - Winner: winner of the match, once it's finished, otherwise is None
    - Shooters: list of shooters of each team
- Methods
    - Init: initializes a match instance with the team and players involved
    - Match setup: Method to setup a match, including the participating teams and players within each team
    - Quick match: starts a quick match with two default teams and players, skipping any initial game setup

#### Kick dynamic Classes

**Kick**: Represents an individual kick, with information on each participating player's strategy and the result of the combination of both strategies.
- Data attributes
    - Strategies: tuple containing the strategy of the shooter and the goalkeeper.
    - Result: stores result of the kick
    - Match: match to which the kick belongs to   
- Methods
    - Set result: determines kick result from the combination of the values in the `strategies` attribute.
    - Update score: Updates the match score based on the kicks result (goal or miss)
    - Start kicks: starts a kicks session, that is repeated until one of the players wins

**Strategy**
- Data attributes
    - Player: player object that decides on the strategy
    - Height: numeric altitude to which the ball is shoot or where the goalkeeper is directed to
    - Direction: direction given to the kick/catch
    - Margin of error: randomly selected error value within a default range

## Skills

Python, object-oriented programming, software design
