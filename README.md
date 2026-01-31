
# Interactive 27-Card Ternary Magic Trick

An interactive, browser-based implementation of the classic **27-card mathematical card trick**, powered by base-3 (ternary) arithmetic.

The user selects a favorite number from 1 to 27, memorizes a card, and identifies which pile it appears in over three rounds.  
At the end, the app reveals the chosen card at the exact position predicted by the math.

No sleight of hand — just mathematics.

---

## Background

I originally encountered this trick in a **YouTube video presented by a mathematician**, where the underlying idea was explained using base-3 numbers.

Curious about translating the idea into software, I first implemented the trick as a **mobile app using MIT App Inventor 2**, and shared it with the App Inventor community.

Later, I adapted the idea again as a **fully interactive web application**.

---

## A Note on AI-Assisted Development

This project has also served as a **test prompt for AI coding agents** I encounter over time.

    make an interactive card game, in a single html file, where the user enters a favorite number from 1 to 27. the game shuffles a deck and deals 27 cards (left to right, top to bottom) into 3 piles and 9 rows.  ask the user to memorize one card and press the button that corresponds to the pile where the card is located. the game gathers the piles in a specific (secret below) way and repeats this in 2 more rounds.  then it is revealed - the chosen card is in the location indicated by the favorite number.  secret: subtact 1 from the favorite number and convert to base 3.  say the favorite number is 20.  convert 19 (20 - 1) to ternary, you get 201.  the digits in reverse order, dictate how the piles are gathered at each round, where 0 means gather the chosen pile first followed by the other files, 1 means gather all piles such that the chosen pile is in middle and 2 means gather the chosen pile last.  reveal by showing the final gathered deck in numbered order and highlight the location of the memorized card.  the location is (in this example) 9* 2 + 3 * 0 + 1*1 (using the original digits of the ternary number).  show a button to play again

The prompt describes the trick, the ternary logic, and the user interaction requirements.  
Many AI agents are able to generate a working version, but some subtle issues (edge cases, pile-gathering order, ternary digit handling, and UI rendering quirks) typically require **human debugging insight**.

Several of those issues were resolved with the debugging expertise of **ChatGPT**, making this a nice example of:
- human mathematical understanding
- AI-assisted coding
- iterative debugging and refinement

---

## How the Trick Works (Short Version)

1. The user enters a favorite number `N` (1–27).
2. Compute `N − 1`, then convert it to **base 3**, producing three digits.
3. The digits (reversed) determine how the piles are gathered in each round:
   - `0` → chosen pile goes first
   - `1` → chosen pile goes in the middle
   - `2` → chosen pile goes last
4. After three rounds, the final position of the chosen card is:

