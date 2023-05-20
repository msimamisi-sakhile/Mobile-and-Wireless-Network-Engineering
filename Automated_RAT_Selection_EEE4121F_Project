import numpy as np 

import matplotlib.pyplot as plt 

 

def main(): 

    MIN_WEIGHT = 0 

    MAX_WEIGHT = 10 

    global statistic 

     

    num_users = eval(input("Enter the number of user in the network\n")) 

    num_criterias = 3; 

    weights_arr_size =(num_users,num_criterias) 

    user_arrays = generate_weights(MIN_WEIGHT,MAX_WEIGHT,weights_arr_size) 

     

    statistic = np.zeros((5,), dtype=int) # Keeps track of handoff calls accepted by each RAT 

    norm_matrix = [np.array([0.1,0.002,0.0008]),np.array([0.135,0.002,0.0008]),np.array([0.167,0.02, 

0.0033]),np.array([1,1,1]),np.array([0.333,0.007,0.0007])] 

    choose_RAT(calc_ranking_values(user_arrays,norm_matrix)) 

     

    print(statistic) 

    plot_results(statistic) 

     

def generate_weights(MIN_WEIGHT,MAX_WEIGHT,size): 

    opt_1 = "To investigate a certain criteria enter:\n [1]-Cost\n [2]-Delay\n [3]-Bandwidth\n\n" 

    opt_2 = "Otherwise just randomize:[4]-Random\n" 

    opt = eval(input(opt_1+opt_2)) 

     

    arr_weights = np.random.randint(MIN_WEIGHT,MAX_WEIGHT,size) 

     

    if opt == 1: 

        max_min = eval(input("Does the user care about Cost? [1]-Yes [2]-No\n")) 

        if max_min == 1: 

            arr_weights[0] = 9 

        elif max_min == 2: 

            arr_weights[0] = 0 

    elif opt == 2: 

        max_min = eval(input("Does the user care about Delay? [1]-Yes [2]-No\n")) 

        if max_min == 1: 

            arr_weights[1] = 0 

        elif max_min == 2: 

            arr_weights[1] = 9   

    elif opt == 3: 

        max_min = eval(input("Does the user care about Bandwidth? [1]-Yes [2]-No\n")) 

        if max_min == 1: 

            arr_weights[2] = 9 

        elif max_min == 2: 

            arr_weights[2] = 0 

    else: 

        arr_weights = arr_weights 

     

    return arr_weights 

     

# Calculates the RAT ranking values for each user 

def calc_ranking_values(user_arrays, norm_dec_matrix): 

    ranking_values_all_users = [] 

    for i in range(len(user_arrays)): 

        ranking_values_one_user = [] 

        for j in range(len(norm_dec_matrix)): 

            ranking_values_one_user.append(round(np.sum(user_arrays[i]*norm_dec_matrix[j]),3)) 

        ranking_values_all_users.append(ranking_values_one_user) 

    return ranking_values_all_users 

 

# Chooses best RAT based on the ranking values 

def choose_RAT(ranking_values_array): 

    for i in range(len(ranking_values_array)): 

        max_value = np.array(ranking_values_array[i]).max() 

        RAT_num = ranking_values_array[i].index(max_value) 

        statistic[RAT_num]+=1 

 #print("RAT-",RAT_num+1," has been chosen by User-",i+1,".",sep="") 

 

# Plot bar graph of results 

def plot_results(statistic): 

    RATs = ["2G","3G","4G","5G","WiFi"] 

    plt.bar(RATs,statistic) 

    plt.xlabel("RATs") 

    plt.ylabel("No. of handoff calls accepted")  
    
    
main()
