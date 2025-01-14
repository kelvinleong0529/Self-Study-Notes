# **Make VS New**
## **Similarities**
- both are building functions that allocates memory to instantiate variable for given type

## **Data Types**
- `make()` only works with **slices, maps and channels**
- `new()` works with any data types
```golang
s := make([]int,0)
m := make(map[int]int)
c := make(chan bool)

i := new(int)
```

## **Returned Types**
- `make()` returns the target type
- `new()` returns the address (returns a pointer to nil)
```golang
var v map[int]int = make(map[int]int)
var p *map[int]int = new(map[int]int)
```

## **Memory Initialization**
- `make()` initializes memory
- `new()` zeros memory
```golang
var mMake map[int]int = make(map[int]int) // Initializes a map
var mNew *map[int]int = new(map[int]int) // Doesnt initialize a map object, zeros a map pointer to nil

mMake[0] = 1    // Runs
(*mNew)[0] = 1  // Crashes, because map object hasnt been instantiated yet, and we are dereferencing a nil pointer
```

# **Go Build**
- `go build` is used to compile packages and dependencies that we have defined / used in our project
- when compiling packages, `build` ignores files that end in **_test.go**
- if we specify a single file as argument it treats as a single package, but if the arguments are a list of .go files then all the source should be specifying / pointing to a single package


```golang
go build -ldflags="flag" sourcefile.go
```
- the **flag** above is related to the linker (**ld** stands for linker), this flag is the overall used flag as it inserts **dynamic information** at build time in our binary file
```golang
// main.go
var mainPackageVariable string

func main() {
    fmt.Println("Main Package Variable"=,mainPackageVariable)
}

// sub.go
var subPackageVariable string

func main() {
    fmt.Println("Sub Package Variable=",subPackageVariable)
}
```

# **Go Vet**
- `go vet` tool has the ability to check for invalid conversions between `unsafe.Pointer` and `uintptr` types