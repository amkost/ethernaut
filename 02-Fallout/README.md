# Fallout

### Goal
Become the owner of the contract.

### Exploit
The constructor is written incorrectly so we can just call it externally whenever:

```solidity
function Fal1out() public payable { ... }
