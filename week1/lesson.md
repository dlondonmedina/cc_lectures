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

* ```<<, >>``` These are bitwise operators and they shift bits. We won't use them in this class, but here's how they work: the number one in decimal is the same as 0001 in binary. If we use the bitwise operator  ```1 << 2```, we are telling the computer to take 1 and shift its bits left by 2 places. So 0001 becomes 0100, which is 4 in decimal. Likewise, ``` 4 >> 1 ``` tells the computer to take 4 (0100) and shift its bits right by 1 place. So 0100 becomes 0010, which is 2 in decimal. There are several other bitwise operators, and they are useful because computationally complex operations like finding powers of 2 or square roots can be done more easily by performing the operation bitwise in binary. 

