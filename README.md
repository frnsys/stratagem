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