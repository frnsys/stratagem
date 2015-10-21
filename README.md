A strategic card game played with a regular 52-card playing deck.

Inspired by (elements borrowed from):

- <http://thom.org.uk/2008/09/23/magic-the-gathering-with-normal-playing-card/>
- <http://www.angelfire.com/my/zelime/games.html#Magic>
- <https://gist.github.com/datagrok/9107521>

Principles for interesting gameplay:

- There should be a small degree of randomness
- There should be a strategy bottleneck (some factor limiting available strategies)

---

### Deck

One standard 52-card playing deck is all that's needed.

Players draw from the same deck. When the deck is empty, the discard piles of each player are shuffled to form a new deck.

### Card types

- Units (♣ Clubs)
- Events (♦ Diamonds)
- Resources (♠ Spades)
- Environments/Equipment (♥ Hearts)

### Resource costs

Resource costs should be some function of the card's (or combination of cards') value.

### Card strength/potency

Card strength/potency should also be some function of the card's (or combination of card's) value.

### Varying rule sets

Use numerical properties of the cards to determine their abilities

- e.g. primes have one ability, abilities by parity (i.e. even numbers have another, odd numbers have another)
- how to deal with face cards and suits?


1 (A)           odd
2       prime           even
3       prime   odd
4                       even
5       prime   odd
6                       even
7       prime   odd
8                       even
9               odd
10                      even
11 (J)  prime   odd
12 (Q)                  even
13 (K)  prime   odd

### Extra components

A die?

### Card combinations

Cards have effects on their own but can have different effects in combination with other cards.

What card combinations are valid (not all combinations do anything, for instance) and what effect they have are decided before each game. There may be a preset enumerated list of them; at the start of the game you roll dice to see which ones are active for that game.

Possible card effects:

- Destroy resource
- Destroy unit
- Counter event
- Purge environment/equipment
- Instant damage
- Restore life
- Prevent damage
- Buff unit
- Debuff unit
- Temporary resources


---

### Ferris' Idea

TODO: Add  more to shop
TODO: Probably needs balancing

### Materials

*Required* = 

- 52-card playing deck
- Sheet of paper + pencil

*Misc* =

- 20-sided die (used for the global resource counter)
- die to keep track of the number of cards each player can use per turn

### Rules

#### Resources

##### Adding

  * Each card in the deck can be played at any time to add X of that card's suit 
    into your resource pool (e.g. 5 of diamonds will add 5 diamonds to your 
    resource pool).

  * Face cards have the following values:
  
      ```
        Ace = 1
        Jack = 11
        Queen = 12
        King = 13
        Joker = 1 of any suit
      ```

  * You can't add resources while spending them (while you're creating a spell).
    Therefore, a spell's cost can not exceed the global resource counter 
    (see below).

##### Global Resource Counter (GRC)

  * The total amount of all resources in your resource pool cannot exceed the 
    value of the global resource counter. 

  * The global resource counter starts at *2* (meaning at any time, each player 
    can only have 2 of a any resource in their pool at any given time). The 
    global resource counter ticks up by 1 on each player's turn. 

    Example: If Player A goes first, the global resource counter starts 
    at 2. Then on Player B's turn, the global resource counter ticks up to 3.

  * If you expend a card that exceeds the value of the global resource counter,
    then you add the difference of the maximum allowed amount of any given 
    resource, and the current amount in your pool. 

    Example: If the GRC is at 5, and you have 1 club, and you play a 5 of 
    hearts, you will end up with 1 club and 4 hearts in your resource pool. 

##### Expending

  * You can arbitrarily remove any amount of resources from your resource pool 
    at any time. 

  * Resource pools are emptied at the end of the current turn.

  * You can expend resources in the store, or to increase the number of 
    resource cards you can play per turn.

  * To start, each player can only play 1 resource card a turn. They can 
    increase the number of cards they can play but spending (1) + (X) 
    where X = number of resource cards that player can play currently.

      ```
        Upgrade costs:


          Current | Next
          --------|------
          1       | (2)
          2       | (3)
          3       | (4)
          4       | (5)
          X       | (1) + (X)
      ```

#### Spells
  
  * The phase of the turn determines which types of spells you can create.
  
  * When you create a spell, you are must cast it. 

  * All abilities must have legal targets, unless otherwise specified in order
    to be purchased.

  * Resources are expended to buy abilities from the store. All abilities modify 
    properties of spells / permanents. 

    The types you can create are:

      ```
        Instant
        Sorcery
        Enchantment
        Creature 
      ```

  * The cost to create a spell of each type:

      ```
        Sorcery  = (1)
        Instant  = (2)
        Enchant. = (3)
        Creature = (3)
      ```

  * Spells use the stack / priority system from MTG.

  * All creatures start as (0/0)

#### Misc.

  * All other rules (tapping, stack, combat, how damage works, 
    when you can play cards of certain types, etc.) work like MTG, except 
    the resources you have empty out at the end of your turn (instead at 
    the end of each phase like in MTG).

  * There are no graveyards. Expended spells are removed from the game.

### How to play

  * Each player starts with 20 life, and 5 cards. 

  * The global resource counter starts at 2.

  * The game works like MTG, except each player draws from the shared stack. 
    (Untap, Upkeep, Draw, Main Phase I, Combat, Main Phase II, End)

  * As resources are expended they are placed in the discard pile. 

  * Used up cards are simply removed from the game. 

  * If the center pile runs out of cards, shuffle the discarded pile, and use 
    that as the new deck. 

### Sample Shop

(C)lub = cleverness, (D)iamond = greed, (S)pade = power, (H)eart = life

```
Key
  - (XXX): ABILITY = Activated ability with cost (D)
  - (REC)          = Recurring ability at beginning of your turn 
  - EOT            = End of turn
```

| Cost | Creature     | Enchantment                                       | Instant                                           | Sorcery          
|:----:|:------------ |:------------------------------------------------- |:------------------------------------------------- | :-------------------------------------------------
|  C   | +0/+1        | (REC) Target creature gains unblockable until EOT | Tap target creature                               | Untap target creature
|      |              |                                                   | Target creature gets -3/-0                        |       
|  D   | +2/-1        | (REC) Add 1 resource of any type.                 | Add 1 resource of any type. Lose 1 life           | Draw a card, then discard.
|      | -1/+2        |                                                   |                                                   |
|  S   | +1/0         |                                                   | Prevent 3 dmg                                     | Gain 5 Life
|  H   | +1/0         | (REC) Deal 1 dmg                                  | Deal 2 dmg                                        | Deal 3 dmg       
|      | 0/+1         |                                                   |                                                   | Haste            
|      |              |                                                   |                                                   | Target creature gets +3/+3            
| SSS  | First Strike |                                                   | You can use an extra resource card this turn.     | Destroy creature 
|      |              |                                                   |                                                   | You can use an extra resource card this turn.
| CCC  |              |                                                   | Counter spell                                     | Look at target player's hand.                
| HHH  |              |                                                   | Destroy enchantment                               |                 
| DDD  |              | (D): Lose 2, Draw 1                               |                                                   |

### Other ideas

  * ???