# Privacy notice

> **Draft.** This notice was prepared by the product team and has not been
> reviewed by a solicitor or a data-protection specialist. Have it reviewed,
> and fill in the details marked `[in brackets]`, before you rely on it or
> publish it.

**Last updated:** [date] · **Version:** 0.2 (draft)

## Who this is about

WealthHorizon is run on **your own hardware**. Your financial and household
data lives in the database on your machine and in the backups you make.
**Muneris Management Ltd does not receive, store or have access to it.** We
cannot see your accounts, balances, transactions, documents or plans. Support
that would need to see your data happens only if you switch on an access grant
inside the software, for a period you choose, and switch it off again.

Because of that, this notice is mostly about the small amount of information
that leaves your installation, and the details you give us when you buy a
licence or send feedback.

## Who we are

The data controller for the information described below is:

**Muneris Management Ltd**, a company registered in England and Wales,
company number 09096411.
Registered office: 20-22 Wenlock Road, London, England, N1 7GU.
Contact: **info@muneris.co.uk**.

For questions about this notice or your personal data, email the address
above with "Privacy" in the subject line.

## What leaves your installation, and why

WealthHorizon lists every connection it makes on its own **Privacy &
connections** page (under **Tools**): what each one is, where it goes, what it
sends, when, and whether it is on by default. This section describes the same
connections.

### 1. Buying a licence

You buy a licence key through our online shop, which uses **Lemon Squeezy**
(Lemon Squeezy LLC) as the seller and payment processor. They collect your
name, email address, billing country and payment details, and give us your
name, email, order and the licence key. We do not see your card number.

- **Why:** to sell you the licence and support you.
- **Lawful basis:** performance of our contract with you.

### 2. Checking your licence

When the software activates and then checks your key, about once a day on a
licensed build, it contacts the licensing service: **Lemon Squeezy** for a key
bought there, or the **Muneris licence server** for a key issued by us. These
requests carry your **licence key** and an **identifier for this
installation** (with Lemon Squeezy, also the installation's name), and, like
any internet request, your installation's **IP address**. They carry nothing
about your finances.

- **Why:** to confirm the licence is valid and used on one machine at a time.
- **Lawful basis:** performance of our contract with you.

### 3. Checking for a newer build

On the Windows installer and the published Docker images, WealthHorizon asks
our **update relay** whether a newer build is available, when a page loads and
at most once every six hours. The request carries your **licence key**, as
proof that it comes from a licensed copy, and your IP address. It carries
nothing about your finances. On other installations it is off unless an
administrator sets it up.

- **Why:** to tell you when an update, including a security fix, is available.
- **Lawful basis:** [our legitimate interest in keeping licensed installations
  up to date and secure — confirm].

### 4. Feedback you choose to send

If you use the **Feedback** page in the app, your report is sent to us through
the same relay. It carries the text you write, your **display name** in
WealthHorizon, and a small, fixed set of technical details: the build number,
the page you were on, your browser, your screen size, and the last error the
app recorded. The request is accompanied by your licence key, as proof that it
comes from a licensed copy; the key is not part of the report. It is turned
into an issue on our private issue tracker, which is hosted by **GitHub, Inc.**
in the United States.

The app is designed **not** to include your account names, balances or
figures in a report — but the free-text box is yours, so please do not type
personal or financial details into it.

- **Why:** to fix problems and improve the software.
- **Lawful basis:** our legitimate interest in improving the product, and your
  choice to send each report.

### 5. The optional daily heartbeat

There is an optional daily "heartbeat" that is **off unless you switch it on**.
When on, it sends the build number, the software version, how many days the
server has been up, the **date** (not the time) of the last sign-in, your
licence instance identifier, the server software version and the edition, with
your licence key. It carries nothing about your finances and no account names.

- **Why:** to understand whether installations are active and up to date.
- **Lawful basis:** your consent (you switch it on, and can switch it off).

### 6. Prices and exchange rates

WealthHorizon asks **public market-data sources** (Stooq, Yahoo Finance, and
Coinbase for cryptocurrencies) for prices and exchange rates: exchange rates
once a day for the currency pairs you have switched on, and prices when you
press Refresh. A back-test on the Growth & income tab asks Yahoo Finance for a
holding's price history. These requests carry the ticker symbols and currency
codes, and your IP address, but no name and no account details (though the
symbols asked for show what is held).

- **Why:** to value your accounts and holdings.
- **Lawful basis:** performance of our contract with you.

### 7. Public reference data

These requests carry nothing about you beyond your IP address:

- **Tax rate tables**, fetched from government websites (such as gov.uk,
  gov.je, revenue.ie and irs.gov) when WealthHorizon starts and every 30 days.
- **Bank logos**, fetched from each bank's own website a few at a time, for
  every bank in WealthHorizon's catalogue rather than only yours, so no bank
  learns that you hold an account with it.
- **Payee logos**, fetched only for payees you have given a website.

### 8. Connections you choose to set up

None of these is on unless you set it up, and each sends only what that
service needs:

- **SimpleFIN** (US banks and brokers): your SimpleFIN access, to read your
  accounts, balances and transactions.
- **Trading 212**: your read-only API key, to read your account, positions,
  orders and dividends.
- **Open Banking (TrueLayer)**: available only where your administrator has
  registered a TrueLayer application; your consent and the tokens it gives, to
  read your bank accounts, balances and transactions.
- **Email**: sent through the mail server **you** configure, not through us.
- **AI assistance**: off until switched on. Questions go to the model you
  choose (by default one running on your own computer), cut to the level of
  detail you allow, and never include contact details, dates of birth or
  notes.

When you connect one of these services, your relationship with it is governed
by its own terms and privacy notice.

- **Why:** to provide the features you turn on.
- **Lawful basis:** your consent / performance of our contract.

## Cookies and local storage

The app runs in your browser against your own server. It stores a sign-in
session and your preferences in your browser's local storage. It does **not**
use third-party advertising or tracking cookies.

## Sharing and international transfers

We do not sell your personal data. We share it only with the service providers
named above — Lemon Squeezy (sale, payment and licence checks), GitHub
(feedback issues) and [the provider hosting our update and feedback relay] —
acting for us. Some of these providers are in the **United
States**, so sending data to them is an international transfer; where that
happens it is covered by appropriate safeguards (such as the UK International
Data Transfer Agreement or an adequacy decision). [Confirm the mechanism for
each provider.]

## How long we keep it

- **Purchase and licence records:** for as long as you hold a licence, and
  afterwards as long as we must for tax and accounting law (normally six
  years).
- **Feedback issues:** for as long as they are useful to the product, then
  closed and retained in the tracker's history.
- **Heartbeat records:** 12 months, then deleted.
- **Update-check requests:** [how long the relay keeps its request logs — confirm].

Your own data on your own machine is kept, and deleted, by you.

## Your rights

Under UK data protection law you have the right to ask us for a copy of the
personal data we hold about you, to have it corrected or deleted, to object to
or restrict how we use it, and to receive it in a portable form. To exercise
any of these, email **info@muneris.co.uk**.

You can also complain to the UK regulator, the **Information Commissioner's
Office** (ico.org.uk), though we would be glad to put things right first.

## Changes to this notice

We will update this notice as the product changes, and will note the date at
the top.
