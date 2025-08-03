# Digital circuits - AND OR NOT

##Overview
Before we can even think about all these crazy video games and internet access and neural networks we need to do what a computer is named after - computing!

###Numbers
###Boolean arithmetic 
###Transistors
###Physical Gates

##Numbers

Before we can talk about programming languages and compilers and databases we should understand how any of this is possible. How can a piece of silicon do maths or store images and predict text?

Anything complex can be made from simple blocks. Your human brain more complex - but not necessarily smarter - than any computer is made of simple neurons. These simple neurons are made of even simpler atoms. But you can do maths, draw pictures and predict text - probably.

The Computer is the same. It is the brain made up of neurons - building blocks.

We should start at the beginning.

At its most basic, you should understand that from simple rules we can make complex sytems.
A maths analogy - we must accept that we can have this arbitrary construct, this single value. Mathematically this is strange, how can something just exist and come from nothing? Ask the universe.
Anyway, once you have found peace, if we can have one we must then accept that we can multiples of things. This leads to the existence of numbers bigger than one.
With this concept of "multiple", we can now add these numbers bigger than one, addition. By the same patternm addition allows for multiplication. Multiplication allows for powers. Now we can represent many many types of real functions.

We can start conceptual first and then move to the electronics.

Similarly the computer must start at this most basic building block, a way to store the number one. 
Here's a good idea: one as a concept is the presence of something. Zero is the presence of nothing. So we have a conceptual object that is there if it is, or isn't if it isn't. 
Now at some point we have to tie this to a real phenomena and we know at some point that electricity is going to show up. Let's say that when there is electricity we have one, and when we don't we have zero.
What we have described is just an electrical signal.

Now we would like multiplication - but how can we do that?
Of course, we can have multiple signals - multiple wires in parallel. However, humans don't do this. Think of 100, do you imagine 100 points or is it the number one shifted up two places in the decimal base system? That's right, the human number system doesn't revolve around a bunch of ones. It is a system that allows "individual" numbers to increase until reaching a multiple of 10 at which point that place in the number will increase and one will be added to the next place.

Same for our circuit, We don't want one signal/wire for every "one", we want a way to represent multiciplicty without one for every number.
Now, if we wanted to do the same thing that humans do and represent the number 10 in circuits, we could try to do it as a single number, going up to 9, and then after that we have two signals.
If we had an analog computer with large gears this might be possible, maybe a 10-toothed gear system. 
However, we need to tie it back again to electricity and physical silicon switches at some point again. We might like a switch that does 10 different things when 10 levels of voltages are applied to it, but there isn't a material that does this on its own cheaply and in a useful way. Here's something amazing we do have: the number 2.

##Boolean arithmetic 

Now you're going to have to trust me that a 2-state system makes the most sense for these building blocks. I promised you a structure in the overview so for now just know that when we get into the hardware we'll discuss why we are using base 2.

We already have a thing that can perfectly represent 2 states - a signal. To reach our number 10, we can actually do the same thing we do with decimal numbers anyway. Just take the last digit in our number and add it to the digit to the left. Now we only need four of these signals to represent the number 10. We have our last number be 0 since 10 is even. Then 1. Then 0 again. And 1 again.






##Electronics

In the spirit of this book I will explain the very basics of a circuit with the assumption you have not learned this already, but you very likely have. I will not discuss the mathematics of circuits in series and parallel for it is not actually important.

The essential thing is to understand that wants to flow from a high point to a low point and it will do this by taking the path of least resistance, much like how a river forms.

The essential things to know is we have a source - the "high" point, the ground - the "low" point. We also have a thing called a resistor that makes it difficult for electricity to flow through. In our river analogy a resistor would be like hard rock. A river absolutely can erode away hard rock but it would prefer to avoid our resistor if necessary. If it finds a different path that has no resistor, it will take that path.
Now likely you will know that an electrical flow can travel in parallel even with two different resistance values, but with a resistance of 0 you can show that 100% of the current will flow down the path of no resistance so this simple explanation will suffice.

##Transistors

A transistor is not a lightswitch!

A transistor is always called a switch - this is confusing. The most common mechanical switch is a lightswitch - this type of switch does exactly two things. It allows current to pass when it is turned on, and it stays in its position once switched. Annoyingly, the transistor is referred to as a switch but it only does one of these things. If you "flip" the transistor it does not stay open. It is a pushbutton - it needs to be held open to allow current to pass through. It has another special feature that it allows current to pass through other than the input. It is called an amplifier - which is true - but it is not a multiplier which the name might imply. The amplification property on its own isn't really relevant for the logic we will be discussing - its importance is that the output can be connected to a common source so that when we eventually chain a bunch of these transistors together, the voltage output of the last transistor is commong from source - not from the outputs of previous gates. I.e. our signal isn't decreasing at every single step.

regeneration of logic



Again to fund the motivation for this, you can form ANY other combination of logic with NAND. This is more of a cost-saving measure because of course you can form any combination of gates using AND OR NOT.

AND gate

![and gate](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS2HpkERX6c4U7G9YUO7Ivx8rUbdUs_U2sSNg&s)

OR gate

![or gate](https://static.wixstatic.com/media/10da4b_ac20ecc6831e4a07a3427fb509ac96da~mv2.png/v1/fill/w_456,h_652,al_c,lg_1,q_85/10da4b_ac20ecc6831e4a07a3427fb509ac96da~mv2.png)

NOT gate

![not gate](https://cdn.prod.website-files.com/6634a8f8dd9b2a63c9e6be83/669d78d482a4499b76f2634b_311277.image0.jpeg)

Now if we wanted to chain these together infinitely as discussed before, we could make any boolean function. If we want to check if any of 100 inputs are true, we chain together a bunch of OR gates. (XOR is technically a distinct special operation but it itself is also just a chain where OR leads to high but AND shorts the output.)

As discussed before as well, without talking about circuits yet, we can form AND OR NOT using only NAND gates. Soooo, since we ARE talking about circuits, it would sure be convenient if we could manufacture a single gate that could be chained together to create ANY boolean function.


However, we can do something amazing...
Let's put 2 transistors in a circuit with one collector joined the other's emittor. Applying a voltage to our two imputs (the bases of our transistors) will short this circuit (assuming the collectors and emmitors are connected to source and ground.)

In this diagram we have the point AB. Note there is no resistor to AB but there is a resistor R1 to VCC. Thus normally AB has no connection to ground, instead it has a connection to Vcc. However, if, and only if BOTH A and B are high will there now be a connection to the ground. There is now a crossroads between ground, source and AB. Since source is blocked by a resistor, AB and ground will connect to each other, so our output AB is low.

![nand gates](https://mathcenter.oxford.emory.edu/site/cs170/nandFromTransistors/nand_gate.jpg)

Now we can actually chain these together to form the overflow behaviour as talked about before. We can add any size of numbers with enough gates, we multiply divide subtract etc etc etc...

We have maths, but we need a way to actually store our results.
(We could cheat and skip to CD's and other kinds of discs that use dyes heated by lasers or magnets to modify the values stored on them - but we're talking about transistors anyway and we eventually want to get to a CPU - right?)
We could ALSO talk about DRAM which uses a transistor and a capacitor, or flash memory which use floating-gate transistors which trap a charge on an isolated gate - buuuuut, nah... Let's JUST use transistors for now and none of this weird stuff I would have to introduce and explain. (I will eventually but at a high level, we're not in manufacturing).

Let's store data with just transistors - even better let's do it with just NAND.

![nand gates](https://sub.allaboutcircuits.com/images/04173.png)
 
Wow - NAND really can do anything!

So, IF you wanted to implement the whole of computing with only one type of gate - for example you were an early computer engineer who needed to build computers out of discrete IC's - you would be able to simplify your part inventory and bulk manufacture these simple parts for cheap.
Nowadays, people aren't stringing individual gates together - at least in modern CPU's, so we don't need to actually limit ourselves to only NAND gates.
But we have a bunch of other gate types we'd like to implement so why not implement them directly instead of out of 2-3 layers of NAND.
When designing a modern CPU we will use high level hardware description languages (HDLs) which take in our described circuits and optimise them for gate count, depth, speed, etc.


There's a lot more to computers as you might imagine - if we included all the peripherals we'd be here all day. The important part is that we now have both the theoretical and practical ability to compute and store the results of anything (but with theoretical hardware).