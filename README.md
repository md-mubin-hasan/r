# R Programming Guide

## Basic R Codes with Explanations

### 1. Variables and Data Types

```r
# Creating variables
name <- "John"           # Character/String variable
age <- 25               # Numeric variable
height <- 5.9           # Decimal/Float variable
is_student <- TRUE      # Logical/Boolean variable

# Checking data types
class(name)             # Returns "character"
class(age)              # Returns "numeric"
class(is_student)       # Returns "logical"

# Printing values
print(name)             # Displays: "John"
cat("Hello, ", name)    # Alternative print method
```

### 2. Vectors

```r
# Creating vectors
numbers <- c(1, 2, 3, 4, 5)           # Numeric vector
letters_vec <- c("a", "b", "c")       # Character vector
logical_vec <- c(TRUE, FALSE, TRUE)   # Logical vector

# Creating sequences
seq_1_to_10 <- 1:10                   # Sequence from 1 to 10
seq_2_to_20 <- seq(2, 20, by=2)       # Sequence from 2 to 20 by step 2

# Vector operations
sum(numbers)                           # Sum: 15
mean(numbers)                          # Mean: 3
length(numbers)                        # Length: 5
max(numbers)                           # Maximum: 5
min(numbers)                           # Minimum: 1

# Accessing vector elements
numbers[1]                             # First element: 1
numbers[c(1, 3, 5)]                   # 1st, 3rd, 5th elements: 1 3 5
```

### 3. Lists

```r
# Creating a list (can contain different data types)
my_list <- list(name = "Alice", age = 30, scores = c(85, 90, 78))

# Accessing list elements
my_list$name                           # "Alice"
my_list[["age"]]                       # 30
my_list$scores                         # c(85, 90, 78)

# Modifying list elements
my_list$age <- 31                      # Change age to 31
my_list$city <- "New York"             # Add new element
```

### 4. Data Frames

```r
# Creating a data frame
df <- data.frame(
  Name = c("John", "Jane", "Bob"),
  Age = c(25, 28, 35),
  Score = c(85, 92, 78)
)

# Accessing data frame elements
df$Name                                # Access column by name
df[1, ]                                # First row
df[, 2]                                # Second column
df[1, 2]                               # Element at row 1, column 2

# Basic data frame info
nrow(df)                               # Number of rows: 3
ncol(df)                               # Number of columns: 3
head(df)                               # First few rows
str(df)                                # Structure of data frame
```

### 5. Conditional Statements (if, else)

```r
# Simple if statement
age <- 20
if (age >= 18) {
  print("Adult")
}

# if-else statement
if (age >= 18) {
  print("Adult")
} else {
  print("Minor")
}

# if-else if-else statement
if (age < 13) {
  print("Child")
} else if (age < 18) {
  print("Teenager")
} else {
  print("Adult")
}
```

### 6. Loops

```r
# for loop
for (i in 1:5) {
  print(i)                             # Prints: 1, 2, 3, 4, 5
}

# for loop with vector
fruits <- c("apple", "banana", "cherry")
for (fruit in fruits) {
  print(fruit)
}

# while loop
count <- 1
while (count <= 5) {
  print(count)
  count <- count + 1
}

# repeat loop with break
x <- 1
repeat {
  print(x)
  x <- x + 1
  if (x > 5) break                    # Exit loop when x > 5
}

# next (skip to next iteration)
for (i in 1:5) {
  if (i == 3) next                    # Skip iteration when i = 3
  print(i)                            # Prints: 1, 2, 4, 5
}
```

### 7. Functions

```r
# Creating a simple function
add <- function(a, b) {
  return(a + b)
}
add(5, 3)                              # Returns: 8

# Function with default parameters
greet <- function(name = "User") {
  return(paste("Hello,", name))
}
greet()                                # "Hello, User"
greet("Alice")                         # "Hello, Alice"

# Function that returns multiple values
stats <- function(x) {
  return(list(mean = mean(x), 
              sum = sum(x), 
              length = length(x)))
}
result <- stats(c(1, 2, 3, 4, 5))
result$mean                            # 3
```

### 8. Matrices

```r
# Creating a matrix
mat <- matrix(1:9, nrow = 3, ncol = 3)

# Matrix operations
dim(mat)                               # Dimensions: 3 3
t(mat)                                 # Transpose
mat[1, 2]                              # Element at row 1, column 2
mat[1, ]                               # First row
mat[, 1]                               # First column

# Matrix arithmetic
mat + 10                               # Add 10 to each element
mat * 2                                # Multiply each element by 2
mat %*% mat                            # Matrix multiplication
```

### 9. String Operations

```r
# String manipulation
str1 <- "Hello"
str2 <- "World"

# Concatenate strings
paste(str1, str2)                      # "Hello World"
paste(str1, str2, sep = "-")          # "Hello-World"

# String length
nchar(str1)                            # 5

# Extract substring
substr(str1, 1, 3)                     # "Hel"

# Convert to uppercase/lowercase
toupper(str1)                          # "HELLO"
tolower(str1)                          # "hello"

# Replace substring
gsub("World", "R", "Hello World")     # "Hello R"
```

### 10. Apply Family Functions

```r
# apply() - apply function to rows or columns of matrix
mat <- matrix(1:9, nrow = 3)
apply(mat, 1, sum)                     # Sum of each row
apply(mat, 2, mean)                    # Mean of each column

# lapply() - apply function to list, returns list
lapply(c(1, 2, 3), function(x) x * 2) # list(2, 4, 6)

# sapply() - apply function to list, returns vector
sapply(c(1, 2, 3), function(x) x * 2) # c(2, 4, 6)

# mapply() - apply function to multiple arguments
mapply(function(x, y) x + y, c(1, 2, 3), c(10, 20, 30))
```

### 11. Factor and Levels

```r
# Creating a factor (categorical data)
gender <- factor(c("M", "F", "M", "F", "M"))

# Viewing levels
levels(gender)                         # "F" "M"

# Accessing factor properties
as.numeric(gender)                     # Numeric representation
nlevels(gender)                        # Number of levels: 2

# Creating factor with custom levels
status <- factor(c("low", "high", "medium"),
                levels = c("low", "medium", "high"))
```

### 12. Basic Statistics

```r
# Summary statistics
data <- c(10, 15, 20, 25, 30, 35, 40)

sum(data)                              # Total: 175
mean(data)                             # Average: 25
median(data)                           # Middle value: 25
sd(data)                               # Standard deviation
var(data)                              # Variance
quantile(data)                         # Quartiles

# Basic summary
summary(data)                          # Min, Q1, Median, Q3, Max
```

### 13. Working with Files

```r
# Write data to file
write.csv(df, "data.csv", row.names = FALSE)

# Read data from file
df_read <- read.csv("data.csv")

# Write to text file
write.table(df, "data.txt", sep = "\t")

# Read from text file
df_read <- read.table("data.txt", sep = "\t", header = TRUE)
```

### 14. Logical Operations

```r
# Logical operators
a <- TRUE
b <- FALSE

a & b                                  # AND: FALSE
a | b                                  # OR: TRUE
!a                                     # NOT: FALSE

# Comparison operators
5 > 3                                  # TRUE
5 == 5                                 # TRUE
5 != 3                                 # TRUE

# Logical operations on vectors
vec <- c(1, 2, 3, 4, 5)
vec > 3                                # FALSE FALSE FALSE TRUE TRUE
vec[vec > 3]                           # c(4, 5) - subset vector
```

### 15. Error Handling

```r
# Try-catch error handling
result <- tryCatch({
  x <- 10 / 2                          # No error
  print(x)
}, error = function(e) {
  print("An error occurred!")
}, warning = function(w) {
  print("A warning occurred!")
})

# Check for NA values
is.na(NA)                              # TRUE
is.null(NULL)                          # TRUE
```

---

## Tips
- Use `?function_name` to get help on any function
- Use `head()` to preview data
- Use `str()` to check data structure
- Use `summary()` for statistical summaries
