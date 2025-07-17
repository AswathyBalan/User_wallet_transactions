# User_wallet_transactions
 Crediting Score to transaction-level data from the Aave V2 protocol in json format. Each record corresponds to a wallet interacting with the protocol through actions such as `deposit`, `borrow`, `repay`, `redeemunderlying`, and `liqu idationcall`.
 The scores range from 0 to 1000, indicating the risk profile of each wallet.
 
#Prerequisites

Python 3.8 or higher

Required libraries :
pip install matplotlib seaborn
pip install numpy scikit-learn
The project uses pandas,matplotlib,seaborn,json,datetime and collections.defaultdict. 

**Methodology**

#Data Preprocessing 
- Loaded JSON data and grouped by wallet.
- Converted timestamps to datetime format
- Normalized token amounts using token decimals(6 for USDC/USDT, 18 otherwise).
- Converted to USD using available asset prices.

**Feature Engineering**

To evaluate the reliability of each wallet on the Aave V2 protocol, a set of behavioral and transactional features derived from raw transaction data. Aggregated transactions by wallet address and calculated the total USD value of key actions such as deposit, borrow, repay, and liquidationcall, after normalizing for token decimal differences (e.g., USDC/USDT with 6 decimals, others with 18). Then computed important financial ratios, including the repay-to-borrow ratio (indicating how much of borrowed value has been repaid) and the borrow-to-deposit ratio (showing how aggressively the user borrows relative to deposits). Additionally, measured wallet activity over time by calculating monthly transaction frequency and protocol lifetime (days between first and last transaction). The number of liquidation events was also recorded as a key indicator of risk. These features collectively captured the responsible or risky behavior of wallets, serving as the foundation for the final credit score calculation.

**Scoring Logic(Rule-Based)**

- **Base score**: 1000
- **Penalties**:
  - `-100` if no `repay` action
  - `-100` if `repay/borrow < 0.5`
  - `-200` if `borrow/deposit > 2`
  - `-100 * number of liquidations`, capped at `-300`
- **Rewards**:
  - Up to `+100` for high deposit volume (`min(100, deposit/1000)`)
  - Up to `+100` for high transaction frequency (`min(100, tx_per_month * 5)`)
- **Final score** is clamped between 0 and 1000

**Run the script**

git clone https://github.com/AswathyBalan/User_wallet_transactions.git

cd User_wallet_transactions

