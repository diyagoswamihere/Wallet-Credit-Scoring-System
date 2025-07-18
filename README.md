# Wallet-Credit-Scoring-System

This project assigns credit scores (0-1000) to wallets based on Aave V2 transaction data. Higher scores indicate reliable usage, while lower scores suggest risky or bot-like behavior. The script processes user-transactions.json, creates features, calculates scores, and analyzes the results.

Method:- 
1. Data Loading: Loaded user-transactions.json using pandas and flattened actionData into columns like amount and assetSymbol.
2. Feature Engineering:
  a.Total transactions: Count of all actions.
  b.Time span: Days between first and last transaction.
  c.Total deposits, borrows, repays, redeems: Sum of amounts for each action.
  d.Unique assets: Number of distinct assets.
  e.Liquidation count: Number of times wallet was liquidated (0 if no data).
3. Scoring:
  a.Base score: 500
  b.Bonuses:
   Time: Up to 200 points for 1 year.
   Repayment: 100 points if repays >= borrows or no borrows, else proportional.
   Asset diversity: Up to 100 points for 5+ assets.
  c.Penalty: -100 per liquidation, capped at 500.
  d.Scores clamped between 0 and 1000.
4. Analysis: Plotted score distribution and analyzed wallets in 0-400 and 600-1000 ranges.

How to Run:- 

1. Install dependencies: pip install pandas numpy matplotlib seaborn
2. Place user-transactions.json in the same directory.
3. Run: python wallet_scoring.py
4. Outputs:
  wallet_features.csv: Wallet features.
  wallet_scores.csv: Wallet addresses and scores.
  score_distribution.png: Score distribution plot.

Files:-

wallet_scoring.py: Main script.<br>
README.md: This file.<br>
analysis.md: Score distribution and wallet behavior analysis.<br>
score_distribution.png: Plot of score distribution.
