# Week 1

This week we're going to cover quite a bit of review matieral. If this isn't review for you, that's fine as well. I'm going to write up a short summary here. We'll then cover the material in class.

## What is a programming language?

Computers are extremely powerful, but stupid machines. At the present moment, they can operate extremely quickly and precisely, **but** only on instructions that they have been given. What this means for us is that we can be one of two types of users. First, we can use computers by accessing the instructions that other people have given them. We do this whenever we "use" programs on our computer. Someone wrote a sequence of instructions, which manifest into the program that we use. Second, we can write instructions to the computer itself to have it do novel operations of our design. When we learn programming, we become the second type of user. 

A programming language is simply a formal set of syntax that we construct to give instructions to a computer. I say formal insofar as there is no intuition in how a programming language is interpreted by the computer. You either give it an instruction it knows and it does the action, or you give it an instruction it doesn't know and the computer will give you an error message. It will not guess what you might've meant like we do with human language. 

Let me give you an example:

```python
y = 2 + 2
print(y)
```

This instruction tells the computer to calculate the value of two plus two (which is four), and then save it to a place in memory which is identified by the name y. The second instruction tells the computer to display whatever value is stored in the memory address identified by y. The output will be, of course, 4. 

Why does the computer follow these instructions? Because it has Python installed and therefore knows what these instructions mean. If I wrote them like this:

```python
y = 2 +_ 2
print(y)
```

The computer would throw an "SyntaxError" on the first line because it doesn't know what ```+_``` means. This is important to understand because to you and me, we would guess that the first instruction really wants us to add 2 and 2 and store it to the variable y, but we have a typo. The computer wouldn't guess that. It simply will say, "I don't understand what you want me to do." It doesn't mean I'm a bad programmer or don't know what I'm doing. It simply means there is an error in my code, or I forgot the syntax for addition. In any case, I fix it and move on. The computer is nice enough to tell me what my error is so it's easier to fix. 

## Math operators

Computers do calculations, and the fundamental starting spot for us is calculations. Here are the operators and their meanings:

* ```+, -, *, /``` These operators do addition, subtraction, multiplication and division. 

* ```%``` This is the modulo or mod operator. It divides two numbers and returns the remainder. So ```5 % 2``` would be ```1``` because 5 can be divided by 2 with one remaining. The mod operator is really valuable for math tricks. 

* ```=``` This is an assignment operator. It says take whatever is on the right side and assign it to the variable on the left. If there are any operations on the right side of the operator, those are performed first. So ```y = 2 * 2``` would calculate 2 times two FIRST and then assign the result to the variable "y".

* ```<<, >>, &, |, ~, ^``` These are bitwise operators and they perform operations on the string of bits that represents a value. We won't use them in this class, but they are pretty cool, and you can do clever tricks to make your program much more efficient.

## Variables

If we do a calculation in our program, the computer does not automatically save the output of that calculation. For instance, if we calculate ```2 * 2``` the calculation "returns" or outputs 4, obviously, but once the computer moves on to the next instruction, it immediately discards that value of 4 unless we happened to tell the computer to write that value to memory. 

### Volatile and Non-volatile Memory

Generally, when you save a file on your computer, you are saving it to what is called non-volatile memory. The data is written to a "disk" of some sort where it is saved permanently unless you delete or overwrite it. Non-volatile means that the data is not lost when we turn off the computer.

However, when writing programs, whenever we store data with variables we are storing them to volatile memory. Volatile memory is generally when you know as RAM. If your computer has 16GB of RAM, that means that there are 16 billion bits of storage space at any given time. A bit is a unit of memory that can hold a 0 or a 1. For funsies, my name, Dylan, when converted to binary looks like this: ```01000100 01111001 01101100 01100001 01101110```One set of 8 bits for each letter, so my name takes requires 40 bits. The thing about RAM is that while it is a lot faster than non-volatile memory, it will save your data until the sector is marked for deletion or when the computer loses power. If you have ever written a document and had the power go out before you saved and you lost a bunch of work, that is because the work was stored in RAM but had not been written to non-volatile storage. 

Volatile and non-volatile matter a little to us. If we want our programs to store data between runs or from session to session, we need some way to write that data to non-volatile storage. More important for understanding variables is that our variables are little more than names that point to addresses of memory. Let me explain this a bit more. My computer has 16GB of memory. That's a lot of 0's and 1's. How does our computer ever find anything? Well, that memory is organized by addresses. Our operating system is in charge of this, and if you've ever wondered the difference between a 32 and 64 bit operating system, that refers to the difference in the size of each address. Think of it as a map of a city, each "building" has an address, which tells us where in the city to find that building. The same is true for our memory in our computer. The operating system manages a map of the memory. When we create a variable, the operating system locates a free sector of memory of sufficient size and associates the variable name with that memory address. When we use that variable later to get the data we stored, the operating system retrieves the data stored at that address and allows us to do something with it. Let me give you an example with some notes in code:

```python
first_name = "Dylan"  # this line creates a variable called first_name. 
                      # The OS then finds a sector of memory large enough
                      # to fit 01000100 01111001 01101100 01100001 01101110
                      # and associates the variable name: first_name with 
                      # that address. If I were to inspect the contents of 
                      # my RAM, I would find that value at the corresponding
                      # address. 
print(first_name[0])  # this line tells the computer to access data stored at
                      # the address associated with first_name. Then it uses
                      # string slicing to get the first character of that value
                      # and then it passes that character to the built in 
                      # function print(), which displays on the screen whatever
                      # value is given to it in side the parentheses. So when 
                      # the computer executes this line, "D" will be printed
                      # to the screen.
first_name = "Daniel" # This line will now tell the computer to find the 
                      # address identified by first_name and replace whatever
                      # was stored in that sector of memory with the word 
                      # "Daniel". If I looked at the contents of the memory 
                      # at the address identified by first_name after this line
                      # is executed, I would find the contents is no longer the 
                      # binary for "Dylan", but instead is the binary for 
                      # "Daniel" and the data "Dylan" is totally lost. 
```

NOW, this is a long discussion, but I think it is important to understand what is going on under the hood when you use variables in Python. Whenever you create a variable, or a function, or any other named entity, Python stores that value/code/class/etc. to a sector of memory that is identified by the name you give it. 

## Functions

Variables are not the only named entities. Variables store data or values, but let's say you have a set of instructions or code that you want to repeat a whole bunch of times. For example, let's say you've been given the task of finding the most common word in each document within a sequence of documents. If you wanted to do this for one document the code might look like this:

```python
with open("the_document.docx") as f: # this line opens the file.
    max = 0
    max_word = ""
    text = f.read() # this line reads the file
    for word in text.split(" "): # this gets a list of all the words
        if text.count(word) > max: # if the count of the word is greater than the max, we have a new max. 
            max = text.count(word)
            max_word = word
    
print(max_word, max) # print the result because why not.
```

Now if I wanted to do this with a bunch of files, I'd have to manually change the name "the_document.docx" to each file in the list and then either run the code again or copy the code with the new file name. Like so:

```python
with open("document1.docx") as f: # this line opens the file.
    max = 0
    max_word = ""
    text = f.read() # this line reads the file
    for word in text.split(" "): # this gets a list of all the words
        if text.count(word) > max: # if the count of the word is greater than the max, we have a new max. 
            max = text.count(word)
            max_word = word
    
print(max_word, max) # print the result because why not.

with open("document2.docx") as f: # this line opens the file.
    max = 0
    max_word = ""
    text = f.read() # this line reads the file
    for word in text.split(" "): # this gets a list of all the words
        if text.count(word) > max: # if the count of the word is greater than the max, we have a new max. 
            max = text.count(word)
            max_word = word
    
print(max_word, max) # print the result because why not.
```

That's a bad practice because I have a lot of code copied and pasted. Instead, I could create a **function** which is a named entity that is a collection of instructions. Each function has an input, it has the instructions, and it has an output. So let me refactor my code so it can be used as a function:

```python
def get_max_word(filename):
    with open(filename) as f:
        max = 0
        max_word = ""
        text = f.read() # this line reads the file
        for word in text.split(" "): # this gets a list of all the words
            if text.count(word) > max: # if the count of the word is greater than the max, we have a new max. 
                max = text.count(word)
                max_word = word

    return (max_word, max)
```

The first line tells the computer that this is a function that needs to be stored in memory. The name of the function is ```get_max_word```. The input is ```filename```. Finally, instead of printing the max word and count, it returns those values so that I can use them elsewhere. Now, if I want to run this on a bunch of files with the same output as above, my code might look like this:

```python
def get_max_word(filename):
    with open(filename) as f:
        max = 0
        max_word = ""
        text = f.read() # this line reads the file
        for word in text.split(" "): # this gets a list of all the words
            if text.count(word) > max: # if the count of the word is greater than the max, we have a new max. 
                max = text.count(word)
                max_word = word

    return (max_word, max)

print(get_max_word("document1.docx"))
print(get_max_word("document2.docx"))
print(get_max_word("document3.docx"))
print(get_max_word("document4.docx"))
print(get_max_word("document5.docx"))
```

On the last five lines, the code saved as get_max_word is run on each of the 5 files. The output of tha function (max_word, max) is then printed to the screen. Any time you have a set of instructions that needs to be executed many times, it's a good idea to consider how you might use a function. it makes the code neater. Also, if I want to change how the instructions work, like make the instruction non-case-sensitive, I only need to change the code in one place. 

## Conclusion   

These are the main types of named entities. There are also Classes, but we'll move on to that in the future. Named entities are variables or functions that the computer stores in volatile memory. They are simply names that point to addresses in memory in which the value or instructions are stored. We use those human readable names to easily retrieve the stored stuff later in our program. 

        
