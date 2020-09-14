# String

A `String` is a collection of characters. A `Character` is made up of one or more Unicode scalar values. 

#### String initialization

```swift 
let aString = "Hello, developers." // literal String 
let ceoKeynote = "Developers! Developers! Developers!" // initializer syntax
```

#### Unicode value count 
```swift 
let duck = "🐥"
print(duck.unicodeScalars.count) // 1 unicode value

let usFlag = "🇺🇸"
print(usFlag.unicodeScalars.count) // 2 unicode values

let makingTheUSFlag: Character = "\u{1F1FA}\u{1F1F8}"
print(makingTheUSFlag) // "🇺🇸"
```

## Unicode

Unicode is the universal character encoding. The Unicode standard was created to represent the vast number of languages around the world, including languages like English, Mandarin and even endangered languages like Navajo and the list goes on. 

Example of a unicode character is `U+1F4F1`

In swift the sytax would be 

```swift 
print("\u{1F4F1}") // "📱"
```

https://home.unicode.org/basic-info/overview/

https://www.compart.com/en/unicode


## Types of encoding `utf8`, `utf16`

#### `utf16`

_Wikipdeia:_ UTF-16 is the only web-encoding incompatible with ASCII, and never gained popularity on the web, where it is used by under 0.01% (1 hundredth of 1 percent) of web pages. UTF-8 by comparison is used by approximately 95% of all web pages. The Web Hypertext Application Technology Working Group (WHATWG) considers UTF-8 "the mandatory encoding for all text" and that for security reasons browser applications should not use UTF-16.

https://en.wikipedia.org/wiki/UTF-16


#### `utf8`

_Wikipedia:_ UTF-8 is a variable-width character encoding used for electronic communication. Defined by the Unicode Standard, the name is derived from Unicode (or Universal Coded Character Set) Transformation Format – 8-bit.

UTF-8 is capable of encoding all 1,112,064 valid character code points in Unicode using one to four one-byte (8-bit) code units.

UTF-8 is by far the most common encoding for the World Wide Web, accounting for over 95% of all web pages, and up to 100% for some languages, as of 2020.

https://en.wikipedia.org/wiki/UTF-8


#### Swift 5 switches to `utf8`

Swift 5 switches the preferred encoding to `utf8`. 

From the Swift docs: 

Native UTF-8 support is essential for efficient compatibility with modern computing environments, including:

* Server-side and client-side programming
* Systems programming and C interoperability
* Developer tools (build systems, editors, linters, etc.)

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
#### Inserting

```swift 
var str = "Alex"

str.insert(contentsOf: " Paul", at: str.endIndex)

print(str) // "Alex Paul"
```

#### Removing

```swift 
var str = "alex"

str.remove(at: str.startIndex)

print(str) // "lex"
```

> Note: if you're working in a `repl` environment and don't have access to code completion and it's okay with the interview feel free to convert the given `String` to an `Array` to avoid working with `String.Index`. Converting to an array will give you access to using subscripting using Int's to access a postion in the array of chararaters. 
>```swift
>let str = "Some input String"
>let strArr = Array(str) // you now have an array of [String.Element] aka and array of [Character]
>```


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

#### `hasSuffix`

```swift 
let words = ["Running", "Hockey", "Climbing", "Singing", "Dance", "Jump", "Walking"]

let ingWords = words.filter { $0.hasSuffix("ing") }

print(ingWords)
```


## Writing to a file in the App's Sandbox

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
