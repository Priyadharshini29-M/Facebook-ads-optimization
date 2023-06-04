# Facebook-ads-optimization
To optimize the histogram of facebook ads selection
#IMPORTING LIBRARIES
mport numpy as np
import matplotlib.pyplot as plt
import pandas as pd
#IMPORTING DATASET
dataset = pd.read_csv('Facebook Ads Optimization TSA.csv')
#UPPER CONFIDENCE BOUND
#TSA AD OPTIMIZATION
#IMPLEMENTATION
import random
N = 400
num_ads = 10
ads_selected = []
num_of_rewards_1 = [0] * num_ads
num_of_rewards_0 = [0] * num_ads
total_reward = 0
for n in range(0, N):
  ad=0
  max_random = 0
  for i in range (0, num_ads):
    random_beta = random.betavariate(num_of_rewards_1[i]+1, num_of_rewards_0[i]+1)
    if(random_beta>max_random):
      max_random = random_beta
      ad = i
      ads_selected.append(ad)
      reward = dataset.values[n, ad]
      if reward == 1:
       num_of_rewards_1[ad] = num_of_rewards_1[ad]+1
else:
    num_of_rewards_0[ad] = num_of_rewards_0[ad]+1
    total_reward = total_reward + reward
#HISTOGRAM VISUALIZATION
plt.hist(ads_selected)
plt.title('Histogram of Facebook Ads Selections')
plt.xlabel('Ads Number')
plt.ylabel('slection time of each ad')
plt.show()




