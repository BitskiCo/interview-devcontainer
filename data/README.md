# Sample Data

## Data Types

| Type      | Description                                           |
| --------- | ----------------------------------------------------- |
| H160      | Hex-encoded 160-bit hash                              |
| H256      | Hex-encoded 256-bit hash                              |
| Integer   |                                                       |
| String    |                                                       |
| Timestamp | Timestamp in UTC, i.e. `2022-11-28 00:00:11`          |
| U256      | Hex-encoded 256-bit unsigned integer                  |
| RLP       | Hex-encoded [Recursive Length Prefix (RLP) data][rlp] |

## Schema

`token_transfers.csv`

| Field              | Type      | Description                    |
| ------------------ | --------- | ------------------------------ |
| `chain_id`         | Integer   | [Ethereum chain id][chainlist] |
| `from_address`     | H160      | Sender address                 |
| `to_address`       | H160      | Recipient address              |
| `contract_address` | H160      | Ethereum contract address      |
| `token_id`         | U256      |                                |
| `token_type`       | String    | ERC20, ERC271, ERC155          |
| `amount`           | U256      |                                |
| `transaction_hash` | H256      | Transaction hash               |
| `log_index`        | Integer   |                                |
| `block_number`     | Integer   |                                |
| `block_hash`       | H256      |                                |
| `block_timestamp`  | Timestamp |                                |

`transactions.csv`

| Field                         | Type      | Description                    |
| ----------------------------- | --------- | ------------------------------ |
| `chain_id`                    | Integer   | [Ethereum chain id][chainlist] |
| `hash`                        | H256      | Transaction hash               |
| `nonce`                       | Integer   |                                |
| `transaction_index`           | Integer   |                                |
| `from_address`                | H160      | Sender address                 |
| `to_address`                  | H160      | Recipient address              |
| `value`                       | Integer   |                                |
| `gas`                         | Integer   |                                |
| `gas_price`                   | Integer   |                                |
| `input`                       | RLP       |                                |
| `block_hash`                  | H256      |                                |
| `block_number`                | Integer   |                                |
| `block_timestamp`             | Timestamp |                                |
| `receipt_cumulative_gas_used` | Integer   |                                |
| `receipt_gas_used`            | Integer   |                                |
| `receipt_contract_address`    | H160      |                                |
| `receipt_root`                | Integer   |                                |
| `receipt_status`              | Integer   |                                |
| `max_fee_per_gas`             | Integer   |                                |
| `max_priority_fee_per_gas`    | Integer   |                                |
| `transaction_type`            |           |                                |
| `receipt_effective_gas_price` |           |                                |

[chainlist]: https://chainlist.org
[rlp]: https://ethereum.org/en/developers/docs/data-structures-and-encoding/rlp/
