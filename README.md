# Lesson 19 - Enums and Switch

# Exercise: Defining Enums

Get some practice defining your own enums. Remember the rules about naming enums and their cases.

## Exercise
Define an enum for the compass directions: North, East, South, and West.

```swift
enum Direction {
  case north, east, south, west
}
```

## Exercise
Define an enum for jigsaw puzzle pieces: corner, edge, and middle.

```swift
enum PuzzlePiece {
    case corner, edge, middle
}
```

## Exercise
Define an enum for the playback modes in a music app: standard, repeat, repeat all, and shuffle.

```swift
// Can't use "repeat" since it's a unique keyword in Swift. repeatOne is a good candidate
enum PlaybackMode {
    case standard, repeatOne, repeatAll, shuffle
}
```

# Exercise: Counting Chickens
This playground has a Chicken type built in to it. A Chicken has a breed and temper property, and both properties are enums.

Here is an array of chickens:

```chickens```

The chickens are all hatched, so it’s safe to count them.

```swift
var chickenOfInterestCount = 0
for chicken in chickens {
    if chicken.temper == .hilarious {
        chickenOfInterestCount += 1
    }
}
chickenOfInterestCount
```

## Exercise
Update the code in the for…in loop to only count interesting chickens, like .hilarious .leghorns. Check out the autocompletion popup to see what the possible values for each enum are.

```
// The auto-complete will show you both "temper" and "breed". We want "temper" in this case in order to compare to "hilarious"
```

# Exercise: Replacing Bools
The following struct describes a type of enemy in a game:

```swift
enum Weapon {
    case sword, rubberMallet, none
}

struct Enemy {
    let strength: Int
    let speed: Int
    let weapon: Weapon
}
```

As your game has developed, you’ve decided that your enemies might have more than one type of weapon.

## Exercise
Define an enum to represent the weapons an enemy might have: none, sword, rubberMallet and so on. Change the struct definition to use your new enum instead of a Bool.

# Exercise: Counting Votes

In the Arrays and Loops playground, you had a chance to create a function that would tally votes from classmates. At the time, you could only ask yes-no questions that could be held in Boolean results.

You were worried that using strings would result in voting mistakes from typos. But now that you’ve studied enums, you can safely make your voting system a bit more sophisticated:

```swift
enum ClassTripDestination {
    case beach, chocolateFactory
}

let tripDestinationVotes: [ClassTripDestination] = [.beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .chocolateFactory, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .chocolateFactory, .beach, .beach, .beach, .beach, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .beach, .chocolateFactory, .beach, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .beach, .beach, .beach, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .beach, .beach, .beach, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .beach, .beach, .beach, .chocolateFactory, .beach, .beach, .beach, .beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .chocolateFactory, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .beach, .beach, .beach, .beach, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .chocolateFactory, .beach, .chocolateFactory, .beach, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .beach, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .beach, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .beach, .beach, .beach, .chocolateFactory, .chocolateFactory, .beach, .chocolateFactory, .chocolateFactory, .chocolateFactory, .beach, .beach, .chocolateFactory, .chocolateFactory]
```

## Exercise
Without counting the votes by hand, find out whether the students prefer the chocolate factory or the beach. Hint: Check the Arrays and Loops playground for a refresher on working with collections of data.

```swift
var beachVotes = 0
var factoryVotes = 0

for dest in tripDestinationVotes {
    switch dest {
    case .beach:
        beachVotes += 1
    case .chocolateFactory:
        factoryVotes += 1
    }
}

if beachVotes > factoryVotes {
    print("We're going to the beach!")
} else if beachVotes < factoryVotes {
    print("We're going to the chocolate factory!")
} else { // they are equal!
    print("We'll need to vote again; it's a tie!")
}
```

# Extension
In another poll, for choosing a school mascot, you decide to add an undecided option:

```swift
enum SchoolMascotOption {
    case salamander, marmot, neither
}
import Foundation
let mascotVotes: [SchoolMascotOption] = [.neither, .marmot, .salamander, .neither, .marmot, .neither, .neither, .marmot, .neither, .salamander, .salamander, .marmot, .neither, .neither, .salamander, .neither, .neither, .marmot, .salamander, .neither, .neither, .neither, .marmot, .marmot, .neither, .neither, .marmot, .salamander, .neither, .marmot, .marmot, .marmot, .marmot, .neither, .salamander, .salamander, .salamander, .salamander, .salamander, .salamander, .salamander, .marmot, .neither, .salamander, .salamander, .neither, .salamander, .neither, .salamander, .salamander, .salamander, .salamander, .salamander, .salamander, .marmot, .neither, .neither, .marmot, .salamander, .neither, .neither, .salamander, .salamander, .neither, .salamander, .salamander, .salamander, .salamander, .neither, .salamander, .neither, .salamander, .marmot, .salamander, .marmot, .salamander, .salamander, .marmot, .salamander, .neither, .marmot, .marmot, .marmot, .salamander, .marmot, .salamander, .marmot, .neither, .marmot, .neither, .salamander, .marmot, .marmot, .marmot, .neither, .marmot, .marmot, .salamander, .neither, .neither, .salamander, .neither, .neither, .marmot, .neither, .salamander, .salamander, .salamander, .neither, .neither, .salamander, .salamander, .salamander, .marmot, .salamander, .salamander, .marmot, .salamander, .neither, .marmot, .marmot, .neither, .neither, .salamander, .marmot, .neither, .marmot, .salamander, .salamander, .marmot, .salamander, .neither, .salamander, .marmot, .neither, .salamander, .marmot, .marmot, .salamander, .marmot, .salamander, .marmot, .salamander, .salamander, .marmot, .marmot, .neither, .marmot, .neither, .marmot, .salamander, .salamander, .salamander, .neither, .salamander, .salamander, .neither, .marmot, .neither, .marmot, .marmot, .marmot, .marmot, .neither, .marmot, .neither, .salamander, .marmot, .salamander, .neither, .salamander, .salamander, .marmot, .neither, .marmot, .neither, .salamander, .neither, .salamander, .neither, .neither, .marmot, .salamander, .neither, .marmot, .salamander, .marmot, .neither, .salamander, .neither, .neither, .salamander, .salamander, .salamander, .neither, .salamander, .neither, .marmot, .salamander, .marmot]

var salamanderVotes = 0
var marmotVotes = 0
var neitherVotes = 0

for mascot in mascotVotes {
    switch mascot {
    case .salamander:
        salamanderVotes += 1
    case .marmot:
        marmotVotes += 1
    case .neither:
        neitherVotes += 1
    }
}

if salamanderVotes > marmotVotes && salamanderVotes > neitherVotes {
    print("Salamanders are the new mascot!")
} else if marmotVotes > salamanderVotes && marmotVotes > neitherVotes {
    print("Marmots are the new mascot!")
} else { // neither was the most selected
    print("People didn't like either mascot!")
}
```

## Exercise
Without counting by hand, determine which option has won.
* experiment: In the Arrays and Loops vote counting exercise, an extension exercise asked you to write a single function that could calculate the results of any Boolean vote. What prevents you from writing a single function for calculating both tripDestinationVotes and mascotVotes?

```swift
// You have to create a var for each option that you're going to tally. Trips have two options to vote for, and mascots have 3 options. Inside our function, we can't create different amounts of variables.
```

# Exercise: Switch
This enum represents targets that the player might hit in a game:

```swift
enum Target {
    case red, green, blue, gold
}
```

This function returns a score given a particular target:

```swift
func score(target: Target) -> Int {
    switch target {
    case .red:
        return 10
    case .green:
        return 15
    case .blue:
        return 25
    case .gold:
        return 50
    }
}
```

## Exercise
Update the score(target:) function to use a switch statement and return the correct score for each target. The statements below tell you the values to aim for:

```swift
score(target: .red)    // This should be 10
score(target: .green)  // This should be 15
score(target: .blue)   // This should be 25
score(target: .gold)   // This should be 50
```




