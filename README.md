# Cosmo-Ages Sequence Calculator (CASC)

A simple bayesian approach for a set of gaussian ages in a sequence.

Ángel Rodés, SUERC 2020

[www.angelrodes.com](www.angelrodes.com)

## How it works

Run CASC.m in MATLAB or Octave and select your input file.

### Input data

Copy your data in a `.csv` file with one header line:

```
Sample name , age , uncertainty , unit name ,  seqential order
```
Samples from the same unit have the same sequential order.

Avoid speces and symbols in sample names.

### Under the hood

Age probabilities for each unit (e.g. each morainte) are calculated as:
```
P(t|T+>T>T-) ~ P(T|t) * P(t|t<T+) * P(t|t>T-)
```
Where `T+`, `T` and `T-` are the measured data corresponding to the older,
contemporary, and younger units. 
`P(t|t<T+)` and `P(t|t>T-)` are the product of
old-to-young and young-to-old cumulative sum of older and younger 
age distributions from other units, scaled between 0 and 1.

All distributions are scaled to fit a total probability of 1 for each
unit.

Gaussians are fitted to resulting distributions to produce symmetric ages
for the units. (BGF, see https://github.com/angelrodes/CEAA)

### Graphical output

Two graphs are generated:

* A scatter + error bar graph with the data (black) and seuqential ages (blue)

![scatter plot](https://raw.githubusercontent.com/angelrodes/CASC/main/bars.png)

* A plot showing the camelplots correponding to the original data (in blue) and the sequential ages (in red)
