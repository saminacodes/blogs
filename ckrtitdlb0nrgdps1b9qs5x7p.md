## Day 1 - Getting Started with Flow + Cadence

### Introduction

**What is Flow?**

Flow is a blockchain similar to others you may have heard of such as Ethereum or Solana. One of the key distinguishers for Flow is how they solved scalability while maintaining decentralization and security.

> If you want to dive into a more in depth comparison of Flow and Ethereum check out this article: https://pixelplex.io/blog/flow-vs-ethereum-comparison-best-platforms-for-nft/

**What is Cadence?**

Cadence is a Resource-Oriented programming language designed for developing smart contracts. Cadence is a great programming language to get started in Web3 because it prevents developers from accidentally writing code that could cause data or financial loss. It is also fast, lower cost compared to other [Proof Of Work](https://www.investopedia.com/terms/p/proof-work.asp) Blockchains, and secure.

> You can learn more about Flow and Cadence through their [Getting Started](https://docs.onflow.org/) page.

### Part I - Installing Flow CLI

Installing the Flow CLI will depend on the operating system of your device. Follow the [documentation from Flow](https://docs.onflow.org/flow-cli/install/#gatsby-focus-wrapper) to install the latest version.

After installing, in your CLI/terminal, use the command `flow version` to verify you have the correction version installed.

To start working with Flow in a [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop), in the CLI/Terminal type the command `flow cadence` which will open something that looks like this:

```
Welcome to Cadence v0.18.0!
Type '.help' for assistance.

1>
```

This is the REPL environment in which we will start in.

Of course, we can't break tradition. Let's start learning Cadence with none other than "Hello, World."

In your CLI/terminal type the following and press enter.

```
log("Hello, World")
```

This should echo the statement back in your CLI/Terminal.

Now we can move onto learning comments, types, variables, and functions.

### Part II - Comments

Cadence has your standard options for formatting comments plus a few more.

- **Single line comments**

    ```
    // comment
    ```

- **Multi-line Comments**

    ```
    /* multi line
    comment */
    ```

- **Documentation Comments - Single Line**

    ```
    /// documentation single line comment
    ```

- **Documentation Comments - Multi-line**

    ```
    /**
    documentation
    multi-line
    comment
    **/
    ```

### Part III - Types + Variable Declaration

Like most programming languages, Cadence has **primitive types**. Primitive types are basic data types that serve as a building block in most languages. 

In Cadence, you can declare primitive type variables explicitly `let name: String = "Samina"` or implicitly `let name = "Samina"`

<hr>

**Note:** before we get into types, when declaring variables in Cadence there is a difference between `let` and `var`. Unlike in JavaScript, `let` is an immutable or not changeable variable declaration. In contrast, `var` is mutable or changeable.

```
let age = 21
age = age + 1
```

For example, the statement above would result in an **error**. Use `var` instead of `let` when you are planning on changing the variables. 

<hr>

1. **Integers** are used to represent whole numbers. An integer can take on many forms including decimal, binary, octal, and hex. You can also use underscores to make it visually easier to comprehend bigger numbers (ex. 100,000,000 -> `100_000_000`). 

    ```
    let numOne = 627 //decimal
    var numTwo = 0b1010 //binary (decimal equivalent 10)
    let numThree = 0o13 //octal (decimal equivalent 11)
    var numFour = 0xFF //hex (decimal equivalent 255)
    ```

    You can use specific versions of `Int` such as `Int8` (range: -128 to 127) or `Int16` (range: 
   -32,768 to 32,767) if you want to be specific or save storage space. You can also use unsigned 
    integers: `UInt`. 

2. **Fixed- Point Numbers** are used to represent fractional numbers. In Cadence, these are `Fix64` or `UFix64` for the unsigned version. 

    ```
    let numOne: Fix64 = 7.25
    var numTwo: UFix64 = 126.02
    ```

3. **Strings** are a collection of unicode characters that are immutable. I like to think of them as a collection of characters or a word. **Note:** strings are always enclosed in quotes.

    ```
    let name = "Steve"
    let favoriteGame: String = "Minecraft"
    ```

4. **Addresses** allows you to store addresses or pointers. This is used quite frequently in Cadence to reference accounts and will be super useful when we dive into Smart Contracts and Transactions.

    ```
    let accountAddress: Address = 0x123456789
    ```

5. **Booleans** allows you to store the binary values `true` or `false`. These types can be used to indicate an on or off state or work with conditionals (if-else) to help control your program. 

    ```
    var lightsOn = false
    let isAfraid = true
    ```

<hr>

Cadence also has several **composite data types**. Composite types are usually built from the aforementioned primitive types. 

1. **Arrays** are a mutable collection of types.

    ```
    let months = ["January", "February", "March", "April", 
    "May", "June", "July", "August", "September", "October", 
    "November", "December"]
    ```

2. **Dictionaries** are a mutable collection of key-value pairs. 

    ```
    let sides = {"triangle": 3, "square": 4 , "pentagon": 5 , "hexagon": 6}
    sides["square"] //outputs 4
    ```
3. **Structures** or structs are a value type. You can compare them to objects in JavaScript. Their primary purpose is to store information.

    ```
    pub struct avenger {
        pub let name: String
        pub let ability: String
        pub let weapon: String
        pub let weight: Fix64 //pounds
        pub let height: Fix64 //inches
        
        init(name: String, ability: String, weapon: String, weight: Fix64, height: Fix64) {
            self.name = name
            self.ability = ability
            self.weapon = weapon
            self.weight = weight
            self.height = height
        }
    }
    
    ```

    The keyword `pub` stands for public- which is an [access modifier](https://en.wikipedia.org/wiki/Access_modifiers#:~:text=Access%20modifiers%20(or%20access%20specifiers,facilitate%20the%20encapsulation%20of%20components.). We use the keyword `struct` to declare the structure and follow it with the name to reference the struct: `avenger`. Inside of the struct, after we declare our fields, we must use `init()` to initialize the fields.

    In order to initialize an instance of a struct we would do the following:
    
    ```
    let CaptainAmerica = avenger(name: "Steve Rogers", ability: "Super Strength", weapon: "Shield", weight: 240, height: 74)
    ```

4. **Resources** are similar to structs except they are linear types. Resources are moved around and not copied (in contrast to structs) and they can only exist once. 

    What does that mean? 

    Good question. Well, it is a vital part of Resource-oriented programming 
    languages, prevalent in Web3. Resources are special and can be used in Cadence to 
    represent something unique such as an NFT, Collection, etc. 
    
    For resources I am going to use the following example provided in the Fast Floward Bootcamp:

    ```
    pub resource Wallet {
        pub var dollars: UInt

        init(dollars: UInt) {
            self.dollars = dollars
        }
    }
    ```

    In order to initialize the Wallet we created, we would use the following

    ```
    let myWallet <- create Wallet(dollars: 10)
    destroy myWallet
    ```
    
    Notice how it uses an arrow `<-` instead of `=` and the keyword `create` to initialize the Wallet. The arrow signifies where the resource is moving and the `create` indicates the creation of that resource.

    Because resources don't allow [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science), we must delete the resource manually by using the keyword `destroy` followed by the name of the resource. 

    Something interesting to note is that resources are used in Cadence for assets like [NFTs](https://www.theverge.com/22310188/nft-explainer-what-is-blockchain-crypto-art-faq) because they cannot be destroyed (unless destroyed by the owner). This is an important structure to have because you don't ever want to lose these, oftentimes, valuable assets. 

### Part IIII - Functions

Are you still there? Bare with me, this is the last technical section.

Functions!

If you have worked with functions in other programming languages, this should be fairly similar in nature. 

In contrast to the REPL we worked with earlier, for this section we can work with a `.cdc` or Cadence file.

To begin, create your file in the CLI/terminal:

```
flow cadence demo.cdc
```

You can open this using your favorite command line editor or use an IDE such as VS Code. If you decide to use VS Code, be sure to [install the Cadence extension](https://docs.onflow.org/vscode-extension/) to assist you with syntax highlighting. 

In a `.cdc` file we will declare an [entry-point](https://en.wikipedia.org/wiki/Entry_point#:~:text=In%20computer%20programming%2C%20an%20entry,control%20to%20its%20entry%20point.) by using the `main()` function.

```
pub fun main() {
    log("Hello, World")
}
```
> To run this program type `flow cadence` in the root of your directory. We should once again see it echo "Hello World"

Notice the keyword `pub` (short for public)- this is an access modifier meaning that the public has access to the value. Following that is `fun` which is an abbreviation for function. The rest of it should look similar to functions you have created before.

Now let's take it a step further and add another function. This example was also provided by the Fast Floward Bootcamp

```
pub fun hello(to name: String) {
    log("Hello, ".concat(name))
}

pub fun main() {
    hello(to: "Steve Rogers")
}
```
We should see the following when we run this program:

```
Hello, Steve Rogers
```

With that, we can conclude the main material from Day 1. 

### Fast Floward BootCamp

For further learning, the Fast Floward Bootcamp provides a great example to reinforce all these concepts, and provides Quests to practice your learning.

I want to thank the team at [Decentology](https://decentology.com) for providing all this material to learn Flow and Cadence. Their team has gone above and beyond providing an inclusive, welcoming environment, and supporting incoming developers to Web3. 

If you are interested in registering for the Fast Floward Bootcamp, register through this link: https://www.decentology.com/blog/fast-floward-developer-bootcamp-for-flow