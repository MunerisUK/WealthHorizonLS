# Release notes

What changes in each build of WealthHorizon. The newest is at the top.

Builds come two ways:

- **Windows:** an installer, `WealthHorizon-Setup-B….exe`, on the
  [Releases](https://github.com/MunerisUK/WealthHorizonLS/releases) page. To
  update, run the newer installer over the top.
- **Docker:** an image tag with the build's name, for example `B1047`. To run a
  particular build, set `WH_TAG` in your `.env` file (see
  [Updating](README.md#updating)).

Back up before every update.

---

## B1067: WealthHorizon for Windows

*16 November 2026*

**WealthHorizon now installs on Windows 10 and 11 without Docker.** Download
`WealthHorizon-Setup-B1067.exe` from the
[latest release](https://github.com/MunerisUK/WealthHorizonLS/releases/latest)
and run it. See [Install on Windows](README.md#install-on-windows).

This build is the Windows installer only. Docker users stay on B1047 for now;
the next Docker build will include everything below.

New:

- **Stocks & Shares, under Portfolio.** All your investment accounts together
  as one portfolio. Each account has its own setting for whether it appears
  there.
- **Banks and providers for the UK, the US and Ireland**, with their logos, to
  choose from when you add an account.

Fixed:

- **Money files:** credit cards no longer come in as bank accounts, and a Money
  Home & Business file's receivables and sales tax come in as an asset and a
  loan.
- **Statements:** an OFX or QIF download is read for what it is, whatever the
  file is called. An American Express `.csv` no longer reads charges as
  deposits. QIF and OFX files can be chosen on an iPad.
- **Planning:** "Are you tracking to plan?" compares like with like. A plan
  that starts in a past year no longer grows today's balances through the years
  already gone.

---

## B1047: first release

*11 November 2026*

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
