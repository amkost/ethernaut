### Exploit
The contract is using super predictable "randomness" by using the hash of the last block.
I simply created a contract that is using the exact same blockhash to select the winning side every time, i uploaded on sepolia and called it 10 times manually on different blocks each time.
