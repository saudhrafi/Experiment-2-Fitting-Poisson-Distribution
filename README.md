# Experiment-2-Fitting-Poisson-Distribution
Aim: 
To fit Poisson distribution for the arrival of objects per minute from the feeder. 
# Software required: 

Python and Visual Component Tool
# Theory: 

1. The Poisson distribution gives the probability of a number of events occurring in a fixed interval of time or space when events occur independently and at a constant average rate (λ).
2. The probability mass function (PMF) is:  
<img width="1171" height="73" alt="image" src="https://github.com/user-attachments/assets/e28da9e9-3b3f-4969-baa9-2ff06c3358ba" />
3. Here, λ = mean number of occurrences, and e = 2.718 (base of natural logarithm).
4. The mean and variance of a Poisson distribution are both equal to λ.
5. Applicable when events occur independently, singly, and at a constant rate.
# Algorithm
<img width="1144" height="412" alt="image" src="https://github.com/user-attachments/assets/6bf357bd-7ba2-4908-8c93-ef74e4747a4f" />


# Name: Mohamed saudh R
# Reg_No: 25011649
# Slot_Name: 3P1-1
# Date: 17-11-2025


# Program: 
```
# Exp: No-2
import numpy as np
import math
import scipy.stats

# Input
L = [int(i) for i in input().split()]
N = len(L)
M = max(L)

X = []
f = []

# Frequency count
for i in range(M + 1):
    c = 0
    for j in range(N):
        if L[j] == i:
            c += 1
    f.append(c)
    X.append(i)

sf = np.sum(f)

# Probability of each X
p = []
for i in range(M + 1):
    p.append(f[i] / sf)

# Mean of the distribution
mean = np.inner(X, p)

# Poisson expected frequencies
p = []
E = []
xi = []

print("X   P(X=x)  Obs.Fr  Exp.Fr  xi")
print("--------------------------------")

for x in range(M + 1):
    px = math.exp(-mean) * mean**x / math.factorial(x)
    p.append(px)

    expected = px * sf
    E.append(expected)

    chi_term = ((f[x] - expected) ** 2) / expected
    xi.append(chi_term)

    print("%2d  %.3f   %4d   %.2f   %.3f" % (x, px, f[x], expected, chi_term))

print("--------------------------------")

# Chi-square calculated value
cal_chi2_sq = np.sum(xi)
print("Calculated Chi-square = %.4f" % cal_chi2_sq)

# Table value (1% LOS)
df = M
table_chi2 = scipy.stats.chi2.ppf(1 - 0.01, df=df)
print("Table Chi-square (1%% LOS) = %.4f" % table_chi2)

# Decision
if cal_chi2_sq < table_chi2:
    print("Result: Data fits Poisson distribution at 1% LOS")
else:
    print("Result: Data does NOT fit Poisson distribution at 1% LOS")





```
# Google_Colab-link: 
https://colab.research.google.com/drive/1XHA9fpfKu1iotQaFTkahiDGSxAHf5DWD?usp=sharing





# Output

<img width="551" height="356" alt="image" src="https://github.com/user-attachments/assets/eb5f8c27-1da7-485a-a5b4-6ffad48d1cc7" />


# Result
The Poisson Distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 

