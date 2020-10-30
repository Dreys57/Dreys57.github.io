# Sumo Fight Game Design Document

## Introduction

This game is to be made for the 5100.1 project at SAE Institute Geneva. It is supposed to be a 2 players online game made with the Neko Engine (https://github.com/EliasFarhan/NekoEngine).

## Pitch

Sumo Fight is a 2 player game where each player tries to push his/her opponent out of the ring. The first player out of the ring loses.

![20201030_114939](https://user-images.githubusercontent.com/55787228/97704627-12189080-1ab3-11eb-998a-1190274e8daa.jpg)

## Gameplay

Each player controls a circle which can move forward and backward as well as turn using the W and S keys to move forward and backward as well as A and D to turn.

![20201030_114951](https://user-images.githubusercontent.com/55787228/97704763-45f3b600-1ab3-11eb-9293-2abcc215fc47.jpg)

To try and push his/her opponent out of the ring, the player also has a charge, pressing the Shift key, he/she can use to increase his/her speed for a few moment. During this time, the player can't turn.

![20201030_114957](https://user-images.githubusercontent.com/55787228/97704947-8eab6f00-1ab3-11eb-8857-209fcdd3e2db.jpg)

When colliding with the other player, the charging player will push the other player in the same direction, no matter what his/her previous velocity was.

![20201030_115006](https://user-images.githubusercontent.com/55787228/97705146-e2b65380-1ab3-11eb-98ae-6a9eaeacb413.jpg)

If both players charge at each other at the same time, they "bounce off" each other.

![20201030_115014](https://user-images.githubusercontent.com/55787228/97705249-0ed1d480-1ab4-11eb-9c7f-8dbc271c8048.jpg)

## Challenges

This game uses rollback to make the "real-time" gameplay possible.

One of the challenges of this game is the charge mechanic, because if one player charges the other, we want the other player
to be able to maybe dodge the attack and we also want the charging player to push the other when colliding and not going right through.
To remedy that, the charge will have need to wait a brief moment before working, so that the info went to the clients and the players have time to react if possible.
For the charge itself, it multiplies a scalar to the velocity vector and keeps it in the direction the player was aiming at.

As for the end of the game, the ring will have its own position and radius and whenever one of the players distance to the ring's center is greater than the ring's radius, it will have lost.
