# go-monads
go-monads is a library that implements basic Haskell monads, based on Go 2 Generics Draft.

## Table of Contents

* [Maybe(T)](#maybet)

## Maybe(T)

### Create Maybe
```go
x := Return(int)(5)

or

val := new(int)
x := OfNullable(int)(val)

or

x := Empty(struct{})()
```

### Transform Maybe into new value
```go
x := Return(int)(5)
fmt.Println(Map(int, string)(x, fmt.Sprint))

or

func divideBy(x int, y int) Maybe(int) {
  if y == 0 { 
    return Empty(int)() 
  }
  return Return(int)(x/y)
}
four := Map(int, int)(divideBy(6, 3), func (x int) { return x * 2 }) //four equals Just{obj: 4}
nothing := Map(int, int)(divideBy(6, 0), func (x int) { return x * 2 }) //nothing equals Nothing{}
```