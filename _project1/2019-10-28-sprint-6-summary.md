---
layout: post
title: The Sprint 6 Summary
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, professional proficiency]
date: 2019-10-28
color: brown
---

Actually this post is not going to summary the Sprint 6 working :) . Because I think that I did not do well for project in this particular moment. I was poisoning by a algorithm which called Genetical Algorithm. I was focused on this topic for whole weeks, although I finished the Sprint 6 task. I could not sleep well until I firgued out that it. During the 4 days of the week, I was working to 3 am and went sleep. So here I will put my final code just for a record my Sprint 6 working:

```python
%matplotlib inline
import matplotlib.pyplot as plt
import scipy
from scipy import misc
import numpy as np
import sys
import imageio
import skimage.transform
import random
import time

target = imageio.imread('./images/lena.png')

target = skimage.transform.resize(target, (50,50), mode = 'reflect', anti_aliasing = True) 

xDim = target.shape[0]
yDim = target.shape[1]

dim = xDim * yDim
target1D = target.flatten()

mutationRate = 0.0004 #0.01
populationSize = 500
generationLenght = 31001

def showImage(population, targetShape):
    bestSolutionImage = np.reshape(population, targetShape)
    plt.figure(figsize = (9, 6))
    plt.imshow(bestSolutionImage)
    plt.show()

def initialPopulation(populationSize, chromosomeLength):
    population = np.zeros(shape = (populationSize, chromosomeLength))
    for i in range(populationSize):
        population[i] = np.random.uniform(low = 0.0, high = 1.0, size = chromosomeLength)
    return population
        

def calculateFitness(initialPopulation, target):
    fitnessScores = np.zeros(shape = (populationSize))
    for i in range(len(fitnessScores)):
        fitnessScores[i] = np.linalg.norm(np.abs(np.subtract(target, initialPopulation[i])))
    return fitnessScores

def selectParents(population, scores, parentsSize):
    parents = np.zeros(shape = (parentsSize, dim))
    for i in range(parentsSize):
        minIndex = np.where(scores == np.min(scores))[0][0]
        parents[i] = population[minIndex]
        scores[minIndex] = 999
    return parents

def crossoverOffspring(parents, offspringSize):
    offsprings = np.zeros(shape = (offspringSize, dim))
    crossOverPoint = np.random.randint(0, offspringSize)
    for i in range(offspringSize):
        parentX = np.mod(i, parents.shape[0])
        parentY = np.mod(np.add(i, 1) ,parents.shape[0])
        offsprings[i, 0 : crossOverPoint] = parents[parentX, 0 : crossOverPoint]
        offsprings[i, crossOverPoint : ] = parents[parentY, crossOverPoint : ]
    return offsprings

def mutateOffsprings(offsprings, mutationRate):
    x = np.int8(np.multiply(mutationRate, dim))
    randomOrigin = np.random.randint(dim, size = x)
    randomTarget = np.random.randint(dim, size = x)
    for i in range(len(offsprings)):
        for j in range(x):
            offsprings[i][randomOrigin[j]] = offsprings[i][randomTarget[j]]
    return offsprings

start_time = time.time()

bestScoreProgress = []
solutionsList = []

population = initialPopulation(populationSize, dim)

scores = calculateFitness(population, target1D)

startScore = np.min(scores)
bestScoreProgress.append(startScore)

for generation in range(1, generationLenght):
    parents = selectParents(population, scores, populationSize // 2)
    offsprings = crossoverOffspring(parents, np.subtract(populationSize, len(parents)))
    mutatingOffsprings = mutateOffsprings(offsprings, mutationRate)
    
    population[0 : parents.shape[0], :] = parents
    population[parents.shape[0] : , :] = mutatingOffsprings
    
    scores = calculateFitness(population, target1D)
    
    endScore = np.min(scores)
    bestScoreProgress.append(endScore)
    
    bestSolution = population[np.where(scores == endScore)[0][0]]
    
    if np.mod(generation, 500) == 0:
        print('Generation', generation)
        showImage(bestSolution, target.shape)
        bestSolutionImage = np.reshape(bestSolution, target.shape)
        solutionsList.append(bestSolutionImage)


# Plot progress
import matplotlib.pyplot as plt
%matplotlib inline
plt.plot(bestScoreProgress)
plt.xlabel('Generation')
plt.ylabel('Best solution')
plt.show()

print("The total time of the programming runs is: %s seconds" % (time.time() - start_time))
print("The best solution score starts at ", startScore, ", ends at ", endScore)
```