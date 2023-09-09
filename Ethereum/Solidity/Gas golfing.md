[[Solidity]]

GasBad is an open-source project that evaluates gas efficiency in Solidity libraries - https://github.com/ciwines/gas-bad

As an example: 
	for (uint256 i = 0; i < 100; ++i)
should be replaced with:
	for (uint256 i; i < 100; ++i)
