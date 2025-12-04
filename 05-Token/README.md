### Exploit
When we do arithmetics with uints, the result is also treated as a uint. 

In the require check "balances[msg.sender] - _value >= 0", there is an arithmetic of type a-b>=0.

if we pass values where a<b, then the result of the a-b would in theory negative, as our intuition suggests from math.

However as we know, small negative signed integers have the same binary value as really large unsigned  positive ones.

The problem is that on Solidity 0.6, there was no check to prevent reinpretation of values, so the developer thought they were doing a simple 
arithmetic subtraction a-b while in reality they did a-b and then the outcome was automatically cast as a uint256 without the developer knowing.

I created a script where I pass as argument "_value=30" and since "balances[msg.sender]==20" the result of the require check will be 
uint256(20) - uint256(30) ---------> uint256(-10) which equals to a really large positive unsigned integer.
