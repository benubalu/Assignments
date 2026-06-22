# Flowchart

<img width="458" height="817" alt="Screenshot 2026-06-21 at 23 09 24" src="https://github.com/user-attachments/assets/e4737557-8ff2-4ee7-846e-a416dfa57b54" />

# Challenges

Honestly the hardest part was setting up the K-map correctly. The columns don't go in normal binary order (00, 01, 10, 11); they go 00, 01, 11, 10, and if you miss that, all your groupings are wrong. I had to go back and redo the table once I caught that mistake.

Grouping the 1s was also tricky at first. You want the largest groups possible, and sometimes a 1 can be in more than one group, which felt weird but is totally allowed. For the motion light problem, the K-map was simpler since it only had two variables, and the groupings were more obvious once the table was filled in.

# Problems
I added an image showing the K-maps since it was easier to draw them out clearly than to format the tables in text. The image shows all the groupings and results visually, which I think makes it a lot easier to follow.

## Problem 1: Simplify F = A'B'C' + A'B'C + A'BC + AB'C + ABC'

### Step 1: Place minterms in K-map

Minterms:
- A'B'C' = 000
- A'B'C  = 001
- A'BC   = 011
- AB'C   = 101
- ABC'   = 110

K-map (columns BC in order: 00, 01, 11, 10):
        BC
A    00  01  11  10
0  |  1 | 1 | 1 | 0 |
1  |  0 | 1 | 0 | 1 |

### Step 2: Group adjacent 1s

Group 1: A'B'C' and A'B'C (row A=0, columns 00 and 01)
A stays 0, B stays 0, C differs → term = A'B'

Group 2: A'B'C and AB'C (column 01, both rows)
B stays 0, C stays 1, A differs → term = B'C

Group 3: A'B'C and A'BC (row A=0, columns 01 and 11)
A stays 0, C stays 1, B differs → term = A'C

### Step 3: Final result

F = A'B' + B'C + A'C

---

## Problem 2: Motion-Sensing Light System

Original expression:
i = mt' + m't + mt

K-map:

  .  t
m    0   1
0  | 0 | 1 |
1  | 1 | 1 |

Group 1: mt' and mt (row m=1) → m
Group 2: m't and mt (column t=1) → t

Final result: i = m + t

The lamp turns on if motion is detected OR test mode is on.


# <img width="609" height="752" alt="Screenshot 2026-06-21 at 23 39 25" src="https://github.com/user-attachments/assets/603081ac-ad22-467f-acc3-6587fe1ee19a" />


