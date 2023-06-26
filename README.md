# BRC20 Fungible Token Contract with Ordinal Support

This repository contains an implementation of the ERC20 standard on Bitcoin built on the Bitcoin Computer, with additional ordinal support.

## Interface

The following interface is implemented by the BRC20 contract:

```javascript
interface IBRC20 {
  mint(publicKey: string, amount: number, ordinal?: string): Promise<string>
  totalSupply(): Promise<number>
  balanceOf(publicKey: string): Promise<number>
  transfer(to: string, amount: number): Promise<void>
}
```
## Ordinal Definitions

- Ordinal: A way to tokenize single Bitcoin satoshis.
- Satoshis Classification: Satoshis can be classified as "uncommon" or "rare" based on specific criteria.
- Multipliers: The contract allows defining different multipliers for "uncommon" and "rare" satoshis.
