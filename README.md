# matrix-problem
import matplotlib.pyplot as plt
import numpy as np
Num_sample = 10
Area =50
data = np.round(0+(Area-0)*np.random.random((2,Num_sample)))
plt.figure(1)
plt.plot(data[0,:],data[1,:],'ro')
for i in range(0,Num_sample):
    plt.text(data[0,i],data[1,i],str(i+1))
plt.title("marked data")
plt.grid(True)


dist = np.zeros((Num_sample,Num_sample))
nigh_matrix = np.zeros((Num_sample,Num_sample))
j=0
for i in range(0,10):
    for j in range(0,10):
        d=np.sqrt((np.square(data[0,j]-data[0,i]))+(np.square(data[1,j]-data[1,i])))
        dist[i,j]=np.round(d)

print('distance matrix : ')
print(dist)

for i in range(0,10):
    for j in range(0,10):
        if i!=j:
            if dist[i,j]<=25:
                nigh_matrix[i,j]=1
            else:
                nigh_matrix[i,j]=0

print('Neighbour Matrix')
print(nigh_matrix)
x=int(input("enter the number to check its neighbours:"))
c=[]
for j in range(0,10):
    if nigh_matrix[x,j]==1:
        print(j)
        c.append(j)
        j=j+1
print(c)
for k in range(0,len(c)):
    Lx=[data[0,x],data[0,c[k]]]
    Ly=[data[1,x],data[1,c[k]]]
    plt.plot(Lx,Ly)
plt.show()


    











