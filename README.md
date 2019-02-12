# Assignment-15

# 1.You survey households in your area to find the average rent they are paying. Find the standard deviation from 
# the following data:
#$1550, $1700, $900, $850, $1000, $950

import statistics as stat
data =[1550,1700,900,850,1000,950]
Average = stat.mean(data)
print('The average rent paid is $', round(Average,2))
Population_std = round(stat.pstdev(data),2)
print('The standard deviation of the data is $', Population_std)

# 2. Find the variance for the following set of data representing trees in California 
# (heights in feet): 3, 21, 98, 203, 17, 9

Trees=[3,21,98,203,17,9]
Variance = stat.pvariance(Trees)
print('The variance of the data is -', Variance, 'feet')

# 3. In a class on 100 students, 80 students passed in all subjects, 10 failed in one subject, 7
# failed in two subjects and 3 failed in three subjects. Find the probability distribution of
# the variable for number of subjects a student from the given class has failed in.

import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
n_students = 100
passed_all = 80
failed_one = 10
failed_two = 7
failed_three = 3

num_students_not_passed_all = n_students - passed_all
prob_failed_none = passed_all / n_students
prob_failed_in_one = failed_one/n_students
prob_failed_in_two = failed_two/n_students
prob_failed_in_three = failed_three/n_students

print("Probability failed in no subjects: ",prob_failed_none)
print("Probability failed in 1 subject: ",prob_failed_in_one)
print("Probability failed in 2 subjects: ",prob_failed_in_two)
print("Probability failed in 3 subjects: ",prob_failed_in_three)


x = [prob_failed_none,prob_failed_in_one,prob_failed_in_two,prob_failed_in_three]
counts, bin_edges = np.histogram(x, bins=10, density= True)
pdf = counts/(sum(counts))
cdf = np.cumsum(pdf)

plt.figure(figsize=(8,4))

plt.subplot(1, 2, 1)
plt.plot(bin_edges[1:], pdf,label="PDF")
plt.plot(bin_edges[1:], cdf,label="CDF")
plt.legend()
plt.tight_layout()
plt.title("PDF/CDF of students with respect to subjects passed")
