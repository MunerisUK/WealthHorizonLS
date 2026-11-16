# WealthHorizon

WealthHorizon keeps track of your accounts, investments and pensions, and helps
you plan ahead. I built it to replace Microsoft Money, and it can read a Money
`.mny` file directly.

This repository is for people running WealthHorizon. It holds the instructions,
the Windows installer and the Docker Compose file you need to run WealthHorizon
on your own hardware. It does not hold the source code. You need a licence key
from the WealthHorizon store to use it.

There are three ways to run it:

- **On a Windows 10 or 11 PC:** one installer, nothing else to set up. See
  [Install on Windows](#install-on-windows).
- **On a QNAP or Synology NAS,** point and click in the NAS's own container
  app. See [Install on a QNAP or Synology NAS](#install-on-a-qnap-or-synology-nas).
- **With Docker** on a NAS, a server or a PC, from the command line: see
  [Before you start](#before-you-start).

> **Not financial advice.** The planning, tax and forecast pages work from the
> figures you enter. They help you think things through. They are not advice,
> a recommendation or a promise.

## Install on Windows

You need a 64-bit PC with Windows 10 or 11, and a licence key from the
WealthHorizon store. You do not need Docker.

1. Download `WealthHorizon-Setup-B….exe` from the
   [latest release](https://github.com/MunerisUK/WealthHorizonLS/releases/latest).
2. Run it and say yes to the Windows administrator prompt. If Windows says
   **"Windows protected your PC"**, choose **More info**, then **Run anyway**.
   The installer is not code-signed yet.
3. Tick **Let other devices on my home network open WealthHorizon** only if you
   want to use it from a phone, tablet or Chromebook at home. It works only on
   networks Windows treats as private.
4. Setup waits while WealthHorizon starts. The first start sets up the database
   and takes a minute or two. Then it opens WealthHorizon in your browser. You
   can also use the **WealthHorizon** shortcut, or go to `http://localhost:8082`.
5. Choose **Register** and create your account. The first account becomes the
   administrator.
6. Enter your licence key: **System Admin → Licence → Activate on this machine**.

WealthHorizon runs quietly in the background as a Windows service and starts
with your PC.

- **Your data** is in `C:\ProgramData\WealthHorizon`. Only administrators can
  open it. Make backups in the app and copy them to another drive.
- **To update,** download the newer installer and run it over the top. Your data
  is kept.
- **To remove it,** use **Settings → Apps → WealthHorizon**. Your data is kept
  until you delete `C:\ProgramData\WealthHorizon` yourself, so reinstalling picks
  it up again.

The rest of this page is about running WealthHorizon with Docker. The sections
on [your data](#your-data), [using it away from home](#using-it-away-from-home)
and [reporting problems](#reporting-problems) apply to Windows too.

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

6. Import your Money file, or start entering accounts. The
   [user guide](docs/user-guide.md) walks you through it.

## Install on a QNAP or Synology NAS

This is the same Docker setup, done in the NAS's own container app instead of
the command line. You need:

- a QNAP with **Container Station 3**, or a Synology with **Container Manager**
  (DSM 7.2 or later)
- a NAS with a **64-bit** processor (Intel, AMD or ARM64). Older 32-bit ARM
  models cannot run WealthHorizon
- a licence key from the WealthHorizon store

### 1. Prepare the settings

1. Open [docker-compose.yml](docker-compose.yml) here, click **Raw**, and copy
   everything.
2. Make two long random passwords, using **letters and numbers only** (no
   symbols): one of about 48 characters and one of about 64. A password
   manager's generator is the easiest way.
3. Paste the file into a text editor and change these lines:
   - Both lines that say `${PGPASSWORD:?set PGPASSWORD in .env}`: replace all
     of that with your **first** password. It must be the same in both places.
   - The line that says `${JWT_SECRET:?set JWT_SECRET in .env}`: replace all of
     that with your **second** password.

   Keep this edited copy somewhere safe and private. It holds your passwords.

### 2a. On a QNAP (Container Station)

1. Open **Container Station → Applications → Create**.
2. Name the application `wealthhorizon`.
3. Paste your edited file into the YAML box.
4. Change the three `./data/` paths to a folder on a share, so your data is
   easy to find and back up. For example:
   - `./data/pgdata` becomes `/share/Container/wealthhorizon/pgdata`
   - `./data/documents` becomes `/share/Container/wealthhorizon/documents`
   - `./data/backups` becomes `/share/Container/wealthhorizon/backups`
5. Click **Validate**, then **Create**.

### 2b. On a Synology (Container Manager)

1. In **File Station**, make a folder for it, for example
   `docker/wealthhorizon`.
2. Open **Container Manager → Project → Create**.
3. Name the project `wealthhorizon`, and choose the folder you just made as
   the **Path**.
4. For **Source**, choose **Create docker-compose.yml** and paste your edited
   file.
5. Click **Next** until it finishes. Leave **Web portal** off. Your data goes
   in the `data` folder inside the project folder.

### 3. Open it and activate

1. The first start sets up the database and takes a minute or two.
2. Open `http://<your-nas>:8082` in a browser, using your NAS's address or
   name. If something else on your NAS already uses port 8082, change the left
   side of `"${WH_PORT:-8082}:8082"` to another port, for example
   `"8090:8082"`, and use that port instead.
3. Choose **Register** and create your account. The first account becomes the
   administrator.
4. Enter your licence key: **System Admin → Licence → Activate on this
   machine**.

**To update:** make a backup in the app first. Then, in Container Station or
Container Manager, pull the latest `wealthhorizonls-backend` and
`wealthhorizonls-frontend` images and restart the application or project. The
exact buttons differ between versions of the NAS software.

If it does not start, look at the logs of the `api` container in Container
Station or Container Manager. They say what went wrong.

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
What changed in each build is in the [release notes](RELEASE-NOTES.md).

To run a particular build instead of the latest, set `WH_TAG` in `.env`, for
example `WH_TAG=B1047`, and run the two commands again. This is also how you go
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
