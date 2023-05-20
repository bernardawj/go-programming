# Go Programming

## Description
This repository contains my learning progress in Go language.

## Build
- Commands

### Commands
- `Build App`
```shell
# Single file
go run main.go

# Multiple files
go run main.go deck.go
```

## Usage
- Package
- Imports
- Functions

### Package
- Defines a folder of `.go` files
- Files within the same package can be shared without the need for importing
```go
package main

// imports

// func main
```

### Imports
- Defines the package to be imported
- Imported package can be used even though they do not have the same package name
```go
// package

import (
    "fmt"
)

// func main
```

### Function
- Defines a function that can be called upon
- Every project will require a default function called `main`
```go
// package

// import

func main() {
    // code..
}
```

## Data Types
- Basic Types
```
bool
string
byte
int
float64
```

- Advanced Types
```
# Array fixed-length
[3]string

# Slice variable-length
[]string
```

## Receivers
- Used during the creation of custom functions
  - Avoid `this` or `self` for the naming of variables, even though it is allowed
```go
package main

type deck []string

func (d deck) print() {
    // code..
}

func main() {
    // Instance of the type can call the `print` function
    cards := deck{"1S", "2H", "3C"}
    cards.print()
}
```