## Imports
```
$ import matplotlib.pyplot as plt
```

## Plotting Data
```
$ with open('plot_data.csv', 'r') as csvfile:
    plots= csv.reader(csvfile, delimiter=',')
    for row in plots:
        x.append(float(row[0]))
        y.append(float(row[1]))


$ plt.plot(x,y, marker='o')

$ plt.title('Convergence Rate of Consensus')

$ plt.xlabel('Time in seconds')
$ plt.ylabel('Disk Distance')

$ plt.show()
```
