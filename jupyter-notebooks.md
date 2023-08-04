## iPython
- Jupyter notebooks is built on top of `iPython`, which has features like autocomplete, color, notebook way of writing code in terminal
```
$ ipython
```

## Jupyter Notebooks
- Built around cells: `markdown and code`
- Can render pics inside the notebook and plots
- Order doesn't have to be from top to bottom in cells like normal cells like normal programming in notebook/lab
- You can export notebooks as HTML, PDF 
- Local: Jupyter Notebooks/Lab; Cloud: Colab, Kaggle
- To install
```
$ pip install jupyterlab // local machine
$ !pip install wandb -q // cloud
```
- To run
```
$ jupyter notebook // local
```

## Jupyter Labs
- Newest version of jupyter notebooks
- To run 
```
$ jupyter lab // local
```

## Google Collab
- Same concept as notebook, but on cloud
- They call it Text instead of Markdown

## Kaggle
- You have `access to all public datasets` they have, pre-installed datascience libraries
- Easily import datasets from Kaggle to work on, visualize them
- Can `commit changes` to remote, add users
- You can create `docker` containers for dependencies for other kernels
- Can install python dependencies using `pip` or `github`
- Can have `public` and `private` notebooks

## Keyboard Shortcuts
- To run cells: ` shift + Enter `
- To run cells and stay inside them: ` ctrl + Enter `
- Navigation between cells
 ```
 $ arrow key
 $ j k // keys
 ```
- To exit cell: `esc key`
- Add cell: 
```
$ a // will add a cell above current cell
$ b // will add a cell below current cell
```
- To delete cell:
```
$ dd // delete current cell
```
- To change b/w code and markdown cells
```
$ esc + m // markdown
$ esc + y // code
```

## Terminal Commands
- You could run bash commands inside jupyter notebooks, all you need is to begin with `!`
```
$ !pip install seaborn
$ !ls
$ !cd <directory>; ls // run multiple commands
$ !cowsays "Hussein is coool!" // print string above cow 
```

## Magic Commands
- there are some magic commands in jupyter notebooks that start with `%`, although you can use it instead of `!` as well
```
$ %pip install seaborn
$ %history -on 
```

## Find and Replace
- If you go to `edit->find and replace`, you can use this feature for replacing namespaces
- Can use regex
- ex replace `df` into `social_df`

## Pandas
- To change max displayed lines in `Pandas` when running `df.head()`
```
$ pd.options.display.max_rows = 100 / default 50
```

## Setting up alerts when Cells finished
```
$ !pip install jupyternotify
$ %load_ext jupyternotify // magic command to load in installed library
%%notify // tell cell when this finishes send me a notification, put on top of cell (maybe)
```

## Create Slides 
- For internal company meetings, can easily create a slideshow
- Go to `view --> cell toolbar --> slideshow`
- Set headers as `slide`, and code cells as `fragments`
