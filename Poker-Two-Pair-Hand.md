*[[Unit 5 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How can we determine if the player's hand qualifies as a "two-pair"?
  - We need to check if there are exactly two different ranks that each appear twice in the hand.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Evaluate the player's hand to identify if there are two sets of cards where each set consists of two cards of the same rank.

```markdown
1) Initialize a dictionary `rank_count` to keep track of how many times each rank appears in the hand.
2) Iterate over each card in `player_hand`, incrementing the count of its rank in `rank_count`.
3) Count how many ranks appear exactly twice using a counter `pairs_count`.
4) If `pairs_count` equals 2, return `True` indicating the hand has exactly two pairs. Otherwise, return `False`.
```

**⚠️ Common Mistakes**

- Miscounting the pairs, potentially by not checking if each pair contains exactly two cards.
- Incorrectly handling or iterating through the ranks, leading to inaccurate counts.

## I-mplement

```python

		def is_two_pair(player_hand):
    # Create a dictionary to count occurrences of each rank
    rank_count = {}
    
    # Count the ranks in the hand
    for card in player_hand:
        if card.rank in rank_count:
            rank_count[card.rank] += 1
        else:
            rank_count[card.rank] = 1
            
    # Check for two different ranks each appearing exactly twice
    pairs_count = 0
    
    for count in rank_count.values():
        if count == 2:
            pairs_count += 1
    
    # Return True if there are exactly two pairs
    return pairs_count == 2
```