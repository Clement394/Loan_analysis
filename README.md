# Mortgage Default Analysis 

Analysis of mortgage defaults in a loan pool, originated just before the 2008 US financial crisis. The whole analysis is in one notebook.

## Notebook structure

1. **Determinants of default**: keeps first-lien loans, builds one observation per loan, flags a loan as defaulted if it ever reaches a default-type delinquency status (`9`, `F`, `L`, `R`, `B`), merges HPA data by zip code, and fits a logistic regression of default on FICO, LTV, DTI, interest rate, original balance, documentation level, cash-out refinancing, balloon feature, investor and secondary-residence status, and HPA. Also includes a correlation matrix and a DTI histogram.
2. **Balloon loans**: share of balloon loans and default rate of balloon vs. non-balloon loans.
3. **House price appreciation**: distribution of `HPA2006_00`.
4. **Loan modifications**: number of modified loans (all loans, then first-lien only), delinquency status before modification, changes in rate and balance at modification, and re-default rate after modification.
5. **Total losses**: sum of the final cumulative loss of each loan.

## Main results

- Default rate (first-lien loans): 62.4%
- Logistic regression (3,660 loans, pseudo R-squared 0.106): default is higher with higher LTV and for secondary residences, and lower with higher FICO, full documentation, cash-out refinancing and higher HPA between 2010 and 2006 (`HPA2010_06`). DTI and `HPA2006_00` are not statistically significant.
- Balloon loans: 41.8% of the sample; default rate of 68.0% vs. 58.4% for non-balloon loans
- Modified loans: 729 in total, 703 among first-lien loans
- Re-default rate after modification: 44.9%
- Total cumulative loss: about $224.7 million

## Requirements

- Python 3.11+
- `pandas`, `matplotlib`, `seaborn`, `statsmodels`, `openpyxl` (needed by `pandas.read_excel`)
- Jupyter (or the VS Code notebook extension)

```bash
pip install pandas matplotlib seaborn statsmodels openpyxl jupyter
```
