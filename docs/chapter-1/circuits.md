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