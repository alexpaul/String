# String

Swift String. 

## Unicode


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


Write the following text below to a file called `Output.txt` in the sandbox documents directory. 

<pre> 
iOS apps is predominantly written using Objective-C. 
</pre> 

We are in the current year of 2020 and no longer is this statement true. Update the output file to the following. 

<pre> 
iOS apps is predominantly written using Swift. 
</pre> 
