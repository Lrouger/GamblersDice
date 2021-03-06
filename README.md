Gambler's Fallacy Dice Roller
=============================

Motivation
----------

A dice roller that respects the Gambler's Fallacy.

One night I was playing Settlers of Catan with my family, and a series of lucky rolls brought me from 4 points to 10 points in only 3 turns, thus winning the game. That wasn't very fun, for me or for the other players.

That's why I wrote a dice roller that respects the Gambler's Fallacy. Numbers that have been rolled recently will be less likely to roll again, and numbers which have not been rolled recently will be more likely to roll. This should help to prevent a lucky streak that favors some players, reducing the amount that the players must rely on chance in order to win.

Instructions
------------

You can press enter or spacebar to roll the dice.

You can click on the "Weight factor" to tweak it. The weight factor controls how heavily a number gets penalized after it is rolled. A large weight means that a number that has been recently rolled is much less likely to roll again.

Game Design Notes
-----------------

Some games use random elements to drive the mechanics of the game. Settlers of Catan is a good example, resources are delivered to players based on the results of a 2d6 die roll. Settlers is a great game, but sometimes the random number mechanic that drives the game causes a bit of grief. Sometimes a player will have a settlement on a number that should be commonly rolled, but the the dice just happen not to roll that number. I'm assuming that Settlers was intended to be more a game about skill than a game of chance, and so lucky streaks that deliver one player an advantage or disadvantage are undesireable to the game designer.

I've played more than one game of Settlers where one player feels cheated that their number hasn't come up. I vaguely remember a talk by Sid Meier where he discussed the random number generator that powered the battles in one of his iterations of Civilization, and it had a similar problem. Players would be frustrated when a battle that they had 80% chance to win (for example) would be lost 2 or 3 times in a row. While it's unlikely for that to happen, it's bound to happen sometime, to at least one of your players, and the more a player plays your game the more likely it is to happen. As a designer, [you can never be sure](http://dilbert.com/strips/comic/2001-10-25/) what your random number generator is going to do, and sometimes it may ruin the experience for the player. That's where a "fairer" generator, such as this one, can improve a game's design.

This roller has up an interesting side-effect. If players know that the odds change given previous rolls, they may change their behavior. The player that knows that a rare roll is "due" may ignore the odds and act more boldly than she otherwise would have. If you're a game designer and you're considering implementing a system such as this in your game, consider the impact that making the true odds available to the player, or omitting the generator's special behavior, may have on your design.

Mathematics Notes
-----------------

Suppose I flip a coin and keep track of the number of heads and tails. The law of large numbers states that as the number of flips increases, the proportion of heads to tails tends towards 50% heads and 50% tails. However, there's no guarantee that the difference between the number of heads and the number of tails will trend towards 0. If I flip the coin two million times and I get 1,000,050 heads and 999,950 tails, that's 50.0025% heads, but still a difference of 100 more heads than tails. The law of large numbers doesn't guarantee that tails will ever catch up, and in fact, the longer the simulation runs the less likely tails is to catch up to heads.

This dice roller changes that by making tails more likely to be rolled heads has been rolled more often in the past. Thus, tails is likely to catch up to heads since its probability is greater. Once tails has caught up to heads, the probability goes back to 0.50. You can try it yourself if you put 1d2 into the roller. In tests of large numbers of rolls, for example 10,000 2d6 rolls, the number of 2's is never more than 1 or 2 different than the number of 12's, and often they are the same.