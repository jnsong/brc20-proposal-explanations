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


## Usage

To incorporate ordinal support in your BRC20 contract, follow these steps:

1. **Define the multipliers for uncommon, rare, and epic satoshis** in your contract code or during deployment:

    ```javascript
    const MULTIPLIER_UNCOMMON = 1.5;
    const MULTIPLIER_RARE = 2.0;
    const MULTIPLIER_EPIC = 3.0;
    ```

2. **Implement the following helper functions** to handle ordinal-related operations:

    ```javascript
    // Retrieves the multiplier associated with a specific ordinal
    function getMultiplier(ordinal: string): number {
      if (ordinal === "uncommon") {
        return MULTIPLIER_UNCOMMON;
      } else if (ordinal === "rare") {
        return MULTIPLIER_RARE;
      } else if (ordinal === "epic") {
        return MULTIPLIER_EPIC;
      } else {
        return 1.0; // Default multiplier for common satoshis
      }
    }

    // Apply the ordinal multiplier to the token amount
    function applyOrdinalMultiplier(amount: number, ordinal: string): number {
      const multiplier = getMultiplier(ordinal);
      return amount * multiplier;
    }
    ```

3. Use the `mint` functions in your contract to **support the optional `ordinal` parameter** for minting and transferring tokens with specific ordinals.

4. Use the `balanceOf` function to **retrieve the balance of an account**, without considering the ordinal parameter.

## License

This project is licensed under the [MIT License](LICENSE).

