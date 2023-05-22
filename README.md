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
```go
// Array fixed-length
[3]string

// Slice variable-length
[]string
```

- Data Structures
```go
// Defining a struct
type person struct {
    firstName string
    lastName  string
}

// Instantiating a struct
func main() {
    // 1. Simple initialization (not recommended as bug can occur when variables position is swapped)
    p1 := person{"Bernard", "Ang"}
    
    // 2. Named variables initialization (it is more structured)
    p2 := person{firstName: "Bernard", lastName: "Ang"}
}
```

#### Passing Arguments
- By default, Go passes arguments into function calls using `Call by Value` as compared to `Call by Reference`
```go
type person struct {
    firstName string
    lastName string
}

// This will work, but will not update
// Reason is because the update is done at the copied person object
func (p person) updateFirstName(newFirstName string) {
    p.firstName = newFirstName
}

// To persist changes on the same object, we can make use of pointers
// Reason is because the update is done on the same person object that is referenced in the memory
func (p *person) updateLastName(newLastName string) {
    p.lastName = newLastName
}
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

## Testing
- We can perform unit testing for `.go` codes we have written
- Testing in Go is different from testing in other languages, there are not much handholding and the testing tools that is provided by `Google` is minimalistic
  - Concept is similar to how code is written in Go

### Convention
- Tests for the codes have a file naming convention
  - Assuming that I have a set of codes in `deck.go`, the test file name should be `deck_test.go`
- Test functions should be capitalized and starting with `Test<name>`

### Examples
```go
package main

import "testing"

func TestNewDeck(t *testing.T) {
    d := newDeck()
    
    if len(d) != 52 {
      t.Errorf("Expected deck length of 52, but got %v", len(d))
    }
}
```
