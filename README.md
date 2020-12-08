# Cosmo-Ages Sequence Calculator (CASC)

A simple bayesian approach for a set of gaussian ages in a sequence.

Age probabilities for each unit (e.g. each morainte) are calculated as:
```
P(t|T+>T>T-) ~ P(T|t) * P(t|t<T+) * P(t|t>T-)
```
Where T+, T and T- are the measured data corresponding to the older,
contemporary, and younger units. 
`P(t|t<T+)` and `P(t|t>T-)` are the product of
old-to-young and young-to-old cumulative sum of older and younger 
age distributions from other units, scaled between 0 and 1.

All distributions are scaled to fit a total probability of 1 for each
unit.

Gaussians are fitted to resulting distributions to produce symmetric ages
for the units.


---

Angel Rodes

SUERC 2020
