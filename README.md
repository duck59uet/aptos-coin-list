# Adding Your Coin to the Coin List

## Steps to Add Your Coin:

1. **Fork the repository**.
2. **Add your token icon**: Upload `TOKEN_ICON.svg` to the `icons` folder (ensure it is no larger than 100x100 pixels).
3. **Edit `token.json`**:
    - Add a `RawCoinInfo` entry to the `token.json` file.
    - Try to add it at a random location in `token.json` to prevent merge conflicts.
    - For `unique_index`, choose a random number that hasn't been used yet.
4. **Submit a pull request (PR)**.
5. **Notify the team**: Shout about your PR in [Telegram (TG)](https://t.me/+iouNCXkztwJhODQ1).

---

## RawCoinInfo Format

When adding your coin, ensure the `RawCoinInfo` contains the following fields:

- **name**: The coin name, preferably including the project name.
- **symbol**: A globally unique symbol within this coin registry.
- **official_symbol**: Same as `aptos_framework::coin::CoinInfo.symbol`. Duplicates are allowed.
- **coingecko_id**: The coingecko ID, used by various clients to look up the coin price.
- **decimals**: The number of decimals for the coin.
- **logo_url**: A URL to the token logo (preferably a `raw.githubusercontent.com` URL).
- **project_url**: The project website URL.
- **type**: Either `COIN` or `FUNGIBLE_ASSET`.
- **coin_type**: Coin type information for `COIN` types.
    - **type**: The coin type in the format `module_address::module_name::struct_name`.
    - **account_address**: The account address of the module.
    - **module_name**: The module name.
    - **struct_name**: The struct name.
- **fungible_asset**: Asset type information for `FUNGIBLE_ASSET` types.
- **unique_index**: A unique index for the coin (preferably a random number).

---

## Examples

### COIN Example:

```json
{
  "name": "Aptos Coin",
  "symbol": "APT",
  "official_symbol": "APT",
  "coingecko_id": "aptos",
  "decimals": 8,
  "logo_url": "https://raw.githubusercontent.com/Cellana-Finance/aptos-coin-list/main/icons/APT.webp",
  "project_url": "https://aptoslabs.com/",
  "type": "COIN",
  "coin_type": {
    "type": "0x1::aptos_coin::AptosCoin",
    "account_address": "0x1",
    "module_name": "aptos_coin",
    "struct_name": "AptosCoin"
  },
  "unique_index": 1
}
```

### FUNGIBLE_ASSET Example:
```json
{
  "name": "CELLANA",
  "symbol": "CELL",
  "official_symbol": "CELL",
  "coingecko_id": "cellana-finance",
  "decimals": 8,
  "logo_url": "https://raw.githubusercontent.com/Cellana-Finance/aptos-coin-list/main/icons/cell.svg",
  "project_url": "https://app.cellana.finance",
  "type": "FUNGIBLE_ASSET",
  "fungible_asset": "0x2ebb2ccac5e027a87fa0e2e5f656a3a4238d6a48d93ec9b610d570fc0aa0df12",
  "unique_index": 5
}
```
