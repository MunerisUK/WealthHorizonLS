# Using WealthHorizon

This guide covers the main things you will do in WealthHorizon, from bringing
in your Money file to backing up. It is a starting point, not the whole manual:
every page in the app has a **Help** button that explains that page in more
detail.

Installing, updating and moving WealthHorizon to another machine are covered in
the [README](../README.md).

> **Not financial advice.** The planning, tax and forecast pages work from the
> figures you enter. They help you think things through. They are not advice,
> a recommendation or a promise.

## Contents

1. [First steps](#1-first-steps)
2. [Bringing in your Money file](#2-bringing-in-your-money-file)
3. [Accounts and transactions](#3-accounts-and-transactions)
4. [Payslips](#4-payslips)
5. [Prices and exchange rates](#5-prices-and-exchange-rates)
6. [Keeping documents with your accounts](#6-keeping-documents-with-your-accounts)
7. [Planning ahead](#7-planning-ahead)
8. [Tax and your estate](#8-tax-and-your-estate)
9. [Reports](#9-reports)
10. [Backups](#10-backups)
11. [Your licence](#11-your-licence)
12. [Help and feedback](#12-help-and-feedback)

---

## 1. First steps

1. Open `http://<your-server>:8082` in a browser.
2. Choose **Register** and create your account. The first account on a new
   install becomes the **System Administrator**, so make this one yours.
3. Enter your licence key: **System Admin → Licence → Activate on this
   machine**. Until a key is active you can look around, but you cannot add or
   change anything.
4. Turn on **two-factor authentication**: open your profile, then
   **Security**. It asks for a code from an authenticator app when you sign
   in. Your finances deserve it.

Finding your way around:

- The menu on the left groups the pages: **Overview**, **Portfolio**,
  **Tax & Planning**, **Tools** and **System**.
- **Quick Access** (the lightning-bolt button, or **Ctrl+K** / **Cmd+K**)
  jumps to any page by name.
- WealthHorizon works on a phone or tablet as well as a computer.

Other people in your household can have their own sign-in. Invite them under
**System → Family**. A child member can look at the household's accounts but
not change them.

## 2. Bringing in your Money file

Go to **Accounts**, open the **⋯** menu and choose **Import from MS Money**.

WealthHorizon reads:

- a Money **`.mny`** file directly, including one with a password (it asks
  for the password)
- an Access `.mdb` / `.accdb` file
- an Excel export workbook, a `.qif` file, or a `.csv` **Account Transactions**
  report from Money

Nothing is created until you have checked it. The review screen lists every
account with what WealthHorizon thinks it is, worked out from the name and the
file. For each one you can change:

- **Type**: current, savings, investment, retirement, credit card, loan,
  mortgage and so on
- **Wrapper**: ISA, Cash ISA, Lifetime ISA, SIPP, or none
- **Currency** and **Jurisdiction** (where the account is held), and whether it
  is **Offshore**

If most of your accounts are outside the UK, set the **Default jurisdiction**
and **Default currency** at the top once rather than changing every row.

**Check the balances before you import.** Each account shows the balance it
will have, worked out the way Money works it out, so you can compare it with
Money line by line:

- a cash account is its opening balance plus its transactions
- an investment account is the value of what it holds, not the sum of its
  transactions
- the **Not counted** column shows Money's scheduled items that were never
  entered. They come across, but no balance counts them, just as in Money.

Splits, memos, payees and categories all come across, and Money's
`Parent : Child` categories become a proper hierarchy.

## 3. Accounts and transactions

**Accounts** lists everything you hold. Open an account to see:

- **Transactions**, with a **running balance** on every row, as in Money. If
  your statement and WealthHorizon disagree, look for the row where the two
  balances part company.
- **Holdings**, for investment accounts: what you hold, its price, value, cost
  and gain or loss.

From an account you can **Add**, **Edit** and **Split** transactions, and move
money between accounts. A split keeps its total fixed and counts down what is
left to allocate, so you cannot save one that does not add up.

To add statements after the first import, use **Import** with a file from your
bank. Common formats work, including OFX, QFX, QIF, CSV and PDF card
statements. Rows you have already imported are recognised and skipped.

If you hold shares with **Trading 212**, you can connect it with an API key
and your holdings are fetched for you. Create the key **read-only** in the
Trading 212 app: WealthHorizon only ever reads, but a key created with trading
permissions could place orders in anyone's hands.

Bank connections through **Open Banking** are not switched on yet.

## 4. Payslips

When your salary arrives in an account, you can split it into the lines on your
payslip: gross pay, tax, National Insurance, pension and so on.

- **From a PDF.** On the pay transaction, click the **PDF icon** and attach the
  payslip. WealthHorizon reads the pay lines and deductions and shows each one
  beside the amount your bank actually paid. Nothing is changed until you
  apply it, and you can only apply it when the lines add up to what was paid.
  This works with payslips your employer's payroll system produced as a PDF. A
  scan or photo of a paper payslip will not read.
- **Without a PDF.** Open the transaction, choose **Split…** and then **Split
  it as a payslip**, and type the lines in. If you have split an earlier
  payslip on the same account, **Use last payslip's lines** fills them in for
  you to check.

Use the transaction that is already in the account. Do not create a new one
for the payslip, or your pay will be counted twice.

## 5. Prices and exchange rates

**Prices** keeps the prices of your shares and funds, and **FX Rates** keeps
your exchange rates.

Exchange rates are **kept by date**. When you add a new rate, older
transactions keep the rate that applied on their own date, so your history
does not change behind your back. If you hold accounts in more than one
currency, this is the part of Money that WealthHorizon does differently.

- Press **Update prices** to fetch the latest prices and rates. It tells you
  which ones it could not update, and why.
- Automatic updates are **off** until you switch them on, because they contact
  outside price sources on a timer.
- An account in a currency with no exchange rate on file is **left out** of
  your totals and named, rather than added in at a guess. Add the rate and it
  joins.

## 6. Keeping documents with your accounts

- Every account has a **Documents** card. Attach statements, contract notes,
  policies, anything that belongs with that account.
- **Tools → Documents** lists everything in one place. Files can be up to
  25 MB, and you can link each to an account and add a note.

Documents are stored in the `data/documents` folder next to your
`docker-compose.yml`, so include that folder in your backups.

## 7. Planning ahead

- **Planning** is a guided set of questions that builds an indicative plan. You
  choose the kind of plan first: traditional retirement, early retirement
  (FIRE), financial independence while still working, semi-retirement, or
  selling a business. It only asks what applies to you and fills in what it
  already knows from your accounts.
- **Advanced Planner** is the same engine with every assumption in your hands.
  You can carry your answers across from Planning.
- **Pension Calculator** gives a quick answer: pick the age you stop work and
  how much tax-free cash you take, and it shows what that leaves you each
  month.
- **Cash Flow** shows what each account will hold, day by day, so you can see a
  shortfall before it happens.
- **Goals** tracks what you are saving for, from the account the money sits in.

## 8. Tax and your estate

This is where a lot of the work in WealthHorizon has gone, with the UK first.

- **Tax** models income, dividends and capital gains for a person and a tax
  year. Its **Residency** tab records where each person was resident and
  domiciled over time, and **Days present** counts days in each country against
  the residence tests (the UK Statutory Residence Test among them). Useful if
  you live, work or hold money in more than one country.
- **CGT Optimiser** helps you use your capital gains allowance, lot by lot.
  Gains inside an ISA or pension are left out, because tax cannot reach them.
- **Irish funds**: a fund or ETF domiciled in Ireland is taxed as if sold every
  eight years. **Tax → Ireland** lists when each holding's next one falls.
- **Estate & IHT Planner** models your estate and a possible inheritance tax
  bill, including gifts and reliefs, from your accounts as they stand today.
- **Renewals** reminds you of things that cost money when they lapse:
  insurance, the MOT, a fixed rate ending.
- **Nominees** lets you name someone who can see (but not change) your accounts
  if you cannot. **Readiness** checks whether your affairs would be usable by
  someone else on the day they are needed.

## 9. Reports

**Reports** has the reports Money users will know, among them income and
spending, spending by category and payee, budgets, account balances, loan
terms, investment performance and tax-related transactions. You can customise
a report and print it or save it as a PDF.

**Wealth Report** produces a summary of everything you hold at a point in time.

## 10. Backups

Back up before every update, and keep a copy somewhere other than the machine
WealthHorizon runs on.

Go to **Tools → Backup & Restore**:

- **Manual Backup** saves your data as a file. You can encrypt it with a
  passphrase. Do not lose the passphrase: nobody can open the backup without it.
- **Schedule** makes backups automatically, daily, weekly or monthly.
- **Restore** brings a backup back.

For a scheduled backup to land outside the database, choose **Also write a copy
to a folder** and enter **`/backups`**. That folder is `data/backups` next to
your `docker-compose.yml`. Press **Check the folder** before saving.

Then copy `data/backups` (and `data/documents`) to another disk, another
machine or a cloud drive. A backup on the same disk as the database will not
help if that disk fails.

**Download my data**, under **People & access → Account Access**, gives you a
file of everything WealthHorizon holds about you and your household at any
time.

## 11. Your licence

- You activate your key once, under **System Admin → Licence**. The key works
  on one machine at a time.
- WealthHorizon checks the key with the licensing service from time to time.
  If your server is offline for a while, it carries on working for a grace
  period before it needs to check in again.
- If your licence ends, WealthHorizon becomes **read-only**. You can still sign
  in, see everything and export it. You just cannot add or change anything
  until a key is active again. Your data is never locked away from you.
- Moving to a new machine: **System Admin → Licence → Move this licence** on
  the old one first, then activate the key on the new one. The
  [README](../README.md#moving-to-another-machine) has the full steps.

## 12. Help and feedback

- **Help**, in the top bar, explains the page you are on.
- **Feedback**, the speech-bubble button beside Help, sends me a bug report or
  an idea from any page. It includes the build number, the page, your browser
  and the last error the app saw, so I can usually fix a problem without
  needing to ask you questions. It never includes an account name, a figure or
  your licence key. **My reports**, underneath, shows where each of your
  reports has got to.
- **What's New** in the app lists the changes in your build.

Please use the Feedback page rather than a public issue on GitHub for anything
that involves your data. Public issues here are only for problems installing or
updating.
