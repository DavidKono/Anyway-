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

## The Turing Machine



