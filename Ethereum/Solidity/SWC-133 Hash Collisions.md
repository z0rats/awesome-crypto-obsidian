[[Solidity]]

https://swcregistry.io/docs/SWC-133

## Description

Using `abi.encodePacked()` with multiple variable length arguments can, in certain situations, lead to a hash collision. Since `abi.encodePacked()` packs all elements in order regardless of whether they're part of an array, you can move elements between arrays and, so long as all elements are in the same order, it will return the same encoding. In a signature verification situation, an attacker could exploit this by modifying the position of elements in a previous function call to effectively bypass authorization.

## Remediation

**abi.encode:**
-   If you are dealing with more than one dynamic data type as it **prevents** collision.

**abi.encodePacked:**
-   Takes all types of data and any amount of input.

When using `abi.encodePacked()`, it's crucial to ensure that a matching signature cannot be achieved using different parameters. To do so, either do not allow users access to parameters used in `abi.encodePacked()`, or use fixed length arrays. Alternatively, you can simply use `abi.encode()` instead.

