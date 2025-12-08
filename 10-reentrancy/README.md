### Exploit
When I call the withdraw function of the vulnerable contract, it first sends me the ETH and then it reduces my balance.
However, if called from a contract, sending ETH means it calls the receive() function of the contract.
So I just create a malicious receive() function that will also call withdraw, which will withdraw again since it has priority on execution and the balance has not been updated yet.
