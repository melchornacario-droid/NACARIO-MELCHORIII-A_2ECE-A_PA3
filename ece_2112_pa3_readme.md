# ECE 2112: Programming Assignment 3 - Python Data Analysis (Pandas)

This repository contains the solution for Experiment 3 in ECE 2112 (Advanced Computer Programming and Algorithms). The assignment demonstrates data loading, indexing, slicing, and conditional Boolean filtering using the Pandas library in Python.

## Problem A (POSITIONAL AND LABEL-BASED SLICING)

Load the `cars.csv` dataset into a Pandas DataFrame named `cars`. Display its shape and complete list of column names. Using positional slicing with `.iloc`, create `cars_6_to_10` containing rows 6 through 10 of the dataset (where row 1 is the first data row, corresponding to index `0`). From `cars_6_to_10`, extract and display only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear` using label-based indexing with `.loc`.

The following functions and methods were used in this problem:

* `pd.read_csv()` - Loads a comma-separated values (CSV) file into a Pandas DataFrame.

  Example: `cars = pd.read_csv('cars.csv')`

* `.columns` - Returns an Index object containing the column labels of the DataFrame.

  Example: `cars.columns` $\rightarrow$ `Index(['Model', 'mpg', 'cyl', 'disp', 'hp', 'drat', 'wt', 'qsec', 'vs', 'am', 'gear', 'carb'], dtype='object')`

* `.shape` - Returns a tuple indicating the dimensions (number of rows, number of columns) of the DataFrame.

  Example: `cars.shape` $\rightarrow$ `(32, 12)`

* `.iloc[]` - Performs positional (integer-location based) indexing to slice rows by numerical index range.

  Example: `cars_6_to_10 = cars.iloc[5:10]` $\rightarrow$ extracts index positions 5 through 9 (rows 6 to 10).

* `.loc[]` - Performs label-based indexing to select specific column names across rows in a DataFrame subset.

  Example: `cars_6_to_10columns = cars_6_to_10.loc[:, ["Model", "mpg", "cyl", "hp", "gear"]]`

These functions were used to load the dataset, inspect DataFrame attributes, extract specific rows using integer positions, and isolate requested columns using label-based indexing:

```python
cars = pd.read_csv('cars.csv')
print(cars.columns)
print(cars.shape)
print(cars)
cars_6_to_10 = cars.iloc[5:10]
print()
print(cars_6_to_10)
print()
cars_6_to_10columns = cars_6_to_10.loc[:, ["Model", "mpg", "cyl", "hp", "gear"]]
print(cars_6_to_10columns)
```

Output
```pyhton
Index(['Model', 'mpg', 'cyl', 'disp', 'hp', 'drat', 'wt', 'qsec', 'vs', 'am',
       'gear', 'carb'],
      dtype='object')
(32, 12)
                  Model   mpg  cyl   disp   hp  drat     wt   qsec  vs  am  gear  carb
0             Mazda RX4  21.0    6  160.0  110  3.90  2.620  16.46   0   1     4     4
1         Mazda RX4 Wag  21.0    6  160.0  110  3.90  2.875  17.02   0   1     4     4
2            Datsun 710  22.8    4  108.0   93  3.85  2.320  18.61   1   1     4     1
3        Hornet 4 Drive  21.4    6  258.0  110  3.08  3.215  19.44   1   0     3     1
4     Hornet Sportabout  18.7    8  360.0  175  3.15  3.440  17.02   0   0     3     2
5               Valiant  18.1    6  225.0  105  2.76  3.460  20.22   1   0     3     1
6            Duster 360  14.3    8  360.0  245  3.21  3.570  15.84   0   0     3     4
7             Merc 240D  24.4    4  146.7   62  3.69  3.190  20.00   1   0     4     2
8              Merc 230  22.8    4  140.8   95  3.92  3.150  22.90   1   0     4     2
9              Merc 280  19.2    6  167.6  123  3.92  3.440  18.30   1   0     4     4
10            Merc 280C  17.8    6  167.6  123  3.92  3.440  18.90   1   0     4     4
11           Merc 450SE  16.4    8  275.8  180  3.07  4.070  17.40   0   0     3     3
12           Merc 450SL  17.3    8  275.8  180  3.07  3.730  17.60   0   0     3     3
13          Merc 450SLC  15.2    8  275.8  180  3.07  3.780  18.00   0   0     3     3
14   Cadillac Fleetwood  10.4    8  472.0  205  2.93  5.250  17.98   0   0     3     4
15  Lincoln Continental  10.4    8  460.0  215  3.00  5.424  17.82   0   0     3     4
16    Chrysler Imperial  14.7    8  440.0  230  3.23  5.345  17.42   0   0     3     4
17             Fiat 128  32.4    4   78.7   66  4.08  2.200  19.47   1   1     4     1
18          Honda Civic  30.4    4   75.7   52  4.93  1.615  18.52   1   1     4     2
19       Toyota Corolla  33.9    4   71.1   65  4.22  1.835  19.90   1   1     4     1
20        Toyota Corona  21.5    4  120.1   97  3.70  2.465  20.01   1   0     3     1
21     Dodge Challenger  15.5    8  318.0  150  2.76  3.520  16.87   0   0     3     2
22          AMC Javelin  15.2    8  304.0  150  3.15  3.435  17.30   0   0     3     2
23           Camaro Z28  13.3    8  350.0  245  3.73  3.840  15.41   0   0     3     4
24     Pontiac Firebird  19.2    8  400.0  175  3.08  3.845  17.05   0   0     3     2
25            Fiat X1-9  27.3    4   79.0   66  4.08  1.935  18.90   1   1     4     1
26        Porsche 914-2  26.0    4  120.3   91  4.43  2.140  16.70   0   1     5     2
27         Lotus Europa  30.4    4   95.1  113  3.77  1.513  16.90   1   1     5     2
28       Ford Pantera L  15.8    8  351.0  264  4.22  3.170  14.50   0   1     5     4
29         Ferrari Dino  19.7    6  145.0  175  3.62  2.770  15.50   0   1     5     6
30        Maserati Bora  15.0    8  301.0  335  3.54  3.570  14.60   0   1     5     8
31           Volvo 142E  21.4    4  121.0  109  4.11  2.780  18.60   1   1     4     2

        Model   mpg  cyl   disp   hp  drat    wt   qsec  vs  am  gear  carb
5     Valiant  18.1    6  225.0  105  2.76  3.46  20.22   1   0     3     1
6  Duster 360  14.3    8  360.0  245  3.21  3.57  15.84   0   0     3     4
7   Merc 240D  24.4    4  146.7   62  3.69  3.19  20.00   1   0     4     2
8    Merc 230  22.8    4  140.8   95  3.92  3.15  22.90   1   0     4     2
9    Merc 280  19.2    6  167.6  123  3.92  3.44  18.30   1   0     4     4

        Model   mpg  cyl   hp  gear
5     Valiant  18.1    6  105     3
6  Duster 360  14.3    8  245     3
7   Merc 240D  24.4    4   62     4
8    Merc 230  22.8    4   95     4
9    Merc 280  19.2    6  123     4
```

## Problem B (MODEL LOOKUP)

Use Boolean indexing on the `Model` column of the `cars` DataFrame to locate specific vehicle records without hard-coding row indices. Extract the complete row for `Toyota Corolla` and store the result in `toyota`. Extract only the columns `Model`, `mpg`, `hp`, and `wt` for `Pontiac Firebird` and store the result in `pontiac`.

The following functions and methods were used in this problem:

* `Boolean Indexing` - Evaluates a conditional comparison against column values to construct a boolean mask (`True`/`False`).

  Example: `cars["Model"] == "Toyota Corolla"` $\rightarrow$ evaluates `True` for matching rows.

* `Bracket Selection` - Passes a boolean mask directly into the DataFrame to filter and retrieve matching rows.

  Example: `toyota = cars[cars["Model"] == "Toyota Corolla"]`

* `.loc[]` - Combines boolean row filtering with explicit column label selection in a single operation.

  Example: `pontiac = cars.loc[cars["Model"] == "Pontiac Firebird", ['Model', 'mpg', 'hp', 'wt']]`

These functions were used to dynamically filter DataFrame rows based on string conditions and extract specific attribute subsets without referencing static row indices:

```python
toyota = cars[cars["Model"] == "Toyota Corolla"]
pontiac = cars.loc[cars["Model"] == "Pontiac Firebird", ['Model', 'mpg', 'hp', 'wt']]

print(toyota)
print(pontiac)
```

Output
```python
Model   mpg  cyl  disp  hp  drat     wt  qsec  vs  am  gear  carb
19  Toyota Corolla  33.9    4  71.1  65  4.22  1.835  19.9   1   1     4     1

               Model   mpg   hp     wt
24  Pontiac Firebird  19.2  175  3.845
```

## Problem C (MULTI-MODEL SUBSETTING)

Create a DataFrame named `selected_cars` containing records for three models: `Datsun 710`, `Lotus Europa`, and `Ferrari Dino`. Retain only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear`. Verify that the resulting subset DataFrame satisfies the required $3 \times 5$ dimension check by displaying `selected_cars` and its shape.

The following functions and methods were used in this problem:

* `Bitwise OR Operator (|)` - Chains multiple boolean conditions together to filter rows matching any of the specified criteria.

  Example: `(cars["Model"] == 'Datsun 710') | (cars["Model"] == 'Lotus Europa') | (cars["Model"] == 'Ferrari Dino')`

* `.loc[]` - Selects rows matching combined logical conditions while filtering for specified column labels.

  Example: `selected_cars = cars.loc[condition, ['Model', 'mpg', 'cyl', 'hp', 'gear']]`

* `.shape` - Displays the row and column dimensions of the filtered DataFrame to confirm exact output specifications.

  Example: `selected_cars.shape` $\rightarrow$ `(3, 5)`

These functions were used to construct multi-condition row filters, extract target feature columns, and confirm that the final DataFrame contains exactly 3 rows and 5 columns:

```python
selected_cars = cars.loc[(cars["Model"] == 'Datsun 710') | (cars["Model"] == 'Lotus Europa') | (cars["Model"] == 'Ferrari Dino'), ['Model', 'mpg', 'cyl', 'hp', 'gear']]
print(selected_cars)
print(selected_cars.shape)
```

Output
```python
Model   mpg  cyl   hp  gear
2     Datsun 710  22.8    4   93     4
27  Lotus Europa  30.4    4  113     5
29  Ferrari Dino  19.7    6  175     5
(3, 5)
```
