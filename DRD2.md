# DNA and RNA dynamics - part 2 doctormariagiuliabacalini

## Introduction
* We will prepare a report (:/)
* We will use mainly R
* The CRAN repository has general statistics packages
* Bioconductor is a repository for bioinformatics R packages
* Contributed packages are not always reliable!

## Workspaces, objects, syntax
* Comments are rendered with `#`
* Spaces are ignored except that in variable and function names
* The R workspace contains
* An R object is a variable
	* It cannot contain special characters except for underscore and dot
	* It needs to start with a letter
	* It can be a good idea to always start variables with capital, so to not mix them up with function
	* Objects are assigned with the assignment operator `<-` or `=`
	* In R the operator `<-` is preferred since `=` can be mistaken by `==`
* Data types can be symple or aggregated
* Simple: integer, float, string, boolean, factors, NA (missing data)
* Aggregated: vector (made of numbers or factors), list (made of any datatype), matrix (2 dimensional and numerical), dataframe (2 dimensional and of any type)
* Even a number is actually a vector of lenght 1
* In dataframes columns and rows have names
* A factor is a categorical variable
	* It is like a string but without quotes
	* They can be put in a vector
	* A list of strings can be converted in a vector of factors with `factor(list)`
	* The function `levels(vector)` returns the possible categorical values
* In dataframes all the strings are converted to factors
	* This is memory effective since a single categorical variable is represented by just one integer irrespective of its lenght!
* Logical operators
	* Not x `!x`
	* Or `|`
	* And `&`
	* `isTRUE(x)` returns True if the expression x is true
	* `x %in% y` returns true if x is a subset of y
* Indeces
	* A vector is indexed as `v[i]`
	* A matrix or dataframe as `M[i,j]`
* Exploratory functions are particularly useful for dataframes

