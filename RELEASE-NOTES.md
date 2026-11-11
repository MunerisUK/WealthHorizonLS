# Release notes

What changes in each build of WealthHorizon. The newest is at the top.

Each build is published as a Docker image tag with the same name, for example
`B1150`. To run a particular build, set `WH_TAG` in your `.env` file (see
[Updating](README.md#updating)). Back up before every update.

---

## [B____] First release

*[Date]*

The first build available to download. It includes:

- **Your Money file, read directly.** Import a `.mny` file, including one with
  a password, check every account's balance against Money before anything is
  created, and keep your splits, memos, payees and categories.
- **Accounts, investments, pensions and property in one place**, with prices
  and exchange rates updated from public sources when you ask, or on a
  schedule you switch on.
- **Exchange rates kept by date**, so a new rate never changes the history of
  your older transactions.
- **Payslips split for you** from a payroll PDF attached to the pay
  transaction, or typed in by hand.
- **Planning**: a guided plan for retirement, early retirement (FIRE) and
  financial independence, an advanced planner, a pension calculator, cash flow
  by account and savings goals.
- **UK tax and estate planning**: income, dividends and capital gains,
  residency and days present across countries, a CGT optimiser, Irish fund
  deemed disposals, and an estate and inheritance tax planner.
- **Documents** attached to accounts and transactions.
- **Backups** you can encrypt and schedule, written to a folder you can copy
  off the machine.
- **Feedback** from inside the app, with the details I need to fix a problem.

Not in this build:

- Open Banking bank connections are not switched on yet.

See the [user guide](docs/user-guide.md) for how to use each part.
