# Enumerations lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1 DONE

a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.

Answer:
```swift
enum iOSDeviceType {
case iPhone(String)
case iPad(String)
case iWatch(String)
}

var myDevice = iOSDeviceType.iPhone
```

b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.

Answer:
```swift
var myDeviceWithModel = iOSDeviceType.iPhone("6 Plus")
//var myDeviceWithModel = iOSDeviceType.iPad("Mini")
//var myDeviceWithModel = iOSDeviceType.iWatch("4")

switch myDeviceWithModel {
case .iPhone(let model):
print("iPhone \(model)")
case .iPad(let model):
print("iPad \(model)")
case .iWatch(let model):
print("iWatch \(model)")
}
```

## Question 2 DONE

a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.

c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.

Answer:
```swift
//a & b:
enum Shape: String {
case triangle = "A triangle has 3 sides."
case rectangle = "A recrangle has 4 sides."
case square = "A square has 4 sides."
case pentagon = "A pentagon has 5 sides."
case hexagon = "A hexagon has 6 sides."
}

let myFavoritePolygon = Shape.square
print(myFavoritePolygon)

// c:
enum Shape {
case triangle(Int)
case rectangle(Int)
case square(Int)
case pentagon(Int)
case hexagon(Int)

func getPerimeter() -> Int {
switch self {
case .triangle(let length):
return (3*length)
case .rectangle(let length):
return (4*length)
case .square(let length):
return (4*length)
case .pentagon(let length):
return (5*length)
case .hexagon(let length):
return (6*length)
}
}
}

var length = 10
var perimeterTriangle = Shape.triangle(length).getPerimeter()
print(perimeterTriangle)
```

## Question 3 DONE

Write an enum called `OperatingSystem` and give it cases for `windows`, `mac`, and `linux`. Create an array of 10 `OperatingSystem` objects where each one is set to a random operating system. Then, iterate through the array and print out a message depending on the operating system.

Answer:
```swift
enum OperatingSystem: String {
case windows = "Windows"
case mac = "Mac"
case linux = "Linux"
}

let arrayOfOS = [OperatingSystem.mac, OperatingSystem.mac, OperatingSystem.linux, OperatingSystem.windows, OperatingSystem.windows, OperatingSystem.mac, OperatingSystem.mac, OperatingSystem.mac, OperatingSystem.linux, OperatingSystem.windows]
print(arrayOfOS)

for os in arrayOfOS {
if os == OperatingSystem.mac {
print(OperatingSystem.mac.rawValue)
} else if os == OperatingSystem.windows {
print(OperatingSystem.windows.rawValue)
} else if os == OperatingSystem.linux {
print(OperatingSystem.linux.rawValue)
}
}

```

## Question 4 DONE

You are working on a game in which your character is exploring a grid-like map. You get the original location of the character and the steps he will take.

- A step .up will increase the y coordinate by 1.
- A step .down will decrease the y coordinate by 1.
- A step .right will increase the x coordinate by 1.
- A step .left will decrease the x coordinate by 1.
- Print the final location of the character after all the steps have been taken.

```swift
enum Direction {
    case up
    case down
    case left
    case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

// your code here
```
Answer:
```swift
enum Direction {
case up
case down
case left
case right

func move(location: (x: Int, y: Int)) -> (x: Int, y: Int) {
switch self {
case .up:
return (location.x, location.y + 1)
case .down:
return (location.x, location.y - 1)
case .left:
return (location.x - 1, location.y)
case .right:
return (location.x + 1, location.y + 1)
}
}
}


var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

for step in steps {
location = step.move(location: location)
}
print(location)
```

## Question 5 DONE

a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).

Hint: Rock beats scissors, paper beats rock, scissor beats paper

Answer:
```swift
//a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

enum HandShape {
case rock
case paper
case scissors
}


//b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

enum MatchResult {
case win
case draw
case lose
}


//c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).
//
//Hint: Rock beats scissors, paper beats rock, scissor beats paper

func match(_ yourHS: HandShape, otherHS: HandShape) -> MatchResult {
if yourHS == HandShape.rock {
if otherHS == HandShape.rock {
return MatchResult.draw
} else if otherHS == HandShape.paper {
return MatchResult.lose
} else {
return MatchResult.win
}
} else if yourHS == HandShape.paper {
if otherHS == HandShape.rock {
return MatchResult.win
} else if otherHS == HandShape.paper {
return MatchResult.draw
} else {
return MatchResult.lose
}
} else {
if otherHS == HandShape.rock {
return MatchResult.lose
} else if otherHS == HandShape.paper {
return MatchResult.win
} else {
return MatchResult.draw
}
}
}

print(match(HandShape.rock, otherHS: HandShape.paper))
```
## Question 6 DONE

a) You are given a `CoinType` enumeration which describes different coin values. Print the total value of the coins in the array `moneyArray` which contains tuples of type (`quantity`, `CoinType`).

```swift
enum CoinType: Int {
    case penny = 1
    case nickle = 5
    case dime = 10
    case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
                                   (15,.nickle),
                                   (3,.quarter),
                                   (20,.penny),
                                   (3,.dime),
                                   (7,.quarter)]

// your code here
```
Answer:
```swift
enum CoinType: Int {
case penny = 1
case nickle = 5
case dime = 10
case quarter = 25
}

var moneyArray:[(quantity: Int, coinType: CoinType)] = [(10,.penny),
(15,.nickle),
(3,.quarter),
(20,.penny),
(3,.dime),
(7,.quarter)]



var total = 0

for i in moneyArray {
total += (i.0 * i.1.rawValue)
}
print(total)
```

b) Write a method in the `CoinType` enum that returns an Int representing how many coins of that type you need to have a dollar. Then, create an instance of `CoinType` set to `.nickle` and use your method to print out how many nickels you need to have to make a dollar.

Answer:
```swift
enum CoinType: Int {
case penny = 1
case nickle = 5
case dime = 10
case quarter = 25

func getDollar() -> Int {
switch self {
case .penny:
return 100/CoinType.penny.rawValue
case .nickle:
return 100/CoinType.nickle.rawValue
case .dime:
return 100/CoinType.dime.rawValue
case .quarter:
return 100/CoinType.quarter.rawValue
}
}
}

var nickelsNeeded = CoinType.nickle.getDollar()
print(nickelsNeeded)
```

## Question 7

a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

`let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]`

c) Write a method in `DayOfWeek` called `isWeekend` that determines whether a day is part of the weekend or not and write code to calculate how many week days appear in `poorlyFormattedDays`.

Answer:
```swift
let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]
var wellFormattedDays = [String]()

for day in poorlyFormattedDays {
wellFormattedDays.append(day.lowercased())
}

var howManyWeekdays = 0

enum DayOfWeek: String {
case monday = "monday"
case tuesday = "tuesday"
case wednesday = "wednesday"
case thursday = "thursday"
case friday = "friday"
case saturday = "saturday"
case sunday = "sunday"


func isWeekend() -> Bool {
switch self {
case .monday:
return false
case .tuesday:
return false
case .wednesday:
return false
case .thursday:
return false
case .friday:
return false
case .saturday:
return true
case .sunday:
return true
}
}
}

for day in wellFormattedDays {
if day != "saturday" && day != "sunday" {
howManyWeekdays += 1
}
}

print(DayOfWeek.monday.isWeekend(), howManyWeekdays)
```
## Question 8 DONE

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.

Answer:
```swift
enum MetroLine {
case red
case orange
case yellow
case green
case blue
}

var trainLine = MetroLine.red
print(trainLine)

```

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.

Answer:
```swift
enum MetroLine {
case red(Int)
case orange(String)
case yellow(String)
case green(Int)
case blue(String)
}

var trainLine = MetroLine.red(1)
print(trainLine)
```

c) Write code that prints the train letter or number of your instance of `MetroLine`.

Answer:
```swift
switch trainLine {
case .red(let number):
print(number)
case .orange(let letter):
print(letter)
case .yellow(let letter):
print(letter)
case .green(let number):
print(number)
case .blue (let letter):
print(letter)
}
```

## Question 9 DONE

a) Think of your own example of something that can be modeled as an enum and write it. Remember that enums allow you to create instances of a defined list of cases.

b) Add a method to your enum.... try to have the method make sense.

Answer:
```swift
enum GelatoFlavors {
case yogurt
case chocolate
case mint
case strawberry
case peach

func isFruitFlavor () -> Bool {
switch self {
case .yogurt:
return false
case .chocolate:
return false
case .mint:
return false
case .strawberry:
return true
case .peach:
return true
}
}
}

var isItFruityGelato = GelatoFlavors.strawberry.isFruitFlavor()
print(isItFruityGelato)
```
