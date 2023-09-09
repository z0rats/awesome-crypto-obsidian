#sec #solidity #reentrancy
[[Solidity]]


### Regular Reentrancy

Let's say that contract `A` calls contract `B`.

Reentracy exploit allows `B` to call back into `A` before `A` finishes execution.

### Read-Only Reentrancy

The classical examples of reentrancy typically reenter in a state-modifying function so that an inconsistent state is used to perform malicious writes on the contract’s storage. Typically, contracts guard themselves with reentrancy locks, protecting their state from such malicious actions. In contrast, the read-only reentrancy is a reentrancy scenario where a `view` function is reentered which in most cases is unguarded as it does not modify the contract’s state. However, if the state is inconsistent, wrong values could be reported. Other protocols relying on a return value, can be tricked into reading the wrong state to perform unwanted actions.

### Preventative Techniques

-   Ensure all state changes happen before calling external contracts
-   Use function modifiers that prevent re-entrancy [[Mutex Pattern]]