# String


## Unicode

https://home.unicode.org/basic-info/overview/

The Unicode scalar value "\u{301}"


## Types of encoding `utf8`, `utf16`

https://swift.org/blog/utf8-string/


## Accessing the elements of a String using `String.Index`

```swift 
let fullName = "Alex Paul"
```

#### Accessing the first element

```swift 
print(fullName[fullName.startIndex]) // A
```

#### Access the last element in a String 

```swift 
print(fullName[fullName.index(before: fullName.endIndex)]) // l
```

#### Finding the first occurrence of a given element in a String 

```swift 
let spaceCharacterIndex = fullName.firstIndex(of: " ") ?? fullName.endIndex

let firstName = fullName[..<spaceCharacterIndex]

print(firstName) // "Alex"
```

#### Using `offsetBy:` to get a distance `String.Index`

```swift 
let str = "programming"

let firstIndex = str.startIndex

let distance = str.index(str.startIndex, offsetBy: 2)
print(str[firstIndex...distance]) // "pro"
```


## Substrings 

```swift 
let fullName = "Alex Paul"
```

#### `prefix`

```swift 
let prefix = fullName.prefix(3) // O(1)

print(prefix) // "Ale"
```

#### `hasPrefix`

```swift 
let fellows = ["Anabelle", "Josh", "Anna", "Anamarie", "Cathy"]

let matchesPrefix = fellows.filter { $0.hasPrefix("An") }

print(matchesPrefix) // ["Anabelle", "Anna", "Anamarie"]
```

## Converting a `String` to an array of `String`s or an array of `Character`s aka `String.Element`

```swift 
let charArr: [Character] = str.map { $0 } // creates Character array aka String.Element

let strArr = str.map { String($0) } // create a String array

let alsoCharArr: [String.Element] = Array(str) // also an array of String.Element or Character


print(charArr[0]) // p

print(strArr[0]) // p
```


## Writing to a file 

```swift 
let url = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask)[0].appendingPathComponent("Alex.txt")

print(url)

try? "Writing to a file".write(to: url, atomically: true, encoding: .utf8)
```

## Reading from a file 

```swift 
let url = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask)[0].appendingPathComponent("Alex.txt")

let output = (try? String(contentsOf: url)) ?? "no contents"

print(output) // "Writing to a file"
```


## Challenge 


1. Write the following text below to a file called `output.txt` in the sandbox documents directory. 

<pre> 
iOS apps is predominantly written using Objective-C. 
</pre> 

2. Read and print the contents of the `output.txt` file. 

3. We are in the current year of 2020 and no longer is this statement true. Update the output file to the following. 

<pre> 
iOS apps is predominantly written using Swift. 
</pre> 

4. Read and print the modified `output.txt` file. 
