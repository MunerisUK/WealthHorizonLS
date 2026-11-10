# WealthHorizon

WealthHorizon keeps track of your accounts, investments and pensions, and helps
you plan ahead. I built it to replace Microsoft Money, and it can read a Money
`.mny` file directly.

This repository is for people running WealthHorizon. It holds the instructions and the Docker
Compose file you need to run WealthHorizon on your own hardware. It does not
hold the source code. The software itself comes as Docker images, and you need
a licence key from the WealthHorizon store to use it.

> **Not financial advice.** The planning, tax and forecast pages work from the
> figures you enter. They help you think things through. They are not advice,
> a recommendation or a promise.

## Before you start

You will need:

- a computer, NAS or server that runs **Docker Engine with Docker Compose v2**,
  on 64-bit x86 or ARM
- to be comfortable with Docker: editing a Compose file, reading container
  logs, updating images and keeping your own backups
- a licence key from the WealthHorizon store. The link is in your invitation
  email.

I can help with problems in WealthHorizon itself. I cannot help with Docker,
your network, your firewall or reaching your server from outside your home.

## Install

1. Make a folder for WealthHorizon and download the two files into it:

   ```sh
   mkdir wealthhorizon && cd wealthhorizon
   curl -fsSLO https://raw.githubusercontent.com/MunerisUK/WealthHorizonLS/main/docker-compose.yml
   curl -fsSL  https://raw.githubusercontent.com/MunerisUK/WealthHorizonLS/main/.env.example -o .env
   ```

2. Open `.env` and fill in `PGPASSWORD` and `JWT_SECRET`. The file explains each
   one and how to generate it.

3. Start it:

   ```sh
   docker compose pull
   docker compose up -d
   ```

   The first start sets up the database, which takes a minute or two. To watch
   it: `docker compose logs -f api`.

4. Open `http://<your-server>:8082` in a browser. The first account you create
   becomes the System Administrator.

5. Enter your licence key: **System Admin → Licence → Activate on this
   machine**. The machine needs an internet connection the first time, so the
   key can be checked. Until a key is active you can sign in and look around,
   but you cannot add or change anything. Whatever happens to the licence
   later, you can always read and export your data.

6. Import your Money file, or start entering accounts.

## Your data

Everything is kept in the `data` folder next to `docker-compose.yml`:

| Folder | What it holds |
|---|---|
| `data/pgdata` | The database |
| `data/documents` | Files you attach to accounts and transactions |
| `data/backups` | Backups, if you set the backup folder in the app to `/backups` |

Copy your backups somewhere other than the machine WealthHorizon runs on. A
backup that sits on the same disk as the database will not help if that disk
fails.

Your financial data stays on your machine. WealthHorizon contacts the outside
world only for these things:

- **the licence check**, which sends your licence key and an identifier for
  this machine to the licensing provider
- **price and exchange rate updates**, which ask public sources for the
  symbols and currencies you hold
- **feedback you choose to send**, which carries the build number, the page,
  your browser and the last error, and never an account name or a figure
- **an optional daily heartbeat**, off unless you switch it on

## Updating

1. Make a backup in the app first.
2. Then:

   ```sh
   docker compose pull
   docker compose up -d
   ```

Database changes are applied automatically when the new version starts.

To run a particular build instead of the latest, set `WH_TAG` in `.env`, for
example `WH_TAG=B1070`, and run the two commands again. This is also how you go
back to an earlier build if a new one causes you a problem.

## Using it away from home

WealthHorizon works in a browser on a phone, tablet or computer. Reaching it
from outside your home is up to you. Do not open port 8082 to the internet
directly: it is plain HTTP. Use a VPN, or a reverse proxy that serves it over
HTTPS.

## Moving to another machine

1. Make a backup and copy it to the new machine.
2. On the old machine: **System Admin → Licence → Move this licence**. This
   releases the key without deleting anything.
3. Install on the new machine, restore the backup and activate the key there.

## Removing it

`docker compose down` stops WealthHorizon and keeps your data. Deleting the
`data` folder removes everything for good, so export what you want to keep
first.

## Reporting problems

- **Use the Feedback page in the app.** It sends your report to me privately,
  with the details I need to fix it.
- **Do not put financial details in a public issue here.** This repository is
  public. Issues here are only for problems installing or updating, and must
  not contain balances, account names, payslips or anything else personal.
- **Security problems:** see [SECURITY.md](SECURITY.md). Please do not open a
  public issue.

## Privacy

Your financial data stays on your machine; Muneris cannot see it. The small
amount of information that leaves your installation — a licence check, optional
price updates, and any feedback you choose to send — is described in
[PRIVACY.md](PRIVACY.md).

## Licence

WealthHorizon is proprietary software owned by Muneris Management Ltd. See
[LICENSE.md](LICENSE.md). Your right to use it comes from the licence agreement
you accept when you buy your key. It is for your own household's use. It must
not be used by a financial services firm, or to give financial advice to other
people as a business.
