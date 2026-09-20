# Monte Carlo Revenue-at-Risk and Pricing Scenario Simulator

A Jupyter Notebook project that compares subscription pricing decisions under uncertain inflation, USD/TRY, demand, price sensitivity, and churn. The business is synthetic, with 100,000 starting customers across three plans and three customer segments.

The question is practical: which price change improves the business without taking too much revenue risk or losing too many customers?

## What the notebook does

- Simulates 12 months of customer signups, churn, revenue, and costs across 5,000 economic paths.
- Compares no increase, upfront and staged increases, inflation-linked pricing, plan-specific increases, and a policy that protects existing customers temporarily.
- Reports expected revenue, the fifth percentile, probability of missing a revenue target, contribution, gross margin, and year-end customers.
- Checks how the conclusions change under demand, inflation, FX, and price-sensitivity stress.
- Searches a small grid of prices subject to a revenue-risk limit and a minimum year-end customer count, then evaluates the selected policy on fresh simulations.

The notebook has 30 numbered modules. Code and comments are in English; run the modules in order.

## Example result

With the included assumptions, a staged 15% increase was selected. On fresh simulations, its expected annual revenue excluding tax was TRY 353.37 million, its expected gross margin was 21.8%, and its year-end customer count was about 96,376. Its estimated probability of missing the revenue target was 27.1%. These numbers change when the assumptions change and are not forecasts for a real company.

## Run locally

From this folder, install the dependencies and start Jupyter:

```bash
python3 -m pip install -r requirements.txt
python3 -m notebook Monte_Carlo_Revenue_at_Risk.ipynb
```

In Jupyter, use **Restart Kernel and Run All Cells**. Run Jupyter from this folder so that the final module saves `pricing_comparison.csv` here. The included CSV shows the example run.

Change the exchange rate, prices, assumed tax, and payment commission in Module 2; starting customers and monthly signups in Module 4; or economic assumptions and decision limits in Module 6. Run all cells again after changing an input.

## How to read the results

Plan prices and company revenue exclude tax. The model adds an assumed 25% tax to the customer bill, records that tax separately from revenue, and charges a 1.5% payment commission on the tax-inclusive payment. Starting gross margins are calibrated to 20%, 22.5%, and 25% for Basic, Standard, and Premium. These are project assumptions, not claims about a particular company's costs or the tax treatment of a real product.

`pricing_comparison.csv` contains monetary figures in TRY; the target-miss probability is a fraction between 0 and 1. Customer counts during the simulation are continuous *customer equivalents* rather than individual people.

## Limits

The data and behavioral responses are synthetic. The model does not include plan switching, customer lifetime value after month 12, or a causal estimate of how real customers respond to price changes. The selected policy is the best among the tested candidates under these assumptions, not a universal optimum.
