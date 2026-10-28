# ATLAS — XAUUSD Trading Journal

A static, dark-premium manual trading journal for XAUUSD. Built with HTML, CSS, and vanilla JavaScript so it can run locally or on GitHub Pages.

## Features
- Manually add, edit, delete closed trades.
- Net P/L = gross P/L + commission + swap. Enter costs as negative amounts.
- Dashboard: net P/L, return on configurable starting balance, win rate, profit factor, maximum realized drawdown, expectancy, average win/loss, ending realized equity.
- Equity curve and closed-trade drawdown curve.
- Filters for period, result, strategy and notes.
- CSV import/export.
- Browser-local persistence via `localStorage`.

## Important data and metric notes
- **No real trade data is included.** The dashboard starts empty.
- The default starting balance is a placeholder of USD 10,000. Double-click the metric cards to change it; the value is stored only in this browser.
- Gross P/L must be entered from your MT4 history or calculated using your broker's exact XAUUSD contract specifications. The app deliberately does not assume a universal gold contract size.
- Commission and swap should be negative when they are costs, positive only if a credit/refund is actually received.
- Win/loss classification uses **net P/L per trade** after commission and swap.
- Profit factor = sum of positive net trade results / absolute sum of negative net trade results.
- Expectancy = total net P/L / number of closed trades.
- Maximum drawdown is calculated from the sequence of **realized equity** (starting balance plus cumulative closed-trade net P/L). It does not include floating P/L, intraday equity, deposits, withdrawals, or open positions.
- Recovery factor = net P/L / maximum drawdown in USD; shown as unavailable when drawdown is zero.
- Average R-multiple uses only trades with a positive `Initial risk (USD)` entered. `R = net P/L / initial risk`.
- Sharpe ratio, Z-score, and floating drawdown are intentionally not shown in this starter version because they require additional methodological choices or richer data.

## Run locally
Open `index.html` in a modern browser. Trade data stays in that browser's local storage and is not automatically sent to GitHub.

## Publish with GitHub Pages
1. Create a repository, e.g. `trading-performance-journal`.
2. Upload `index.html` and `README.md` to the repository root.
3. Open **Settings → Pages**.
4. Under Build and deployment, select **Deploy from a branch**.
5. Select branch `main`, folder `/ (root)`, and save.
6. Wait for the Pages deployment, then open the URL GitHub displays.

## Privacy warning
A public GitHub Pages site is accessible to anyone with the URL. Browser-local trades are not automatically visible to other visitors, but they are not a secure multi-user database. Do not enter broker passwords, account numbers, or private personal information. If you want a public performance portfolio, export and review a sanitized dataset and publish only the statistics/trades you intentionally want to share. For private synchronized data, add a backend/database with authentication; GitHub Pages alone does not provide that.

## CSV format
Expected header includes at minimum: `date,side,lot,gross`.
Optional columns: `entry,exit,risk,commission,swap,strategy,session,mood,notes`.
Date format: `YYYY-MM-DD`; side: `BUY` or `SELL`.
