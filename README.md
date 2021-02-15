# Cosmo-Ages Sequence Calculator (CASC)

A simple Bayesian approach for a set of gaussian ages in a sequence.

Ángel Rodés, SUERC 2020
[www.angelrodes.com](www.angelrodes.com)

## How it works

* Install MATLAB or [Octave](https://www.gnu.org/software/octave/download) in your computer.
* Download the files `CASC.m` and `BFG.m` to the same folder as your `data.csv` (e.g. `Code`>`Download ZIP` and extract all files).
* Run CASC.m in MATLAB or Octave to compute a sequence of ages for samples listed in `data.csv`.

### Input data

Copy your data in a comma-separated file called `data.csv` with one header line:

```
Sample name , age , uncertainty , unit name ,  seqential order
```

`data.csv` can be created in Excel and save as .csv. Make sure to use `.` as decimal separator and `,` as the delimitter.

Samples from the same unit have the same sequential order. In case of a gap in the sequential corder (e.g. 1, 2, 4, 5), sequential ages will be calculated also for units with no data.

Avoid spaces and symbols in sample and unit names. For example, use "Moraine-1" instead of "Moraine 1".

## Under the hood

Age probabilities for each unit (e.g. each moraine) are calculated as:
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

## Graphical output

Two graphs are generated:

* A scatter + error bar graph with the data (black) and seuqential ages (blue)

![scatter plot](https://raw.githubusercontent.com/angelrodes/CASC/main/bars.png)

* A plot showing the [camelplots](https://cosmognosis.wordpress.com/2011/07/25/what-is-a-camel-diagram-anyway/) correponding to the original data (in blue) and the sequential ages (in red)


![camel plot](https://raw.githubusercontent.com/angelrodes/CASC/main/camels.png)
