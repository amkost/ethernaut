# Fallback

### Goal
Become owner and withdraw funds.

### Exploit
- First call `contribute()` with a small amount so `contributions[msg.sender] > 0`.
- Then send ETH directly to the contract (no function call).  
  This triggers the `receive()` function.
- `receive()` sets `owner = msg.sender`, giving you ownership.
- Finally, call `withdraw()`.

### Key Point
Direct ETH sends can trigger `receive()` and change ownership if not designed carefully.
