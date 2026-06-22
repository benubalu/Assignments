# Flowchart

<img width="683" height="817" alt="Screenshot 2026-06-21 at 22 33 36" src="https://github.com/user-attachments/assets/7c81a5d3-422b-4e43-8525-e862a2619ede" />

# Challenges

Honestly the first thing that got me was just remembering to use lowercase. I almost started with "Ben" and then caught myself because uppercase B has a different ASCII value than lowercase b, which would have given me the wrong hex code entirely.

The hex part was fine until I hit remainders bigger than 9. Like when I got 14 I just wrote 14 at first and then remembered that in hex that is supposed to be E. That took a second to get used to, having letters mixed in with numbers felt weird.

The binary conversion for 2005 was not too bad once I got the rhythm of dividing by 2, but I kept almost losing track of which remainder went where. You have to be really careful writing them down in order because you read them backwards at the end, and if you mess up one step the whole thing is wrong.


# Encoding

### Part 1: Name in Hexadecimal

Name in lowercase: ben

Step 1: Convert each letter to ASCII decimal

| Letter | ASCII (decimal) |
|--------|-----------------|
| b      | 98              |
| e      | 101             |
| n      | 110             |

Step 2: Convert each decimal to hexadecimal

b = 98
98 ÷ 16 = 6 remainder 2
So 98 in hex = 62

e = 101
101 ÷ 16 = 6 remainder 5
So 101 in hex = 65

n = 110
110 ÷ 16 = 6 remainder 14 --> 14 = E in hex
So 110 in hex = 6E

Codename (hex): 62 65 6E

---

### Part 2: Birth Year in Binary

Birth year: 2005

| Division  | Quotient | Remainder |
|-----------|----------|-----------|
| 2005 ÷ 2  | 1002     | 1         |
| 1002 ÷ 2  | 501      | 0         |
| 501 ÷ 2   | 250      | 1         |
| 250 ÷ 2   | 125      | 0         |
| 125 ÷ 2   | 62       | 1         |
| 62 ÷ 2    | 31       | 0         |
| 31 ÷ 2    | 15       | 1         |
| 15 ÷ 2    | 7        | 1         |
| 7 ÷ 2     | 3        | 1         |
| 3 ÷ 2     | 1        | 1         |
| 1 ÷ 2     | 0        | 1         |

Read remainders from bottom to top: 11111010101

2005 in binary: 11111010101
