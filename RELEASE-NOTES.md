# Release notes

What changes in each build of WealthHorizon. The newest is at the top.

Every release on the [Releases](https://github.com/MunerisUK/WealthHorizonLS/releases)
page also carries **release-notes.html**: download it and open it in your
browser to pick any release and see what it fixed and what it added. This page
has the same notes as plain text.

Builds come two ways:

- **Windows:** an installer, `WealthHorizon-Setup-B….exe`, on the
  [Releases](https://github.com/MunerisUK/WealthHorizonLS/releases) page. To
  update, run the newer installer over the top.
- **Docker:** an image tag with the build's name, for example `B1378`. To run a
  particular build, set `WH_TAG` in your `.env` file (see
  [Updating](README.md#updating)).

Back up before every update.

---

## B1378

*26 November 2026*

- **Windows:** `WealthHorizon-Setup-B1378.exe` on the
  [B1378 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1378).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1378`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Added or enhanced:

- **Add a logo from the account.** Where the bank's logo could not be found (a
  Bank of America account showed "AM"), the mark at the top of the account's
  page is now a button for a System Administrator, Add a logo for the bank,
  which opens that bank on Financial Institutions ready to upload one.
- **Payment and Deposit columns, as in Money.** In an account's register, ⋯ →
  Payment and Deposit columns shows money out and money in in two columns,
  each as a positive figure, in place of Type and one Amount. It is kept on
  this device, and One Amount column switches back.
- **Arrange the Accounts sections.** Accounts → ⋯ → Arrange sections moves
  each section, Current, Savings, Credit cards and the rest, up or down, so
  they sit in the order you want. It is kept on this device, and Usual order
  puts it back.
- **Categories as a tree.** The Categories page lists each sub-category
  indented under its parent, as Money does, and a parent folds its
  sub-categories away. They were listed level by level, so a sub-category
  could sit a screen away from its parent.
- **Start again is easier to find.** My Account and System Admin each have a
  Start again card that takes you straight to it, under Backup & Restore →
  Restore, where it still lives.
- **The menu starts across the top for someone new.** As Money has it. Anyone
  already using WealthHorizon keeps the side menu unless they move it, and a
  choice made on a device is kept there.

---

## B1374

*26 November 2026*

- **Windows:** `WealthHorizon-Setup-B1374.exe` on the
  [B1374 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1374).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1374`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Unticking Repeat stops the payment repeating.** The tick shows when any
  recurring item in the account names the payee, but unticking removed only
  one, so a payment with two (a salary imported from Money and also ticked in
  the register) stayed ticked and nothing seemed to happen. Untick now stops
  every recurring item that row belongs to in the account, and says so if
  there is none.
- **The Payslip and Split badges stay readable beside a long payee.** They
  were squeezed onto two lines ("Paysli / p").
- **Card purchases no longer show as Income on the Month-end plan.** Money
  into a credit card is never income: a regular item recorded that way shows
  as *Into the card* and is not counted, and regular money into a card is no
  longer offered as an income item. A card whose purchases are recorded as
  money in (an Amex statement imported before 4 October 2026) is named under
  the list, with how to import it again.
- **"Tax treatment" everywhere in a US household.** The Wrapper columns, the
  Tax wrapper labels, the account import and merge screens, Rebalance,
  Allocation, the Planner, Tax, the report list and System Admin all read
  "Treatment" or "Tax treatment" in a US household. Everyone else sees no
  change.
- **Error messages name WealthHorizon, not "the server".** When WealthHorizon
  is slow or still starting it now says "WealthHorizon is still working on
  that…" or "WealthHorizon is starting up or not running", instead of "Gateway
  Time-out".
- **One household on first sign-in.** Signing in for the first time could
  create several empty households for the same person. It now creates exactly
  one.
- **An expired licence no longer counts down to read-only on a version it
  covers.** When the licence provider reports a key as expired, WealthHorizon
  now keeps its end date: a version released on or before that date keeps
  working and the Licence card says updates have ended; a later version
  becomes read-only and says to renew. With no end date known, the banner says
  the provider reports the key as expired, when it last checked, and to press
  Check now if you have renewed.
- **"A newer build is available" works on the Windows app.** The update check,
  and the heartbeat if you switch it on, now use the relay the app was built
  with, as feedback already did.
- **A big Money import no longer goes in twice (or three times).** On the
  Windows app a large file outlasted the wait for an answer: the page said
  nothing had been imported while it carried on and finished, and each retry
  brought the whole file in again. The import now runs in the background with
  a progress bar, a second import cannot start while one runs, and the dialog
  only says nothing was imported when that is so.
- **Start again finishes, and shows how far it has got.** On a large household
  it timed out, then said it was already running with nothing to show for it,
  and every attempt stored another complete backup. It now runs in the
  background with progress, keeps only the newest "before Start again" backup,
  and says where that backup is kept (inside WealthHorizon, under Snapshots,
  with Download to save it as a file). Deleting is much faster: 41 links
  between tables were missing the index that makes it quick.

Added or enhanced:

- **One icon everywhere: the white arrow on green.** The browser tab, an
  installed app and the Windows desktop and Start-menu shortcuts now show the
  same mark as the app's top bar, a white rising arrow on a green square. They
  showed an older navy "WH" design. Windows may keep the old shortcut picture
  until its icon cache refreshes or you sign out and back in.
- **Back up to OneDrive.** Where WealthHorizon runs on a Windows computer with
  OneDrive set up, Backup → Schedule offers **Back up to OneDrive**: it makes
  a WealthHorizon Backups folder there and writes each scheduled backup into
  it, encrypted with your backup passphrase, so OneDrive keeps a copy away
  from the computer. Anyone can choose it; other folders still need a System
  Administrator. Restore the latest file on any computer to recover.
- **The Month-end plan's list can be worked with.** Click a total (Coming in,
  Bills, Credit cards, Transfers, Left after bills and cards) to see only the
  entries that make it up. Change one entry's amount or date this time only,
  leave one out (a duplicate, say) and bring it back, and add a one-off entry
  such as an expected refund, which can be deleted again. From and To choose
  the dates the list covers, without changing the plan's.
- **Where your data is.** System Admin shows where WealthHorizon keeps its
  data (on Windows, C:\ProgramData\WealthHorizon unless it was moved; on
  Docker, the database container's volume) and how big the database is.
- **Privacy & connections.** A new page under Tools lists every connection
  WealthHorizon makes to the internet: what it is, where it goes, what is
  sent, when, and whether it is on by default. There is no analytics and no
  tracking.
- **Remove empty household.** System Admin → Backup & Restore lists one row
  per household, marked Primary or Empty extra household; Export and Restore
  act on that row's household, and a System Administrator can remove an extra
  household that has nothing in it, after confirming. The removal is recorded
  in the audit log.
- **The help explains "the server".** WealthHorizon runs a small server on
  your own computer and your browser talks to it; nothing leaves your machine
  except the data fetches listed under Privacy & connections.
- **Compact is now as dense as Money.** With a mouse, Compact draws each
  transaction and each account on a single line, about 25 pixels high instead
  of 33 to 47. The bank's name follows the account's name, a transaction's
  Attach, Edit and Delete buttons appear when the pointer is on its row, and
  anything cut short shows in full when you hover over it. Comfortable is
  unchanged, and touch screens keep larger rows.

---

## B1362

*25 November 2026*

- **Windows:** `WealthHorizon-Setup-B1362.exe` on the
  [B1362 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1362).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1362`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **The all releases link on What's new can be read in every skin.** It kept
  the browser's own dark blue, which all but vanished on the dark skin and on
  the Money 2005 skin's blue title band. It now takes the heading's text
  colour, underlined.
- **Dropping a file onto an import box reads it.** The Import, Import
  transactions, Import accounts and balance-history boxes said "Drop a file"
  but had nothing to catch one, so the browser offered to save or open the
  file instead. A file dropped anywhere else in the app is now ignored rather
  than opened by the browser.
- **Currency pairs switched on are kept up to date, crypto included.** Most
  pairs (BTC/USD, ETH/USD, XRP/USD, EUR/USD and others) are listed switched
  off, and switching one on, or adding it, left its automatic updates off, so
  it was never fetched. Switching a pair on now turns its updates on, and
  pairs already switched on are mended.
- **A currency pair can be removed from FX Rates.** The bin beside a pair's
  On/Off button takes it off the list; its stored rates are kept and adding it
  again brings it back.
- **Sorted oldest first, the register says which way it pages.** It loads 500
  entries at a time, and the button at the bottom said "Load older
  transactions" even when it would load newer ones. It now says older or newer
  by the sort order, the line under the balance says latest or earliest, and
  **Show all** loads the rest in one go.
- **Closed accounts in a Money file can be imported.** They could not be
  ticked at all. Every account is now ticked, closed ones included, and a
  closed account comes in closed, with all its history, hidden from the list
  until Show inactive. The file's warnings are listed once, one to a line,
  instead of a run-on banner repeated on the done screen.
- **A new account from an import starts in your household's currency.** An
  account a file names no currency for, and a new account made from Import
  accounts, started in pounds; they now start in the household's own currency
  (dollars in the United States).
- **"Checking" wherever a US household sees an account type.** The search box,
  the Import dialog's account picker, an institution's accounts, the stocks
  list and the balance-history import still said "Current".

Added or enhanced:

- **Release notes on every release.** Each release on the downloads page now
  carries **release-notes.html**: every release down the left, and for the one
  you pick, what it fixed, then what it added or enhanced. The same two lists
  are in the release's own description on the page.
- **Household licences cover a number of people, and have no public sign-up.**
  A Standard licence covers 4 people who sign in and a Pro licence 8; children
  under 16 are not counted. The Licence card says how many are counted, and at
  the limit Add user, inviting another adult and reactivating somebody are
  refused with the reason. Nobody already in is ever locked out. Public
  sign-up is for the Adviser and Firm editions: on a household licence the
  switch stays off, and somebody invited can still create their account. An
  install that needs no licence is unchanged.
- **One household per household licence; named seats for Adviser and Firm.** A
  household licence covers one household, counted once it has accounts. The
  Adviser and Firm editions are licensed per named seat (every adviser with a
  client, manager, compliance manager and administrator, signed in or not):
  Adviser starts at 2 seats and 50 client households, Firm at 10 seats and
  250. Clients are not seats. The Licence card shows both, and the step that
  needs another seat or household is refused with the reason. A backup restore
  is never limited, and an install that needs no licence is unchanged.
- **One licence key, one installation.** A MUN1 installation sends a random
  installation id (and nothing else about itself) with its daily check, and
  the Licence card warns when the licence server has seen the key on another
  installation too. Nothing stops; Move this licence releases the
  installation.
- **A subscription buys updates; the version you have keeps working.** A
  licence's end date is now the end of its updates. A version released before
  then keeps working after it, for good, and the Licence card says updates
  have ended; a version released later is read-only until the licence is
  renewed, and says so. Each customer build carries its release day.
- **Licensed to.** Where the licence names its owner, "Licensed to …" shows
  under the logo and at the foot of the plan report (workbook and print). It
  is the name from the purchase, never an email address.
- **Standard and Pro differ in features.** Pro adds AI assistance, bank and
  broker feeds (Open Banking, SimpleFIN, Trading 212), the plan report, and
  more than three scenarios a plan; the Adviser and Firm editions have them
  all. On Standard each says where it lives that it is part of Pro, and the
  server refuses it with the reason. A feed connected before can still be
  looked at and disconnected. The evaluation is Standard. An install that
  needs no licence is unchanged.
- **Future-dated entries are shaded light grey in the register.** Each entry
  dated after today, the ones the balance leaves out until their date, has a
  light grey background, so they stand apart whichever way the register is
  sorted, newest first included. Every skin has its own grey: light, dark and
  Money 2005.
- **The release notes page has a theme picker.** In its title bar choose
  **System**, which follows your device's light or dark setting, **Light**,
  **Dark** or **Money 2005**, the same as the app's skins. The page remembers
  your choice next time you open it.
- **Compact rows.** Profile → Text size and row spacing has Row spacing:
  Comfortable or Compact. Compact fits more accounts and transactions on the
  screen, as Money does. Money 2005 starts compact until you choose.
- **Create a category as you categorise.** Typing a name no category has into
  a transaction's Category now offers "Create category: …" first, and the
  field says it is created when you save. (Typing a new name always created
  it; nothing said so.)
- **Credit cards have their own section on the Accounts page**, apart from the
  mortgage and the loans, which are now under Loans and liabilities.
- **The A/C button is gone for now.** The All accounts / UK / Ireland / US /
  Jersey button beside the search stored a choice that no page used, so it
  changed nothing. It comes back when pages filter by it.
- **US spelling for a US household.** A household in the United States now
  reads Favorites, license, color, organize, catalog, center and the rest in
  the menus, the page titles and every page's help; every other household, the
  UK and its Crown Dependencies included, keeps UK spelling. On the account
  form the Tax wrapper field reads Tax treatment in the US.
- **No GIA for a US account.** A US brokerage account no longer offers "No
  wrapper / GIA" beside "Taxable brokerage account", which was the same choice
  twice (and GIA, to an American, is the Gemological Institute of America).
  The badge on a US account's taxable account reads Taxable rather than GIA,
  on the account list, the account page, the account cards and in search.

---

## B1339

*25 November 2026*

- **Windows:** `WealthHorizon-Setup-B1339.exe` on the
  [B1339 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1339).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1339`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Checking, not Current, everywhere in a US household.** Each account's type
  already read Checking, but the Accounts page still filed them under a
  "Current" section, as did the account directory report and a forecast's
  workings, and the account-type picker in Import from another program showed
  the raw code (CURRENT). All now follow the household's country: Checking in
  the United States, Current elsewhere.
- **Risk and return, and Check my chances, show wealth in today's money.** The
  simulated wealth at the end of a plan was in pounds of its last year without
  saying so: £26m forty years out buys about what £12m does now. Both now show
  today's money and name the year, and Risk and return says what a chance of
  success measures. The simulation returns both figures.

Added or enhanced:

- **How is this worked out?** A link beside net worth (Home and Net Worth),
  the amount at the end of a plan (My forecast), a goal's shortfall and the
  gap from the plan (Roadmap), the risk pyramid and its tiers, and an
  account's closing balance (Month picture). It opens the figure's breakdown,
  adding up, with what it rests on, what moves it most and any warning. The
  plan's drivers are measured by running the plan again. No AI is involved.
- **Ask why.** Ask about a figure on any page, from the ✦ button in the top
  bar or from Help: "I don't understand why there is a £726k shortfall". The
  figure is found by its amount (you pick if several fit); the model that
  answers you, where AI is switched on, explains it from WealthHorizon's own
  breakdown, and every amount in the answer is checked against it. With AI
  off, or an answer that does not match, the breakdown is shown instead. The
  administrator switches it on under System → AI Assistance → Features.
- **What's new links to every release.** Under the build line, **all
  releases** opens the public releases page: each build with its notes and
  downloads (Docker images, Windows installer, QNAP zip). When a newer build
  exists, the line says to download it from there as well as the ops menu,
  which a household without the System Admin menu does not have.
- **Planning keeps its landing page.** The journey cards stay Planning's front
  page after a plan exists, led by a Continue your plan card (journey, answers
  so far, last saved, progress to financial independence) with shortcuts to
  Results, Roadmap and Goals. The current journey is marked Your plan;
  Planning home inside the plan returns to it. Picking another journey keeps
  your answers.
- **The Risk Pyramid is drawn as a solid pyramid.** Each tier is a 3D slab
  with a shaded side and a lit top, riskiest at the top, as wide on average as
  the money in it. The slabs lean like a pyramid, or the other way up when the
  shape is inverted, and an empty tier is a gap. The share and amount stand
  beside each slab, on two lines that fit a phone.
- **Bank Connections, in Tools.** Connecting banks and brokers (UK Open
  Banking, SimpleFIN for US banks and brokers, broker links) is one page,
  **Tools → Bank Connections**, renamed from System → Connections. The Open
  Finance Hub, the operator's Open Finance readiness page, moved from Tools to
  System and is shown to a system administrator only; an old link to it takes
  anyone else to Bank Connections.
- **A SimpleFIN sync matches payments entered ahead of the bank.** A synced
  row that can be exactly one entry already in the account (same amount,
  within five days, not reconciled) is merged into it, keeping its payee and
  category; it used to be added beside it. A row that could be two entries is
  added and listed in **Needs attention** as **Duplicate?**, where **Yes**
  merges it. The sync summary counts the rows merged.

---

## B1319

*24 November 2026*

- **Windows:** `WealthHorizon-Setup-B1319.exe` on the
  [B1319 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1319).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1319`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Deleting an account that something points at.** Deleting an account that a
  credit card is paid from (or that a scheduled transfer or a split line
  names) was refused with a database message: "violates foreign key constraint
  card_terms_payment_account_id_fkey". Now the card is kept and forgets its
  payment account, a scheduled transfer into the deleted account is removed
  with it (as one out of it already was), and a split line keeps its amount.

Added or enhanced:

- **Find duplicates** (Accounts → ⋯, or an account's own ⋯ menu). Lists every
  row an import added beside an entry you had already made (the same amount,
  within five days), your entry beside the copy, each pair ticked. Untick any
  that are really two payments, then **Merge N selected**: your entry keeps
  its payee, category and memo, takes the bank's date and is marked cleared,
  and the copy is removed. The next import still recognises the bank's row.
  For tidying up imports made before matching existed, without deleting
  accounts.
- **Recently deleted** (Accounts → ⋯). Deleting a transaction, a selection, an
  account's transactions or whole accounts no longer loses them at once: each
  delete is kept, and **Restore** puts back everything it removed, as it was,
  with the links to what stayed (a card's payment account, the other side of a
  transfer). **Keep deleted items for** is the household's choice: not at all,
  7, 30 (the default) or 90 days, a year, or until removed. The delete
  confirmations now say where to restore from instead of "This cannot be
  undone".

---

## B1313

*24 November 2026*

- **Windows:** `WealthHorizon-Setup-B1313.exe` on the
  [B1313 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1313).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1313`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Monte Carlo: a scenario that sets growth keeps its range of outcomes.** A
  scenario with a growth override — Bear Market, Bull Run, Stagflation — was
  simulated at that rate with no volatility, so its 10th, 50th and 90th
  percentile final wealth were one figure and, in the demo data, every such
  scenario showed a 100% chance of success. The override now replaces the mean
  of every asset class's return, as it replaces every pot's rate in the
  forecast, and each class keeps its own volatility from the Monte Carlo
  assumptions. This applies to plans with no spending target; plans with one
  already worked this way. Portfolio → Risk Pyramid no longer prints "This
  scenario fixes the growth rate, so it has no spread to show".
- **Importing from another program matches the entries you already made.** A
  My Financial Picture export (or Monarch, YNAB, Quicken and the rest)
  imported onto an account you keep by hand used to put every row in beside
  the entry you had made, so a card payment typed ahead of the statement
  appeared twice. Now, before anything is written, **From another program**
  lists each row that is the same amount as one of your entries within five
  days, your entry beside the bank's row, with **Merge** (the default) or
  **Keep separate**, and **Merge all** / **Keep all separate**. A merge keeps
  your payee, category and memo, takes the bank's date and marks it cleared,
  as the single-account import already did. Rows already imported are still
  skipped as duplicates. **Import accounts** now recognises such a file and
  hands it to this importer, instead of reading it as a generic multi-account
  CSV (which matched nothing, read the dates day first and dropped the payee).

Added or enhanced:

- **Needs attention: a Yes button** (a tester's ask). A *Transfer?* or a
  payment *to confirm* is answered in the list in one click: Yes pairs the two
  rows as one transfer, or links the payment to its recurring item, the same
  as on Accounts and Recurring.
- **Risk Pyramid** (Portfolio → Risk Pyramid). Your money drawn as a pyramid:
  Foundation, Security, Growth and Speculative tiers, each holding placed by
  its published risk rating or by what kind of holding it is, with the reason
  shown and guesses marked Estimated. The shape is named (pyramid, oblong,
  diamond, inverted or uneven), the foundation is measured in months of your
  spending against a target you set, and guaranteed income is drawn as a
  floor. Move a holding to another tier with a reason, include your home or
  not, and set each plan scenario's chance of success and range of outcomes
  beside the pyramid. No AI is involved.
- **AI Assistance** (System → AI Assistance), phase 0. Connect a language
  model of your choice at three levels: the installation (system
  administrator), the household (its owner) and each person. Ollama is the
  first provider; others follow on the same connection. The administrator sets
  the rules: AI on or off, which connections may exist, which networks a model
  may be on, how much data it may receive, and monthly limits. Keys are sealed
  with `WH_CREDENTIAL_KEY` and never shown again. **Test connection** sends
  one fixed sentence with no personal data. Every save, test and call is
  audited. AI is off by default and no feature uses it yet.
- **Plainer words, and prices from where you are** (a US tester's points). The
  Accounts column *Juris.* is now **Country**, and the Home net worth panel
  says "every country and currency" rather than "multi-jurisdiction". Home's
  panel is **Most recent transactions** and stops at today, so pre-entered
  future rows no longer sit at the top. An investment account's **Holdings**
  card has **Update prices** for its own instruments, so you don't have to go
  to the Prices page.

---

## B1289

*23 November 2026*

- **Windows:** `WealthHorizon-Setup-B1289.exe` on the
  [B1289 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1289).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1289`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **A fetched exchange rate is checked before it is stored.** The automatic
  refresh stored GBP→USD at 46,927.04 against about 1.31 the day before, and
  every dollar holding was converted at it: nothing compared what a source
  sent back with anything. A rate more than half as much again as the middle
  of the pair's last five, or less than two thirds of it (three times either
  way for crypto), is now refused, the second source is asked, and if neither
  agrees the pair is reported with both figures and nothing is written.
  Stooq's close is read by its column's name rather than its position, and a
  row for another symbol is not read as this pair's.
- **Accounts: the Updated date follows your date setting.** It was the one
  date still written dd/mm/yy; a US household now sees mm/dd/yy, and the
  tooltip the same way round.
- **No more "�" in an account's mark.** A name starting with an emoji (🚙, 💳)
  had the emoji cut in half for its initials; symbols are now skipped, and a
  character is never split.

Added or enhanced:

- **The mark beside an account with no bank recorded shows its type** (a
  tester's question: "is there any means of determining account type, rather
  than just depending on name?"): a card, a car, a house, a loan, a building,
  a chart, a savings pot or a box, instead of letters cut from its name.

---

## B1285

*23 November 2026*

- **Windows:** `WealthHorizon-Setup-B1285.exe` on the
  [B1285 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1285).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1285`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Added or enhanced:

- **Month-end plan: coming in and going out.** The plan now opens with the
  month as a plain list: income, bills (direct debits and standing orders),
  what each credit card needs paying (the Credit Card Debt report's Payment
  due, on its payment day, from the paying account), and transfers between
  your accounts, by date, with totals and what arrives in and leaves each
  account. Nothing is counted twice: a recurring payment to a card that
  already has its statement payment, and a bill charged to a card, are listed
  greyed and not added in.
- **Add the regular payments your history shows, in one click.** The Month-end
  plan's list says how many regular payments are not set up yet; **Show them**
  opens them there, and **Add all** (also on Recurring) adds every one, each
  as its own Add would. A standing order to another of your accounts is now
  offered as a transfer to that account, and a payment to a credit card is not
  offered, because the card's statement payment already covers it.

---

## B1281

*23 November 2026*

- **Windows:** `WealthHorizon-Setup-B1281.exe` on the
  [B1281 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1281).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1281`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Prices: the auto-refresh interval shows in full.** The "Every … min" box
  had room for one digit, so 220 minutes read as "22". It is now wide enough
  for four, on a computer and on a phone.

Added or enhanced:

- **Needs attention** (smart reconciliation, phase 3). One list of everything
  across every account that needs you, with a count on Home: a balance that no
  longer agrees with the bank, and the last day it did, so only the rows since
  need checking; a statement started and not finished; a recurring item late
  or at a different amount; a payment or a transfer to confirm; and check
  numbers missing recently. Each item has one button to where it is put right,
  and a Dismiss that asks for the reason. A dismissed balance comes back when
  the bank reports a new figure.
- **Growth & income, after a tester's first run.** Look back opens with a live
  example (GOOGL, a year ago, 10,000) that runs as it stands, rather than a
  greyed hint taken for a value already there; "Yield growth" is now "Yield
  change a year", which is what it is; the Holding column is left-aligned.
- **Row highlight you can follow** (a tester's suggestion). The row under the
  pointer now stands out the way it does in Money and Outlook, in every skin,
  and every table has it, including the Advanced Planner's (Growth & income,
  the drawdown plan and options, the growth breakdown, tax checks), which had
  none. One setting (`--wh-row-hover` in each skin) drives every table.
- **Import accounts, as a button.** The Accounts page has an **Import
  accounts** button under its description, naming the files it takes (CSV,
  OFX, TXT, QIF, QFX, PDF), instead of the import being two levels into the ⋯
  menu. It is still in the menu, which now names the same formats.

---

## B1273

*23 November 2026*

- **Windows:** `WealthHorizon-Setup-B1273.exe` on the
  [B1273 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1273).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1273`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Fund distributions Money shows as "Unknown" are dividends.** A Money
  activity the import has no name for (a tester's NEOS fund distributions)
  came in as other income. Where the row's memo or category says dividend or
  distribution ("CASH DIV ON 1250 SHS"), it is now a dividend: in the Dividend
  Tracker, for dividend tax, and in Stocks & Shares income. Rows imported
  before this are updated on upgrade; no re-import needed.

Added or enhanced:

- **Growth & income** (Advanced Planner). A holding's price and what it pays,
  side by side. **Look back**: a ticker, a start date and an amount, on the
  fund's real prices and distributions, comparing reinvesting all, none or a
  share you pick, with current yield, yield on cost, price change a year and
  income vs decay. **Look forward**: every holding at its own yield to start;
  change the yield, its growth, how much is reinvested and the price growth
  beyond your Stock price forecast, and see each holding and the portfolio
  year by year. Your assumptions, not advice; tax not deducted.

---

## B1269

*22 November 2026*

- **Windows:** `WealthHorizon-Setup-B1269.exe` on the
  [B1269 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1269).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1269`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **The Stocks & Shares chart drew a holding at $0 until its first price.** A
  day with no price now uses the price paid.

Added or enhanced:

- **Expected items** (smart reconciliation, phase 2). A downloaded payment
  that matches a recurring item exactly is linked to it as it is imported, and
  the import result says how many were. The forecast no longer counts a linked
  occurrence a second time, even when the bill went out a day or two early.
  The Recurring page has a new **Expected items** card, shown only when
  something needs you: a suggested link to confirm or turn down, a payment
  more than three days late (skip it this time), and one that arrived at a
  different amount (unlink it if wrong). Every link is recorded with its
  reason.
- **Transfers between your accounts, found for you** (smart reconciliation,
  phase 2). Money moved between two of your accounts arrives from the two
  banks as two unrelated rows, and both counted as spending and income. The
  Accounts page now lists pairs that look like one transfer (same amount, one
  out and one in, within five days; within 1% at the day's rates across two
  currencies), each with its reason. **Link as one transfer** ties them, with
  an Undo; **Not a transfer** is remembered. Nothing is linked without a
  click.
- **Income counts in investment performance.** Stocks & Shares shows what each
  holding has paid (dividends, reinvested dividends, other income), its yield
  on today's value and on cost, and a **Total return** beside the price gain:
  price change plus income plus anything realised. New **Total return** and
  **Income, 12 months** figures lead the page. A high-income fund down on
  price now shows what it has really made.
- **Profit this year / 1 year** on Stocks & Shares is measured on the holdings
  (value, purchases, sales and income), not on how the cash legs were
  labelled. A Money file that labelled the purchase money twice showed −50% on
  funds 9% below cost.

---

## B1261

*22 November 2026*

- **Windows:** `WealthHorizon-Setup-B1261.exe` on the
  [B1261 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1261).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1261`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Added or enhanced:

- **Statements balanced, with a record of each.** The Balance dialog lists an
  account's past statements; each downloads as a CSV or prints (or saves as
  PDF) with its balances, whether it was forced, who closed it, and every
  transaction it reconciled with who ticked it: the bank's download, you, or
  the adjustment.

---

## B1259

*22 November 2026*

- **Windows:** `WealthHorizon-Setup-B1259.exe` on the
  [B1259 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1259).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1259`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Added or enhanced:

- **Balance an account from your bank's download** (smart reconciliation,
  phase 1). An OFX download's closing balance and date are now kept, as a
  SimpleFIN sync's already were. Balance this account fills the statement in
  from them, ticks every row the bank sent up to the statement date as soon as
  the session starts, and lists only what is left: the rows the bank has not
  shown. Most months that is nothing, and balancing is one click on Finish,
  which is never pressed for you. Each automatic tick is recorded with its
  rule; **Tick what the bank sent** repeats it on a resumed session.

---

## B1257

*22 November 2026*

- **Windows:** `WealthHorizon-Setup-B1257.exe` on the
  [B1257 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1257).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1257`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Prices no longer says the provider "could not be reached" after fetching
  fifty-three prices from it.** Any provider error in any round of a refresh
  raised the red banner, and the instrument that had met it was left off the
  list, so the one thing worth retrying could not be found. The banner now
  means what it says, nothing priced at all; when others priced, the
  instruments the provider did not answer for are listed with the provider's
  reason and a note to try them again.

Added or enhanced:

- **Missing Checks report.** Under Income and Expenses: for each account with
  check numbers, the range used, the numbers missing between the first and the
  last, numbers used twice, and how many were voided (a voided check counts as
  used). EFT, ATM and the like are not check numbers; a gap of more than 200
  is shown as a new checkbook rather than counted. A Money user voids spoiled
  checks "so there is no check number gap"; this is what finds the gaps.

---

## B1253

*22 November 2026*

- **Windows:** `WealthHorizon-Setup-B1253.exe` on the
  [B1253 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1253).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1253`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **A dividend dated ahead counted twice in "still to come".** On an
  investment account with its own cash register, Money's dividend sits in the
  investment register and its cash in the (Cash) account, tied as one
  movement. The "still to come" note added both sides, so two dividends of
  $2,076.17 read "$4,152.34 still to come in 4 entries". The cash row is the
  money; the investment-register row tied to it is no longer counted again.
- **Money's voids came across as reconciled and counted.** Money keeps a void
  in a flag bit, not in the cleared state: a row reconciled and then voided
  still reads R, and Money shows both marks with the void prevailing. The
  engine read the cleared state alone, so every such row arrived as R and in
  the balance (engine 0.6.4 reads the flag; a voided row is V here and counts
  towards nothing, whatever mark it also carried). Start again and re-import
  the file to pick it up.

---

## B1251

*21 November 2026*

- **Windows:** `WealthHorizon-Setup-B1251.exe` on the
  [B1251 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1251).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1251`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Behind-the-scenes changes only; nothing you will notice.

---

## B1249

*21 November 2026*

- **Windows:** `WealthHorizon-Setup-B1249.exe` on the
  [B1249 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1249).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1249`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Added or enhanced:

- **Prices come across from Money, and an instruments step after the import.**
  Money's last price for each holding is written with the import, dated as
  Money dates it, so an investment account is worth something the moment the
  import finishes instead of reading as cash alone. The done screen then says
  how many instruments came across, how many Money's prices covered, and names
  the rest, with **Check tickers and fetch prices** to ask the price provider
  for each and report what it found, and a pointer to the Prices page for a
  ticker to set or a price file to import by ISIN or SEDOL.

---

## B1247

*21 November 2026*

- **Windows:** `WealthHorizon-Setup-B1247.exe` on the
  [B1247 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1247).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1247`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Added or enhanced:

- **No running balance on the Investments view.** The trades' cash legs summed
  are a cost flow, not a balance ("−200,000 for investments seems weird"), and
  Money's investment register has none. The Cash view keeps it.
- **Performance panel while holdings are unpriced.** With no stored price on
  any holding the value, gain and returns are withheld rather than shown as
  the cash alone (which read as a 99% loss on a new account); with some
  unpriced they are shown and marked as short. Paid in and cost stay.

---

## B1245

*21 November 2026*

- **Windows:** `WealthHorizon-Setup-B1245.exe` on the
  [B1245 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1245).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1245`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Added or enhanced:

- **Money's C column in the register.** Blank, C (cleared), R (reconciled) or
  V (void) on every row, in the cash and investment registers and on the
  phone; click to tick a row cleared or untick it, R and V are settled
  elsewhere. A Money user asked to see the flag.

---

## B1243

*21 November 2026*

- **Windows:** `WealthHorizon-Setup-B1243.exe` on the
  [B1243 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1243).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1243`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Added or enhanced:

- **Start again accepts RESET in any case.** A tester typed "reset" and the
  button stayed grey; the word is now matched whatever the case and sent to
  the server in capitals.
- **Void a transaction.** Money's *Mark as → Void*, under **More** on the edit
  form: the row stays in the register, marked **Void** and struck through, and
  counts towards no balance. Unlike deleting it, voiding keeps the row's
  import fingerprint, so the next import of the same file reports it as a
  duplicate instead of entering it again. Both legs of a transfer go together;
  **Restore (not void)** counts it again; a reconciled row is refused. A
  tester whose Money voids had come in as ordinary rows asked for it.

---

## B1241

*20 November 2026*

- **Windows:** `WealthHorizon-Setup-B1241.exe` on the
  [B1241 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1241).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1241`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **"Coming up" on the front page no longer breaks a renewal's name a syllable
  to a line on a phone.** The name sat beside a subtitle that would not wrap,
  so the subtitle took the width and the name was left a sliver, nineteen
  lines tall. The name has the row to itself and the subtitle sits beneath it,
  as the Renewals page already lays them out.

Added or enhanced:

- **US banks and brokers through SimpleFIN**. System → Connections → SimpleFIN
  → Connect with a setup token. You sign in to your banks, cards and brokers
  at the SimpleFIN Bridge (bridge.simplefin.org, a few dollars a year), never
  in WealthHorizon, and paste the one-time token it gives you. WealthHorizon
  exchanges it for a read-only access it keeps sealed and never shows, lists
  every account you connected, and lets you link each to an account here or
  create one for it. Sync brings balances and transactions across for all of
  them in one request (the last 90 days, overlapping the previous sync so
  nothing posted late is missed; pending rows left out); Fetch earlier history
  goes back a window at a time; a nightly sync keeps them current and stops
  after three failures. Revoking the access at the bridge is honoured: the
  card asks for a new token.
- **State income tax for every state, and a move mid-year.** The planner now
  knows all fifty states and the District of Columbia, each with its
  deduction, brackets, Social Security rule and retirement exclusion and a
  note of what it leaves out. Beside the state on My forecast, **State applies
  from** takes the date you moved or will: that year is charged the state's
  tax for the share of the year from the date, earlier years none.
- **State estate taxes on the Estate tab.** Where the plan's state has an
  estate tax of its own — Illinois from $4 million, Oregon from $1 million,
  Massachusetts from $2 million, Washington and Minnesota from $3 million, New
  York from $7.35 million, among a dozen — the Estate tab adds a column for
  it, taken from what passes, with Illinois's whole-estate cliff and New
  York's 105% cliff worked the way the states do.
- **The US return's lines, and the US tax categories in one go.** A category
  can now carry the retirement, investment, withholding and adjustment lines
  of a US return as well as Schedule A's: taxable IRA distributions, Roth and
  qualified charitable distributions, pensions, Social Security, tax-exempt
  interest, Treasury interest (Schedule B, state-exempt), qualified and
  ordinary dividends, capital gain distributions, return of capital, accrued
  interest, early-withdrawal penalties, HSA, federal and state tax withheld
  and estimated. **Add the US tax categories** on the Categories page creates
  thirty categories already on their lines and keeps any you have; the
  suggestions read Money's own names. State tax withheld counts as a SALT
  deduction in the standard-or-itemise comparison. The user guide gains a
  chapter, "Coming from Money: recording the awkward ones", with a how-to for
  each of the practices Money users built by hand: Treasury bills, savings
  bonds, brokered CDs and accrued interest, RMDs and QCDs, Roth conversions,
  dividends on the right lines, return of capital, splits and spin-offs,
  options, money market earnings, tax categories, retirement income, alerts.

---

## B1233

*19 November 2026*

- **Windows:** `WealthHorizon-Setup-B1233.exe` on the
  [B1233 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1233).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1233`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **The account balance reports group as the Accounts page does.** Account
  Balances and Account Balances with Details grouped by the type's broad
  category, which filed pensions under Investments and every current and
  savings account together. They now use the page's sections — Current,
  Savings, Investments, Pensions, Property & assets, Liabilities — with a
  pension under Pensions whatever type it was set up as.
- **On an iPad, a long report printed the screen.** The print sheet was taken
  down a second after printing was asked for, which is fine on a desktop,
  where the print dialog blocks, but iPad Safari builds its preview in the
  background and *Account Balances with Details* took longer than a second, so
  the preview caught the page. The sheet now stays until the browser says
  printing is over.
- **Outbound and output.** SMTP certificates verified; e-mail templates
  HTML-escaped; CSV cells that would start a formula prefixed with `'`; logo
  fetches connect only to the address that was checked (DNS rebinding); relay
  URL must be `https://`; renewal and directory links only for web addresses;
  JSON bodies capped at 1 MB except imports; the brand font is bundled, so the
  browser no longer contacts Google; the vulnerability-score widget is opt-in.
- **QIF and OFX files can be chosen on an iPad.** iPadOS files a `.qif` or an
  `.ofx` as plain "data" and greys out anything a file picker does not name by
  type, so a bank's QIF or OFX download could not be selected while the CSV
  beside it could. The transaction and Money-file pickers no longer carry an
  accept list: every file is offered, the caption says which formats are read,
  and the wizard says what the file is or that it cannot read it.
- **A Money Home & Business file's receivables and sales tax import as what
  they are.** The two account kinds that edition adds had no entry in the
  table that reads Money's account-type code, so both fell to the default and
  arrived as savings accounts. Accounts Receivable is now an asset and Sales
  Tax a loan. Settled against the sample file that ships with Money Plus Home
  & Business, which reads in full: 28 accounts, 2,039 transactions, 17
  holdings.
- **"Are you tracking to plan?" compared today's money with the plan's
  year-end figure, and a plan that started in the past grew today's balances
  for the years already gone.** The projection seeds its first year with what
  the accounts and pensions are worth today, so a plan starting in 2020
  reached "2026" with six years of growth and contributions stacked on today's
  money, and the Roadmap reported a £3.0M household £2.3M behind a £5.3M plan.
  Years already gone are no longer projected: the projection begins at this
  year, says so above the comparison, and a new or changed start year in the
  past is refused. The comparison is now against this year's opening plus the
  part of the year gone, and the Roadmap says what the plan opened the year
  at, so a gap reads as a difference in what is counted rather than a verdict.
- **A fresh install no longer stops on its first screen with
  "LICENCE_REQUIRED".** A public install is read-only until a licence key is
  entered, and the first-run wizard's save of your date of birth was refused,
  showing the bare code with no way forward. The wizard now asks the System
  Administrator for the key first, in words (**Activate**, or **I'll do this
  later**), and its own questions are saved either way. A change refused for
  want of a key now says so in a sentence everywhere, not as a code.
- **A password-protected MS Money file now asks for its password.** Importing
  a locked .mny showed an error and no box to type the password into, so the
  file could not be imported at all. The server answered a locked file as if
  the sign-in had expired, and the upload lost the server's reason on the way
  back. Now the import asks for the password, and says so if it's wrong.
- **A password-protected MS Money file really does ask for its password now.**
  The earlier fix (below) was needed but not enough: the Money engine wraps
  its "needs a password" error in its own, so WealthHorizon still read a
  locked file as an unreadable one and showed "This Microsoft Money file is
  password-protected. Enter the password…" with nowhere to enter it. The
  password error is now found inside the wrapping, and the tests lock a Money
  file and send it through the real engine.
- **"Show inactive" can be seen in the Money 2005 look.** On Accounts the
  switch sat on the navy title banner in dark grey and was all but invisible.
  It is now light on the navy, and a white track with a navy thumb when on.
- **Everything on Money 2005's blue banner can be read.** An account page's
  name, its back arrow and its subtitle were dark grey on the navy banner and
  all but invisible; on an investment account **Transfer cash** was white on
  white; and the subtitles on Planner, Planning, Profile and Renewals were
  dark on navy too. The banner now draws its controls light on dark, as dark
  mode does, and the white panels on it keep their usual colours. A browser
  test measures every word and icon on the banner across eight pages.
- **An OFX file with several accounts is no longer read as one.** The
  transaction import (and Smart Import) put every statement in a combined OFX
  file, as PocketSense writes them, into the one account chosen, so a savings
  account's interest landed in checking. Such a file is now refused with the
  accounts named, and pointed to **Import from MS Money**, which reads each
  account separately and now says it takes OFX.
- **A long account name is shown in full at the top of its page.** The name is
  a button (it opens the account switcher), and the title row held every
  button in it to one height so the controls line up; a name long enough to
  wrap lost its second line. Sooner in Money 2005, whose Tahoma is wider, but
  in every skin.
- **Money 2005's text is no longer larger than the other looks'.** Money is
  set in Tahoma at the same sizes as light and dark, and Tahoma is the bigger
  face (its x-height is about 9% taller), so a tester found it too large. With
  a mouse it now draws itself at 92%; on a touch screen it stays full size so
  its controls stay large enough to tap.
- **The top menu bar clipped its last groups, and the side rail's foot took a
  third of the rail.** The menu strip was never allowed to be narrower than
  its menus (a flex item's minimum width is its content), so it overflowed the
  bar instead of itself, was clipped there, and the scroll arrows, which read
  the strip's own overflow, never appeared: "Tools" was cut to "Too" under the
  build number and System could not be reached. And the arrows had a second
  reason to stay away: their hook attached its listeners once, on first
  render, when the bar did not exist yet (the shell draws it once the session
  has loaded), so nothing was ever watching the strip. The strip now shrinks
  and scrolls, the hook follows the element, and a change to what the strip
  holds measures again. The four navigation-position chevrons in the bar are
  one small menu. In the side rail the "Nav Position" section, the two-line
  user tile with its Exit chip, the Dark mode row and the build stamp are one
  row: avatar, name, then the look, the navigation position and Exit as icons,
  with the role and build beneath — 70 pixels where there were about 170.
- **Re-importing a Money file now brings in investment memos.** The memo was
  stored only alongside a NEW transaction, so a file whose transactions were
  all already in the household (the re-import a tester was told to do) stored
  none. It is now stored for every row that names the investment, a duplicate
  included.
- **A re-import no longer says "Nothing was imported".** Importing onto the
  accounts already there creates no account, and the result screen read that
  as nothing at all. It now says what came in ("25 transactions imported into
  3 existing accounts", "9 investment memos updated") or that the household is
  already up to date.
- **One list of pension wrappers.** Four hand-kept lists said which wrappers
  are retirement money and disagreed: Portugal's PPR was in none, and a Jersey
  pension on a non-pension account type was a pension on some pages and an
  investment on others. They are one list now, checked by a test against every
  pension wrapper in the database, and the screen's copy against the server's.
- **A voided Money transaction counted towards its account's balance**.
  Money's V had no mapping, so the row arrived uncleared and counted. It is
  now imported as void and, as in Money, excluded from every balance; the row
  is kept.
- **Money investment accounts imported wrongly**. From a US tester's file: a
  purchase arrived as a deposit, every dividend as a withdrawal, a sale as a
  purchase, and each dividend cancelled against its own cash, so no income
  showed. Money's own action codes now say what each row is; the investment
  row is written the way a trade entered here is and tied to its cash row, so
  a dividend counts once, in the Dividend Tracker; and shares added, removed,
  transferred, granted or expired move the holding. On the sample every
  position now matches Money (none did). A file imported before is still
  recognised; use Start again to re-import it with the fix.
- **Quicken QIF files.** Dates written the Quicken way (`1/ 5'26`) were not
  read; a whole-file export brought each account in twice and turned its
  category and security lists into transactions; and the accounts came in as
  pounds. Now each account comes in once, the lists are skipped, the
  household's currency is used, and a check's number is kept.
- **US card statements as PDF.** The PDF statement reader knew only pounds and
  day-first dates. It now reads dollar amounts, the short month-first date a
  US statement prints on each line (11/09, its year from the closing date),
  and "Previous Balance" / "New Balance", so the lines still check against the
  statement's own totals.
- **US dates in any file.** A date that could be either way round (03/04/2026)
  was read day first everywhere. It is now read the household's way: month
  first in the US. A date that can only be one way is read that way.
- **The import from another program** started each account on Britain and
  pounds; it starts on the household's own country and currency.
- **A Money investment activity the import had no name for** (a tester's
  monthly ETF distributions) arrived as "Unknown" with its cash deposit shown
  beside it. Such a row, which moves money but no units, now comes in as
  income or expense by its sign, tied to its cash like a dividend, and the
  import says which Money code it met and one example row, so the activity can
  be named from a real file.

Added or enhanced:

- **Reports print as a document, not a screenshot.** *Export → Print, or save
  as PDF* on a report now prints a sheet of its own: the title and what it
  answers, *Prepared for* your name, the dates it is true for, when it was
  printed and the currency, the report's summary line, and the table set for
  A4 with the headings on every page, rows gathered under their group, figures
  right-aligned and a column with nothing in it left off (a foot-note says
  which). Nothing of the app prints. Built from the same rows the CSV and
  Excel exports are.
- **Account Balances is a report, the summary.** It pointed at the Accounts
  page. It now draws every open account with its institution, type, currency
  and balance, grouped with a subtotal per group and the total at the foot,
  and prints in portrait; *Account Balances with Details* is the same rows
  with every column.
- **An account's controls are one corner, and Select starts from the
  register.** The search box and the account filter sat on the name's line and
  the action tiles on the balance's, as two rows that happened to be near each
  other — 2px apart, their right-hand edges out of line — with a "Select"
  button on the search line for the table two rows below it. The corner is one
  block at the right: the tiles, then the search and the filter, flush right
  and 8px apart; with room they share the name's line. Select is now the small
  list-with-ticks button at the left of the register's heading row, where the
  checkbox goes once you are selecting, so nothing moves when you press it.
- **An institution catalogue for the UK, the US and Ireland, with logos
  fetched for the lot.** Financial Institutions now ships more than three
  hundred institutions across the three countries — high-street and challenger
  banks, building societies, card issuers, savings banks, brokers and
  platforms, fund houses, credit unions, pension and life providers — each
  with its website, on top of the larger banks elsewhere in the world it
  already had. Logos are fetched for the whole catalogue, your own accounts'
  banks first, and **Fetch logos** collects everything due in one sitting
  rather than forty a night. A row you add yourself is marked "added here" and
  is never touched by a release; catalogue rows are kept current by them. The
  `DeGiro`/`Degiro` pair the original seed shipped is merged into one.
- **Stocks & Shares, under Portfolio.** Every investment account as one
  portfolio: Portfolio, Day gain, Unrealised gain, Realised, Profit this year
  and over the last year; market value against cost over a chosen range; the
  spread across holdings and across accounts; and each account on its own
  line. Click an account for it position by position — quantity at average
  cost, price and the day's move, cost, value, the gain today or in all, and
  each holding's weight — with the same figures, chart and donut for the
  account alone. Nothing here is a new valuation: it reads the lots, prices,
  valuer and cash flows the Accounts, Wealth Over Time and Returns pages
  already read, and adds only the arithmetic between them.
- **Which accounts are on Stocks & Shares is each account's own setting.**
  Accounts → edit → "Show on Stocks & Shares", offered on investment accounts
  and on by default; an account's page there has Remove, and the overview
  names the accounts kept off with a Show button. The chart, profit and
  realised figures follow the list. On a phone the accounts and positions are
  cards rather than a table, each figure under its own label, so words are no
  longer broken in half to fit eight columns in 360 pixels.
- **Choose the currency your totals are shown in.** Profile now has
  **Reporting currency**: the currency Net Worth, Wealth Over Time, Allocation
  and every other total are added up in, for the whole household. Every
  household started in GBP and nothing could change it, so a household whose
  accounts were all in dollars saw its totals in pounds. The household
  principal chooses it; the history worked out from the transactions is
  rebuilt in it at once, and snapshots typed in or imported keep the currency
  they were recorded in.
- **A new household reports in its own country's currency.** Finishing the
  first-run wizard sets the reporting currency from the country chosen (United
  States → USD, Ireland → EUR, the UK and Crown Dependencies → GBP), for the
  household principal and only while the household has no accounts. The last
  screen says which currency, and where to change it.
- **Text size.** Profile now has **Text size**: Small, Normal, Large or
  Larger, on this device, in every look, applied at once. Menus and dialogs
  keep their usual size.
- **The app speaks the household's country.** Profile has **Household
  country** (every household was Jersey, and nothing could change it). In a US
  household a current account is **Checking**, money is written with a plain
  **$** (not US$, and an Australian dollar is still A$), dates start as
  month/day/year, and the ISA allowance reminder is not shown. The first-run
  wizard sets the country with the currency for a new household. Elsewhere
  nothing changes.
- **Investment memos from Microsoft Money.** The memo Money keeps on each
  investment is now imported from a `.mny` file and shown in grey under the
  instrument's name in an investment account's register. It takes two lines at
  most, and hovering shows the whole memo. **⋯ → Hide memos / Show memos**
  turns them off and on, per device. Memos are kept per household, so a memo
  never shows to a household that shares the instrument. A re-import replaces
  a changed memo. They are included in the household backup. Reading the memo
  needs the Money engine at 0.6.3; with an older engine, nothing is imported
  and nothing else changes.
- **Start again.** **Tools → Backup & Restore → Restore → Start again** clears
  the household's data so a file (a Money `.mny`, say) can be imported from
  scratch. It removes accounts, transactions, investments and their memos,
  categories, payees, budgets, scheduled payments, plans and pensions. It
  keeps the sign-ins, the household's people, its country and reporting
  currency, and its documents and renewals. It is the household principal's
  alone, and only with RESET typed. A **complete** backup (the System
  Administrator's format, plans and pensions included) is stored under
  Snapshots first; restoring it from there brings the household back whole.
  The card says what no backup carries yet: scheduled payments, budgets,
  category rules, reconciliations, wealth targets, plan goals and scenarios,
  and bank connections. Audited as `HOUSEHOLD.RESET`.
- **A balance is what the account holds today.** Entries dated after today
  (Money enters a dividend weeks early, below a line) were counted, so a
  tester's cash total was what it would be in December. The account list, the
  account page, an investment account's cash card, the accounts export and
  Data Health's comparison with a reported balance now count up to today. The
  account page says what is still to come: "Balance as of today. $2,076.17
  still to come in 2 entries dated after today ($12,391.26 including them)."
  The planner and the forecast still count entries already booked for the
  future, because they look forward.
- **US account types**. An account in the US can be a Traditional or Roth
  401(k), 403(b) or IRA, an HSA or a 529, alongside a taxable brokerage
  account (the GIA, named so for a US account). Each carries how it is taxed:
  Traditional pre-tax in and taxed out, Roth taxed in and never again, HSA and
  529 tax-free for medical and education spending. The 401(k), 403(b) and IRAs
  count as retirement money on every page; the Accounts list calls them
  401(k), Roth IRA, HSA. Choosing the United States at first run or in
  Household country now also makes the US where that person's new accounts
  start, so the form offers these rather than ISAs.
- **Social Security in the planner**. Planner → Pensions → State pension, in a
  US household, is **Social Security**. It asks for the monthly benefit at
  full retirement age from the person's Social Security statement and the age
  they will claim it, 62 to 70, and shows what that age is worth beside 62,
  full retirement age and 70. Full retirement age goes by year of birth (66,
  rising to 67 for 1960 on). Claiming early reduces the benefit by 5/9 of 1% a
  month for 36 months and 5/12 of 1% after; waiting adds 8% a year to 70. A
  spouse whose own benefit is under half the other's gets the spousal top-up
  from when both have claimed. The plan pays it from the claiming age and
  raises it with inflation (the cost-of-living adjustment), not the UK triple
  lock. Each line is named for its person ("Social Security — Pat"). A
  state-pension record saved with no currency now takes its country's, so a US
  record is in dollars rather than pounds.
- **Required minimum distributions**. From the starting age (72 if born 1950
  or earlier, 73 for 1951–1959, 75 from 1960) the plan takes at least last
  year-end's balance over the IRS Uniform Lifetime Table divisor from each
  Traditional 401(k), 403(b) and IRA, even when it would rather spend cash. It
  is taxed as income; it pays towards the year's spending; what it nets beyond
  that is kept as cash. The Drawdown plan marks it **R**. A Roth account has
  none.
- **A US retirement account is drawn by US rules.** A Traditional 401(k),
  403(b) or IRA is income in full when withdrawn (the planner had been giving
  it the UK's quarter tax free), a Roth one is not taxed at all, and either
  can be drawn from 60 (penalty-free from 59½) rather than the UK's pension
  age.
- **Medicare's income surcharge, IRMAA**. In a US household, from 65, the plan
  charges each adult the IRMAA surcharge on Part B and Part D when its own
  taxable income two years earlier passes a tier, joint for a couple, and adds
  it to that year's spending. CMS's 2026 and 2027 tables (2027 announced 17
  November 2026: tiers from $112,000 single and $224,000 joint); later years
  indexed with the plan's inflation. The Drawdown plan shows it in a Medicare
  IRMAA column, with the tier and the income that set it. The standard Part B
  premium is not added: a spending target is taken to include it.
- **Roth conversion planning**. A US household's plan can convert Traditional
  401(k), 403(b) and IRA money to Roth each year: to the top of a chosen
  federal bracket (Full tax), under a Medicare surcharge (IRMAA) tier two
  years on, or both, the lower winning, until a chosen year. Conversions come
  after the year's spending is drawn, land in the household's Roth IRA (or one
  the plan opens), and are taxed as income with the tax paid from cash (what
  cash cannot cover is kept back from the conversion). The Drawdown plan shows
  a Roth conversion column; plan files carry the settings.
- **Bank of America My Financial Picture: import its CSV export**. The export
  is recognised by its columns, with nothing to map and dates read month
  first. Pending rows are left out, and so are moves into and out of a
  broker's cash sweep fund (Chase reports its sweep as an investment, so each
  dividend appeared twice); the sweep's interest is kept. Dividends and
  interest are typed as such, MFP's categories are kept, and each row carries
  a key from what it says, so next month's export adds only what is new. A
  file of several accounts is refused, naming them.
- **US drawdown order**. A Traditional 401(k)/IRA and a Roth account each have
  their own place in the withdrawal order, which used to file both as "other
  pensions" and draw them in whatever order the accounts were listed. A US
  plan defaults to cash, then taxable brokerage, then Traditional, then Roth;
  an order saved before keeps working, with Traditional then Roth where the
  pensions were. The drawdown optimiser compares Roth before Traditional too,
  and calls a US band fill "the 10% bracket". Settings sheets accept
  TRADITIONAL and ROTH.
- **US capital gains reporting**. A US household's capital gains page shows
  each calendar year's sales from taxable accounts, short-term apart from
  long-term as Schedule D has them, with the $3,000 limit on a net loss and
  what carries forward; downloads the year's Form 8949 rows as CSV; and checks
  the totals from a broker's 1099-B and 1099-DIV, typed on the page and not
  kept. IRAs, 401(k)s, Roths, HSAs and 529s are left out.
- **Standard deduction or itemising**. A US household's Tax page has a
  Deductions tab: the standard deduction for the filing status (2026: $16,100
  single, $32,200 joint, $24,150 head of household, more for each person 65 or
  over or blind) against Schedule A — medical over 7.5% of AGI, state and
  local taxes under the $40,400 cap (cut above $505,000 of income), mortgage
  interest, and charity over 0.5% of AGI — from what was paid under the
  categories marked with those lines, and which is larger. Cash gifts of up to
  $1,000 ($2,000 joint) count with the standard deduction from 2026.
- **US tax categories**. A US household marks a tax-related category with a
  line of the return chosen from a list — Schedule A's medical, state and
  local taxes, mortgage interest and charity, and Form 1040's wages, interest
  and dividends — and the Categories page suggests lines from what the
  categories are called (Mortgage Interest is line 8a), applied only when you
  say so. Tax-Related Transactions shows each line in words.
- **Check numbers**. Money's Num column, an OFX download's check number and a
  QIF file's number now come across as the transaction's check number; the
  register shows a Num column on an account that has any, and the transaction
  form has a field for it.
- **Tax-loss harvesting suggestions**. A US household's capital gains page
  lists investments in taxable accounts worth less than they cost, with each
  loss, whether selling today would be short- or long-term, and the first day
  it could be bought back without a wash sale; one bought in the last 30 days
  is flagged, as selling it now would be a wash sale. It says what the losses
  would offset this year and the tax that saves at the rates you type.
- **Wash sales**. US capital gains now disallow a loss where the same
  investment is bought within 30 days either side of the sale, in any account:
  Form 8949 marks it W with the amount, Schedule D's totals include it, and
  the loss is added to the new shares' cost with the old holding period
  carried in, or lost for good where they were bought in an IRA or similar.
  The page lists what is waiting and what was lost.
- **Import from Quicken and other programs**. The import that read Microsoft
  Money files is now **Accounts → ⋯ → Import → From another program**, and it
  reads the transaction exports of Quicken (QIF), Quicken Simplifi, Monarch
  Money, YNAB, Rocket Money, Copilot Money, Empower (was Personal Capital),
  Mint and Tiller, each recognised from its columns: every account in the file
  comes in on its own, signs the right way round (Rocket Money and Copilot
  write spending as a positive number), categories with their parent, pending
  rows left out, YNAB transfers naming the other account and Simplifi's split
  transactions with their parts. Importing a later export again adds only the
  new rows. The dialog says where in each program the export is. Such a file
  offered to one account's import is sent to this one rather than misread.
- **State income tax in the planner**. A US household's plan names the state
  it lives in or will retire to (My forecast → State income tax), and with Tax
  set to Full the plan adds that state's income tax each year, on each
  person's income after the state's own exclusions: Social Security, which
  none of the states included taxes; all of a pension and IRA in Pennsylvania
  and Illinois, $20,000 a person in New York, up to $65,000 in Georgia,
  $67,610 in Michigan, New Jersey's exclusion and its income cliff; and a
  California, Massachusetts or North Carolina pension taxed in full. The
  Drawdown plan shows the state's share in a State tax column. States
  included: the nine with no income tax (Alaska, Florida, Nevada, New
  Hampshire, South Dakota, Tennessee, Texas, Washington, Wyoming), California,
  Georgia, Illinois, Massachusetts, Michigan, New Jersey, New York, North
  Carolina and Pennsylvania.
- **Payees and Categories** are in the sidebar beside Accounts, under
  Overview. They were under System, next to the SDK, where a tester could not
  find them.
- **A My Financial Picture export of every account** imports in one go from
  Accounts → ⋯ → Import → From another program: each account on its own,
  pending rows and cash-sweep moves left out and counted, dividends and
  interest typed, and a later export adding only the new rows. The import into
  one account still takes a one-account file and points at this one otherwise.
- **US estate planning in the planner**. For a US household the Estate tab
  gives the federal estate tax if death at the end of each forecast year: the
  estate with IRAs and 401(k)s in full, the exemption ($15,000,000 a person
  for 2026, doubled where a late spouse's unused part transferred, indexed
  with the plan after that year), 40% above it, the beneficiaries' income tax
  on an inherited Traditional account, what passes, and the **step-up in
  basis**: the gains your taxable accounts hold at death, which nobody pays
  capital gains tax on. **Qualified charitable distributions**: My forecast
  takes what each of you gives to charity straight from a Traditional IRA each
  year from 70½ (up to $111,000 a person in 2026); it leaves the pot untaxed,
  meets no spending, and counts towards the required minimum distribution. The
  Drawdown plan shows it in a **QCD** column.

---

## B1125

*19 November 2026*

- **Windows:** `WealthHorizon-Setup-B1125.exe` on the
  [B1125 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1125).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1125`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Saving an account's details looked temperamental.** When a save was
  refused, the reason was written at the top of the edit dialog, which had
  scrolled out of view, so on an iPad Save appeared to do nothing. The
  commonest case was an introductory rate end date with no rate afterwards.
  The reason now sits beside the Save and Cancel buttons and is scrolled into
  view, the rate box at fault is marked with it, and Save is disabled while a
  save is in flight, so two quick taps no longer send two saves (the second of
  which was refused as a clash with "another device").
- **The Accounts title no longer runs down the page one letter per line.** The
  totals band in the title row's corner sat in a grid, and a grid gives its
  content columns their whole width before the title's share: at 1600px the
  band's one-line width took the lot and the title column was 0px wide
  (B1123); on a 1194px iPad the controls alone left it 42px. The row is a flex
  line again, with the controls and the band in a right-hand column that
  cannot squeeze the title below its heading; below about 1170px the column
  takes a line of its own. A browser test measures the title.

Added or enhanced:

- **Sort and filter are one row on the accounts list.** The filter control is
  the heading: Account is a text box named for the column, and Juris., Expat,
  Type and Wrapper are drop-downs whose first entry, the column's name, means
  all. The sort arrow sits beside each. The separate filter row is gone, which
  gives the list another row's height.
- **An account's actions are small tiles beside the balance.** Add, Split,
  Payslips, Import, Balance, Edit, Export, Docs and the ⋯ menu are one-word
  small buttons, right-aligned on the balance's own line, so they no longer
  wrap to a second row under it on an iPad; the full name of each is on its
  tooltip. The register's Detail and Type filters live in their headings, as
  the accounts list's do. Together the transactions start about two rows
  higher.
- **Interest added automatically to a savings account.** Under the rates on a
  savings account's edit form, *Add the interest automatically each month*
  with a day of the month (the last day, or the 1st to the 28th). Every month
  on that day an Interest entry is dated to the account for the month before,
  at the rate on file applied day by day to each day's balance, gross. The
  first entry covers from the day the switch went on. The entry is an ordinary
  transaction: edit or delete it and it stays as left, never re-posted. A
  month whose interest the bank has already paid is left alone. The account
  page says "added automatically on the …" under the balance.

---

## B1101

*18 November 2026*

- **Windows:** `WealthHorizon-Setup-B1101.exe` on the
  [B1101 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1101).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1101`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Behind-the-scenes changes only; nothing you will notice.

---

## B1095

*18 November 2026*

- **Windows:** `WealthHorizon-Setup-B1095.exe` on the
  [B1095 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1095).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1095`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Behind-the-scenes changes only; nothing you will notice.

---

## B1093

*18 November 2026*

- **Windows:** `WealthHorizon-Setup-B1093.exe` on the
  [B1093 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1093).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1093`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **A QIF file's dates were read in two conventions at once.** QIF carries no
  locale, and Money writes dates the exporting machine's way, so `05/07/2026`
  is 5 July on a UK machine and 7 May on a US one. The reader decided per row:
  a day above 12 forced the order, everything else fell to day-first, so a
  file proving itself month-first with `01/13/2026` still read `07/05/2026` as
  7 May. The order is now decided once from the whole file; an undecidable
  file is read day-first and the import preview says so. An ISO date is no
  longer read twenty-one years out, and 31 February is rejected rather than
  rolled into March.

---

## B1085

*17 November 2026*

- **Windows:** `WealthHorizon-Setup-B1085.exe` on the
  [B1085 release](https://github.com/MunerisUK/WealthHorizonLS/releases/tag/B1085).
  Run it over the top of the build you have; your data is kept.
- **Docker:** tag `B1085`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **Table rows three lines tall on an iPad.** Sized to its content, a table
  could shrink a column by breaking what was in it: on Prices the action icons
  stacked down a column, an ISIN split in two and SEDOL became "SEDO L". A
  heading now stays on one line, an actions column takes only the width its
  buttons need, and a code column is never broken.

---

## B1069: the licence key is asked for first

*16 November 2026*

- **Windows:** `WealthHorizon-Setup-B1069.exe` on the
  [latest release](https://github.com/MunerisUK/WealthHorizonLS/releases/latest).
  Run it over the top of B1067; your data is kept.
- **Docker:** tag `B1069`. Back up in the app, then run `docker compose pull`
  and `docker compose up -d`.

Fixed:

- **A new install no longer stops on its first screen with
  "LICENCE_REQUIRED".** WealthHorizon now asks for your licence key straight
  after you register, in plain words: paste it in and click **Activate**, or
  choose **I'll do this later**. Your home country and date of birth are saved
  either way.
- **When a change needs a licence key, WealthHorizon says so in a sentence**
  instead of showing a code.

---

## B1067: WealthHorizon for Windows

*16 November 2026*

**WealthHorizon now installs on Windows 10 and 11 without Docker.** Download
`WealthHorizon-Setup-B1067.exe` from the
[latest release](https://github.com/MunerisUK/WealthHorizonLS/releases/latest)
and run it. See [Install on Windows](README.md#install-on-windows).

**Docker:** the images are tagged `B1067`. Back up in the app, then run
`docker compose pull` and `docker compose up -d`.

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
