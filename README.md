```markdown
# Card Counting Assistant for Blackjack

## Overview
This project implements a simple Card Counting Assistant for the game of Blackjack. The assistant helps players determine whether they have an advantage over the house based on the remaining cards in the deck. By tracking high and low cards, players can make informed betting decisions: "Bet" when the count is positive, indicating an advantage, or "Hold" when the count is zero or negative.

## How It Works
- The system maintains a global `count` variable that keeps track of the current card count.
- Each time a card is dealt, the `cc()` function updates the count based on the card's value:
  - Cards 2 through 6 increase the count by 1.
  - Cards 7 through 9 do not change the count.
  - Cards 10, Jack, Queen, King, and Ace decrease the count by 1.
- The function returns a string indicating the current count and the recommended action:
  - `"Bet"` if the count is positive.
  - `"Hold"` if the count is zero or negative.

## Usage

### Declaring the Count Variable
The system uses a global variable `count` initialized to 0:
```javascript
let count = 0;
``

### The `cc()` Function
Call `cc()` with a card value (number or string) each time a card is dealt:
```javascript
cc(2);   // e.g., increases count
cc("K"); // decreases count
``

### Example:
```javascript
cc(2);    // count becomes 1, returns "1 Bet"
cc(7);    // count remains 1, returns "1 Bet"
cc("A");  // count becomes 0, returns "0 Hold"
``

### Complete Example:
```javascript
// Initialize count
let count = 0;

// Simulate dealing a series of cards
console.log(cc(2));    // "1 Bet"
console.log(cc(3));    // "2 Bet"
console.log(cc(7));    // "2 Bet"
console.log(cc("K"));  // "1 Bet"
console.log(cc("A"));  // "0 Hold"
``

## Implementation
```javascript
let count = 0;

function cc(card) {
  if (typeof card === 'number') {
    if (card >= 2 && card <= 6) {
      count += 1;
    } else if (card >= 10 && card <= 10) {
      count -= 1;
    }
  } else if (typeof card === 'string') {
    if (['J', 'Q', 'K', 'A'].includes(card)) {
      count -= 1;
    }
  }
  const decision = count > 0 ? 'Bet' : 'Hold';
  return `${count} ${decision}`;
}
``

## Testing
Use the `cc()` function with various card inputs to track the count and get betting advice based on the current state.

---
```
