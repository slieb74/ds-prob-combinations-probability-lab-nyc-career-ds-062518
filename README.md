
# Combinations with probabilities

## Introduction

You've already seen in the previous labs that combinations and permutations don't occur in a vacuum. In this lab, you'll extend your knowledge on combinations by using them along with preset probabilities.

## Learning objectives

In this lab,

- You'll get some more practice in on using combinations
- You'll learn how to deal with situations where we're looking sequential outcomes with certain probabilities.

## Let's get started

You'll use combinations again in this lab. It'll be useful to reuse the function you created before:


```python
def combination(n,k):
    combin = factorial(n)/(factorial(n-k)*factorial(k))
    return combin

def factorial(n):
    prod = 1
    while n >= 1:
        prod = prod * n
        n = n - 1
    return prod
```

After a long day of coding, the Flatiron School immersive students decide to go to a bowling alley. A bowling game has 10 rounds. The students still have the combinatorics section of the immersive course in mind, and one student is wondering how big the chance is of throwing 3 strikes first, and then no strikes at all for the next seven rounds. Use the python console below to compute this particular probability, assuming that the chance of a throwing a strike is 0.25%.


```python
strikes_order1 = 0.25**3 * 0.75**7 
strikes_order1 # correct answer: 0.0020856857299804688
```




    0.0020856857299804688



Next, another student is wondering what the chances are of throwing a strike, then no strike for 7 rounds, and then 2 strikes again. calculate the probability below.


```python
strikes_order2 = 0.25 * 0.75**7 * 0.25**2 
strikes_order2 # correct answer: 0.0020856857299804688
```




    0.0020856857299804688



The pattern should be fairly clear from here on out! Now you'll see how combinations come in handy here. You can use them along with these probabilities. Let's see how this works.

Let's start with this question: what is the probability that in the course of 10 games you throw exactly 3 strikes?


```python
exactly_3 = combination(10,3) *0.25**3*0.75**7
exactly_3   # correct answer: 0.25028228759765625
```




    0.25028228759765625



Now, students are obviously interested in throwing as many strikes as possible. Someone wants to know what the probability is of throwing 4 or more strikes. What is the best way of calculating this?


```python
exactly_3 = combination(10,3) *0.25**3*0.75**7
exactly_2 = combination(10,2)*0.25**2*0.75**8
exactly_1 = combination(10,1)*0.25**1*0.75**9
exactly_0 = combination(10,0)*0.75**10

four_or_more = 1- (exactly_0 +exactly_1+exactly_1+exactly_3)
four_or_more # correct answer: 0.3179807662963867
```




    0.3179807662963867



Now, let's make it a little harder. Of course, a spare is also a fairly common outcome when playing bowling. Imagine that the probability of throwing a strike is 0.15, or a spare 0.25 and throwing anything else is 0.60.

What is the probability of exactly throwing 2 spares and 3 strikes?

In this case, it will not be possible to use combinations anymore, but you'll be able to use your permutations knowledge here!


```python
spare_strike =(factorial(10)/(factorial(2)*factorial(3)*factorial(5)))*(0.2**2*0.15**3*0.60**5)
spare_strike # correct answer: 0.026453951999999992
```




    0.026453951999999992


