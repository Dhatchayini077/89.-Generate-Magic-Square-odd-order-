# 89.-Generate-Magic-Square-odd-order-
import numpy as np

order = int(input("Enter order of magic square (order must be odd): "))

# If even number is given, increment it by one
if order % 2 == 0:
    order += 1
    print("Given order is even so it is incremented by 1.")

mid = order // 2
magic = np.zeros((order, order), dtype=int)

# Siamese method for odd-order magic square
k = mid
j = 0

for i in range(1, order * order + 1):
    magic[j][k] = i
    p, q = j, k  # store previous positions
    j -= 1
    k += 1

    if j < 0:
        j = order - 1
    if k > order - 1:
        k = 0
    if magic[j][k] != 0:
        k = q
        j = p + 1

# Display magic square
print("Generated Magic Square is:\n")
for row in magic:
    print("|", end="")
    for val in row:
        print(f"{val:4d} |", end="")
    print()
    print("-" * (5 * order))
output
Enter order of magic square (order must be odd): 5
Generated Magic Square is:

|  17 |  24 |   1 |   8 |  15 |
-------------------------------
|  23 |   5 |   7 |  14 |  16 |
-------------------------------
|   4 |   6 |  13 |  20 |  22 |
-------------------------------
|  10 |  12 |  19 |  21 |   3 |
-------------------------------
|  11 |  18 |  25 |   2 |   9 |
-------------------------------
