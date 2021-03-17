# MarkovChains

import random

dict1 = {'burger': [0.2,0.6,0.2] , 'pizza': [0.3,0,0.7], 'hotdog': [0.5,0,0.5]}

def markov_standard_distribution(dict1,x,state):    # dict1 is markov chain model,x is the number of days, state is initial state
    def prob(lst):                                  # prob is HOF which takes in list of probabilities and outputs an index corresponding to a new probability
      p = random.random()
      adder,counter = 0,0
      for i in lst:
          adder += i
          counter += 1
          if adder > p:
              return counter-1                      # output index corresponding to new probability
    lst = [0]*len(dict1)                            # list to count the occurences of a state
    for i in range(x):                              # iterate through the total number of days
        index = prob(dict1[state])                  # index of new probability
        lst[index] += 1                             # count the occurence of this probability     
        state = list(dict1)[index]                  # change the state to the new state for the next iteration
    for i in range(len(lst)):                  
        lst[i] = (lst[i])/x                         # replace entries in list with new entries corresponding to probability at equilibrium state 
    return lst




##print(markov_standard_distribution(dict1,100,'burger'))
##print(markov_standard_distribution(dict1,1000,'burger'))
##print(markov_standard_distribution(dict1,10000,'burger'))
##print(markov_standard_distribution(dict1,100000,'burger'))
