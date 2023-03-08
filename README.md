# Central Limit Theorem and Random Walks

### Introduction
The central limit theorem (CLT), in probability theory, states that adding together independent random variables will result in a sum that is properly normalized and tends towards a normal distribution or a "bell curve" even if the original variables are not normally distributed.   

To better understand the theorem, we can illustrate a scenario where 100 uniform random numbers are generated and summed to create a single number. This process is repeated 1000 times, resulting in 1000 sums of 100 uniform random numbers. According to the theorem, if a histogram is plotted using the values of these 1000 sums, the resulting distribution will closely resemble a normal distribution. The resemblance to a bell-shaped distribution will become more readily apparent as the number of sums increases (ie. 100000 instead of 1000 sums). Thus, reason for this project was to demonstrate the central limit theorem using *Python* and a couple of its libraries, *NumPy* and *Matplotlib*.

In order to properly demonstrate the CLT, we will code up a 'Random Walk'. A random walk is a randomly made path that is made up of random steps on some space. For our example we will create a random walk on the integer number line which starts at 0, and at each step moves +1 or −1 with equal probability. We will be displaying it on a one-dimensional space. 
<p>&nbsp;</p> 

### Code
*Creating a function that intakes two parameter arguments, number of steps and the start position:*

```
def RandomWalk(num_steps,start_position):
    walk = []
    direction =[-1,1]
    walk.append(start_position)
    for i in range(num_steps):
        a = np.random.choice(direction)
        walk.append(a)
    np.asarray(walk)
    return np.sum(walk)
```
<p>&nbsp;</p>

*Calling the function:*

```
RandomWalk(5,0)
RandomWalk(5,0)
RandomWalk(5,0)
```

*Output:*
```
1
3
-3
```

<p>&nbsp;</p>

*Next, we create another function that creates a vector, with each individual element being a result of our previous "Random Walk" function. We can simulate the random walks "num_sims" times*
```
def SimulateRandomWalk(num_sims,num_steps,start_position):
    walk = []
    for i in range(num_sims):
        a = RandomWalk(num_steps,start_position)
        walk.append(a)
    return np.asarray(walk)
```
<p>&nbsp;</p>

*Calling the function with five-hundred simulations of a random walk, each with ten steps and a starting position of 0*
```
SimulateRandomWalk(500, 10, 0)
```

*Output:*
```
array([  2,   2,   4,   6,  -2,   2,   0,   2,   8,  -2,  -4,   4,  -2,
         2,   0,   6,   0,   2,  -2,  -6,  -2,  -8,   2,   4,   4,  -6,
        -2,  -2,   0, -10,  -8,  -2,   6,   2,   2,  -2,   0,   2,  -8,
         6,   0,   6,   6,   2,   0,  -2,   2,  -2,  -4,   2,  -4,  -2,
         0,   2,  -2,   0,  -4,  -2,   2,  -6,  -2,   2,   6,   0,   0,
         2,   2,  -2,   0,  -6,   0,  -4,  -4,  -2,  -2,   2,  -2,   0,
        -2,  -6,   4,   2,   2,   2,   0,   6,   0,  -2,  -4,   0,   6,
         2,  -6,   6,   2,   2,   0,   0,  -2,   2,   0,   2,   4,  -2,
         2,   2,  -2,  -4,   4,   0,  -6,   0,   0,  -4,   0,  -2,   2,
         0,   6,   6,   0,  -4,   2,   0,   2,   2,  -4,  -2,  -2,   4,
         4,  -2,   2,   0,  -6,  -2,   4,   0,  -2,   4,   6,  -2,  -2,
         2,  -6,   6,   6,   0,   2,   4,  -6,   4,  -2,   4,  -4,   2,
         2,  -4,   4,  -2,  -2,   0,   4,  -4,   4,   4,   2,   2,   0,
         0,   2,   2,  -4,   0,  -2,   0,  -6,   2,  -2,   4,   0,   2,
         2,   4,  -4,   2,  -6,  -2,   6,   2,   0,   4,  -2,   6,   2,
         4,   2,   0,   2,  -2,  -2,   2,  -4,  -2,   0,   2,   0,  -4,
         0,   4,   2,  -2,   0,  -6,  -4,   2,  -2,   2,  -4,  -4,   2,
        -2,  -6,   0,  -8,  -2,   2,  -2,   2,  -4,   0,   0,  -2,   2,
         2,   2,   0,   0,  -2,   2,  -6,  -8,  -2,   2,   4,  -4,  -2,
        -2,   4,  -4,   0,  -2,   6,  -4,   6,  -2,   6,   2,  -4,   0,
         2,   4,   4,   2,   0,  -2,   0,   0,   0,   2,   4,  -2,   0,
         4,  -2,   4,   2,  -2,  -2,  -4,   2,  -2,  -4,   4,  -2,  -6,
         2,  -4,   0,  -4,  -8,   0,  -6,   2,   0,   4,   2,   0,  -2,
        -2,  -2,   0,  -2,   4,  -4,   0,   0,   2,   2,   2,   2,   2,
        -8,   4,  -2,  -4,   2,  -2,   2,   6,   0,   4,   4,  -2,   4,
         0,   4,   6,   2,  -4,  -8,   4,   0,   2,  -8,   0,   0,   0,
        -4,   8,  -6,  -4,   2,   2,   0,  -4,  -4,   2,  -4,   0,   0,
         0,  -2,   2,   4,   2,   0,   2,   0,   2,   0,   2,   2,   0,
         0,  -2,  -2,  -2,   0,   0,   0,   2,  -4,   0,   0,   6,  -4,
        -6,   4,   0,  -2,   4,  -2,  -2,  -2,   2,   2,   0,   2,   2,
        -2,   8,   2,   2,   4,  -2,   0,   2,  -2,   8,  -2,   2,  -2,
        -4,   2,  -4,   4,   0,   6,   6,  -2,   0,   4,  -4,   2,  -2,
        -4,   0,  -2,   0,  -2,   4,   2,   0,  -2,   0,  -6,   0,   6,
        -4,   0,  -2,   4,  -2,  -2,  -6,   4,   4,  -2,  -2,   2,  -4,
         8,   8,   2,   0,  -2,   2,   0,  -6,   2,   2,   0,   8,   0,
        -4,   2,   0,   2,  -2,   2,  -4,   2,  -2,  -2,   2,   8,   4,
         0,  -4,   4,  -4,  -4,  -2,   2,   2,  -4,   0,   4,  -2,  -4,
        -4,  -2,  -2,   2,  -2,   4,   2,  -2,  -4,  -2,  -2,   4,   2,
        -2,   2,   0,   0,   4,  -2])
```        
<p>&nbsp;</p>

*Creating a histogram of the simulations:*
```
x = SimulateRandomWalk(500, 10, 0)
plt.hist(x, bins = 50)
plt.show()
```

*Output:*  
![rwplot](https://user-images.githubusercontent.com/106455858/223662627-ce052bcc-9410-490a-a7d8-1713ac88c27f.png)

<p>&nbsp;</p>

*If we increase the amount of simulations and the number of steps of each random walk element within the vector:*
```
x = SimulateRandomWalk(1000,100,0)
plt.hist(x, bins = 100)
plt.show()
```
  
![rwplot2](https://user-images.githubusercontent.com/106455858/223662755-2c4e5239-6899-4e02-92fd-58dbfb2c6311.png)

*and finally,*
```
x = SimulateRandomWalk(5000,100,0)
plt.hist(x, bins = 100)
plt.show()
```
  
![rwplot3](https://user-images.githubusercontent.com/106455858/223662863-1592f870-cc14-4414-9dbc-c70a3974a106.png)

<p>&nbsp;</p>

### Conclusion  
It becomes obvious that a Gaussian distribution is being displayed as we increase the number of simulations of random walks within our function.

At the beginning, it is difficult to tell whether the histogram distribution is by chance or if values are actually converging towards a bell-shape. However, with the understanding of the central limit theorem and our continual increments of the values within the simulations and the simulations themselves, we were able to display the effect of the CLT in a digestible manner.
