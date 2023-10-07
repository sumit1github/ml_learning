# what is matplot lib
-> used for data visualization
-> helps to plot 2d and 3d graph
-> 


# install
pip install matplotlib

# ------------------------------------------- Bar Plot -------------------------------------------------

`note`
-> In the Bar Plot the x axis should be string format

`---------------------------------------- creating a basic bar chart-------=----------------------`
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('train.csv')
x = df['train_number'].to_list()
y = df['speed'].to_list()

new_x = [str(i) for i in x]

plt.xlabel("train no")
plt.ylabel("speed")
plt.title("Bar chart")
plt.bar(new_x,y)
plt.show()

`---------------------------------------- parameters -------=----------------------`

`<<<< width >>>>>`
plt.bar(new_x,y, width=0.2)

`<<<< Color >>>>>`

`for fixed number of bars`

color = ["red","green","blue","purple"]
plt.bar(new_x,y, width=0.2, color=color)

` radomly alocate color for unknown numbers of bars`

color = ["red","green","blue","purple"]
assign_color_list=[]

for i in range(len(x)-1):
    assign_color_list.append(random.choice(color))
print(assign_color_list)
plt.bar(new_x,y, width=0.2, color=assign_color_list)

`<<<< align >>>>>`
align = "edge" or "center"

plt.bar(new_x,y, width=0.4, align="edge")

`<<<< edgecolor >>>>>`
plt.bar(new_x,y, width=0.4, edgecolor="red")

`<<<< linewidth >>>>>`
plt.bar(new_x,y, width=0.4, edgecolor="red", linewidth=5)

--> combine with edgecolor to set the border width 

`<<<< linestyle >>>>>`
for dotted border
linestyle=":"