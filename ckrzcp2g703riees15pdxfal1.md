## How I Solved W1Q1 Quest- Frame It!

### Introduction

While working through the 2021 Fast Floward boot camp, you will come across a Quest on the first day that involves printing a "picture" from a provided String of characters. This problem tests your knowledge of the basics of the Cadence programming language: types, variables, structs, and functions.

In this blog post, I will go over how I solved this problem and what challenges I faced when working through it. 

### Quest

Write a function that displays a canvas in a frame

```
pub fun display(canvas: Canvas)
```

Expected Output:
```
"+-----+"
"|*   *|"
"| * * |"
"|  *  |"
"| * * |"
"|*   *|"
"+-----+"
```

### Solution

The way I always like to start solving problems is to determine the given input and the expected output. Notice for this function they are passing in a parameter called `canvas`. 

Recall from the given program, a `canvas` is a struct with `width`, `height`, and `pixels` fields. I will use `width` to help parse the given string of `pixels` into the expected output.

```
pub struct Canvas {
    pub let width: UInt8
    pub let height: UInt8
    pub let pixels: String

    init(width: UInt8, height: UInt8, pixels: String) {
        self.width = width
        self.height = height
        self.pixels = pixels
    }
}
```
First I will tackle the top and bottom borders of the "frame". In addition to the `display` function, I am going to create a helper function called `displayBorder` that prints based on the `width` of the canvas. I will pass the `canvas` struct as a parameter and declare a variable `myString` to hold the output.

```
//helper function for display
pub fun displayBorder(canvas: Canvas) {
    var myString = ""
}

pub fun display(canvas: Canvas) {
    //print top border
    displayBorder(canvas: Canvas)
}
```
Now, I want to construct the desired output on `myString`. I will use the `concat()` method to append the characters `myString = myString.concat("+")`.

```
//helper function for display
pub fun displayBorder(canvas: Canvas) {
    var myString = ""

    myString = myString.concat("+")
}

pub fun display(canvas: Canvas) {
    //print top border
    displayBorder(canvas: Canvas)
}
```
After adding the first `+` I will concatenate `-` to span the width of the canvas. 

Since Cadence doesn't have increment-able for loops (i.e `for (var i = 0; i < num; i++)`) I am adding a variable called `idx` set to `0` to help me increment using a while loop. Note when using `canvas.width` in a comparison, you will need to type cast it into an Int, otherwise you cannot compare `Int` and `UInt8`.

```
//helper function for display
pub fun displayBorder(canvas: Canvas) {
    var myString = ""
    var idx = 0

    myString = myString.concat("+")
    while idx < Int(canvas.width) {
        myString = myString.concat("-")
        idx = idx + 1
    }

}

pub fun display(canvas: Canvas) {
    //print top border
    displayBorder(canvas: Canvas)
}
```
To finish this helper function, I will add `myString = myString.concat("+")` one more time and finally `log` the output.

```
//helper function for display
pub fun displayBorder(canvas: Canvas) {
    var myString = ""
    var idx = 0

    //build string
    myString = myString.concat("+")
    while idx < Int(canvas.width) {
        myString = myString.concat("-")
        idx = idx + 1
    }
    myString = myString.concat("+")

    log(myString)
}

pub fun display(canvas: Canvas) {
    //print top border
    displayBorder(canvas: Canvas)
}
```
Now I can add the content inside the canvas plus the left and right borders. For this part I can either create another helper function or leave it inside the `display` canvas. Because I am only using this code once, I keep the code inside the `display` function. 

For printing the canvas, I am going to use the same idea as I did for `displayBorder` except I am going to loop through the length of `pixels`. 

I am also using an `offset` variable equal to the width of the canvas to help navigate each "row" of the canvas.

```
pub fun display(canvas: Canvas) {
    var idx = 0
    var offset = Int(canvas.width)
    var myString = ""

    //print top border
    displayBorder(canvas: Canvas)

    //print canvas + l/r borders
    while idx < canvas.pixels.length {
        
    }

}
```
To build the string for each row, I first concatenate `|` and then use the `slice` method to add the pixels for each row. For slice, I am grabbing `pixels` from `idx` up until `idx + offset` at each iteration of the loop.

```
pub fun display(canvas: Canvas) {
    var idx = 0
    var offset = Int(canvas.width)
    var myString = ""

    //print top border
    displayBorder(canvas: Canvas)

    //print canvas + l/r borders
    while idx < canvas.pixels.length {
        myString = myString.concat("|")
        myString = myString.concat(canvas.pixels.slice(from: idx, upTo: idx + offset))
        myString = myString.concat("|")

        //increment index by offset
        idx = idx + offset
    }

}
```

Notice how I incremented `idx` by `offset` at each iteration. This ensures the index starts and ends at the beginning and end of each row.

To illustrate what I mean, the first time we run our loop our `idx` is 0 and `idx + offset` is 5. The second time our `idx` will be 5 but our `idx + offset` will be 10 and so on. 

At the end of each iteration of the loop I also `log` and reset `myString` before looping again.

```
pub fun display(canvas: Canvas) {
    var idx = 0
    var offset = Int(canvas.width)
    var myString = ""

    //print top border
    displayBorder(canvas: Canvas)

    //print canvas + l/r borders
    while idx < canvas.pixels.length {
        myString = myString.concat("|")
        myString = myString.concat(canvas.pixels.slice(from: idx, upTo: idx + offset))
        myString = myString.concat("|")

        //print and reset string
        log(myString)
        myString = ""
    }

}
```

To finish this function, I will call our helper function `displayBorder` once more to create the bottom border.

```
pub fun display(canvas: Canvas) {
    var idx = 0
    var offset = Int(canvas.width)
    var myString = ""

    //print top border
    displayBorder(canvas: Canvas)

    //print canvas + l/r borders
    while idx < canvas.pixels.length {
        myString = myString.concat("|")
        myString = myString.concat(canvas.pixels.slice(from: idx, upTo: idx + offset))
        myString = myString.concat("|")

        //increment index by offset
        idx = idx + offset

        //print and reset string
        log(myString)
        myString = ""
    }

    //print bottom border
    displayBorder(canvas: Canvas)

}
```

To wrap everything up, call the `display` function in `main()` and test it on the `canvasX` (example provided by Fast Floward).

```
display(canvas: CanvasX)
```

You can see the [final version](https://github.com/saminacodes/Fast-Floward-2021/blob/main/w1q1.cdc) of this program on GitHub.

### Conclusion

That's it! Fairly simple but it takes understanding of a few key concepts and a little bit of work to solve this problem.

A challenge I faced was understanding how to reference the different fields from the struct and type casting. I learned that to reference you will need to prefix the field with the name of the struct e.g `canvas.width` or `canvas.pixels`. I also did not type cast the fields into `Int` initially and ran into several errors. 

Another challenge I faced was understanding which methods I could use to build the strings for the output. I learned Cadence includes `concat()` and `slice()` which I was familiar with from JavaScript and used these two to build my strings.

The last challenge I faced was deciding how to loop through the `pixels` field to display the canvas. I remembered that in problems involving rows and columns using an offset can help simplify the problem. Drawing this part out on paper helped to visualize where to slice from.

Of course, there will be more efficient ways to solve this problem. Even after solving, I realized I could pass `canvas.width` into the helper function `displayBorder` instead of the entire struct. 

If you came up with a different solution, let me know what is was in the comments!

### Fast Floward BootCamp

If you are interested in registering for the Fast Floward Bootcamp, register through this link: https://www.decentology.com/blog/fast-floward-developer-bootcamp-for-flow






