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