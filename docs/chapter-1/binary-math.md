From our basic computer model we have surmised 

The first thing we want our basic computer model to be able to do is to be a basic counter.  
This fulfills the basic goal we lined out of having multiplicity - i.e. numbers bigger than 1.

Let's think about how out boolean operations can perform addition out of simple rules.  
We begin with the number 0. I will be denoting the result of our binary numbers with a 'b' at the start as is standard. To add b1 to b0, we look at our available operator. We can see that either using OR or the XOR will output a 1 so we should use one these for adding our numbers. Ironically using AND does not result in 1, why not?

Now our results is b1. Let's add another b1 to it. Now we know for a fact that b1 plus b1 is b10 (2 in decimal), so whatever logic we are implementng should obviously do that.

Note you will need log 2 10 = 3.322 times the number of binary components to do arithmetic than decimal. 
Note log3 10 is only 2.096