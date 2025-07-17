# Credit Score Analysis of Aave V2 Wallets

This analysis evaluates wallet behavior using credit scores generated from transaction history.

## Score Distribution

| Score Range | Number of Wallets |
| 0-99        | 0 |
| 100-199     | 0 |
| 200-299     | 0 |
| 300-399     | 0 |
| 400-499     | 0 |
| 500-599     | 5 |
| 600-699     | 18 |
| 700-799     | 28 |
| 800-899     | 2243 |
| 900-999     | 192 |
| 1000-1099   | 1011 |


### Behavior of Wallets in the Low (0–299) Score Range

- Average Deposit: $nan
- Average Borrow: $nan
- Average Repay: $nan
- Average Repay-to-Borrow Ratio: nan
- Average Borrow-to-Deposit Ratio: nan
- Average Liquidations: nan
- Average Transactions per Month: nan


### Behavior of Wallets in the High (800–1000) Score Range

- Average Deposit: $166,712.61
- Average Borrow: $117,282.54
- Average Repay: $88,853.49
- Average Repay-to-Borrow Ratio: 0.28
- Average Borrow-to-Deposit Ratio: 7365425.07
- Average Liquidations: 0.02
- Average Transactions per Month: 14.77


## Key Observations
- Low-score wallets tend to have low repay activity, high borrow-deposit ratios, and liquidation events.
- High-score wallets show healthy repay behavior, high deposit activity, and minimal liquidations.
- Score distribution is skewed toward responsible DeFi users.

## Future Work
- Improve score granularity using time-series patterns
- Use anomaly detection for bot behavior
- Extend to other DeFi protocols for cross-platform reliability scoring
