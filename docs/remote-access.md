# Reaching WealthHorizon from outside your home

**Who this is for:** the person who installed WealthHorizon and looks after
the computer it runs on (usually the household's System Administrator).

WealthHorizon is designed to run on your own computer and be used on your own
home network. Reaching it from anywhere else is **optional**, and this guide
explains the choices, starting with the safest.

---

## Read this first

- **Doing nothing is the safest choice.** WealthHorizon works fully without
  ever being reachable from the internet. If you don't need to use it away
  from home, stop here.
- **No software can make a computer on the internet completely safe.**
  Anything you make reachable from outside your home can be found and
  attacked. The steps below reduce that risk; they cannot remove it.
- **The set-up is yours.** Your router, your network, any VPN, reverse proxy,
  domain name or certificate, and any third-party service you choose are
  under your control and their providers' terms, not WealthHorizon's. We
  don't supply, configure, monitor or support them.
- **This guide is general information, not professional security advice.**
  It can't account for your particular router, network or provider. If you
  aren't confident about any step, ask a qualified IT professional, or don't
  go ahead.
- **Your licence still applies.** Your use of WealthHorizon is governed by
  your licence agreement, including its terms that the software is supplied
  "as is" and that limit liability. Nothing in this guide changes those terms
  or gives any warranty or guarantee.
- **Products named here are examples only.** Muneris has no affiliation with
  them and doesn't endorse them. Use whatever suits you, and follow its own
  documentation.

---

## Before you start: secure what's already there

Do all of these first, whichever option you choose:

1. **Update to the latest build** of WealthHorizon, and keep updating it.
2. **Switch on two-factor sign-in for every person** who uses this
   WealthHorizon (each person does this under **My Account**). It is the
   single most effective protection: a stolen password alone is no longer
   enough to sign in.
3. **Use a strong password that isn't used anywhere else** for every person,
   especially every System Administrator.
4. **Check public sign-ups are Blocked** (the switch at the top of **System
   Admin**), so nobody can create an account on your WealthHorizon from
   outside. On a household licence they already are.
5. **Take an encrypted backup** under **Backup & Restore**, and keep a copy
   somewhere other than this computer (scheduled backups to a OneDrive folder
   do this for you).
6. **Know how to undo** whatever you set up (see the end of this guide).

What WealthHorizon already does to help:

- **Limits guessing:** sign-in allows 10 attempts per account every 15
  minutes, then makes the caller wait.
- **Records sign-ins:** successful, failed and throttled sign-ins are written
  to the **Audit log** in System Admin, so you can see who has tried.
- **Two-factor sign-in:** a code from an authenticator app, as above.

---

## Your three options, safest first

### Option 1: at home only (the default, and the safest)

On Windows, WealthHorizon answers on port **8082** of the computer it runs
on. If you ticked **Let other devices on my home network open WealthHorizon**
when installing, other computers on your home network can reach it at `http://<computer-name>:8082`. Windows Firewall only
allows this on networks marked **Private**, never on a public network such as
a café's Wi-Fi.

Nothing is reachable from the internet. Nothing more to do.

*On Docker or a NAS*, WealthHorizon answers on the address and port your
installation was set up with; read that wherever this guide says port 8082.

### Option 2: a private VPN (recommended if you need access away from home)

A VPN lets your own phone or laptop join your home network privately, from
anywhere. **Nothing is opened to the internet**, and WealthHorizon only ever
sees devices you've added to your VPN. This is the option we recommend.

Two common ways to do it:

- **Your router's own VPN**, if it has one (many have WireGuard or OpenVPN
  built in). Follow your router maker's instructions.
- **A "mesh" VPN service** (Tailscale is one example) that you install on the
  WealthHorizon computer and on each device you use. Follow the service's own
  instructions, and protect that account with two-factor sign-in too, because
  whoever controls it controls who can join.

Once connected, open `http://<computer-name>:8082` (or the address your VPN
gives the computer) exactly as you would at home. The VPN encrypts the
connection.

This needs **Let other devices on my home network open WealthHorizon** to have
been ticked when installing (run the installer again to tick it). If it still
doesn't connect over a VPN service, Windows may be treating the VPN's
connection as a **Public** network, where WealthHorizon is deliberately not
allowed. The VPN service's own documentation explains how its connection is
classified; don't open WealthHorizon on public networks to get round it.

Good practice:

- Add only your own devices, and remove any you lose or sell.
- Keep the VPN software and your router's firmware up to date.

### Option 3: a public web address (advanced; not recommended for most people)

This makes WealthHorizon reachable by anyone on the internet at a web address
of your own, protected by HTTPS. It is the option with the **most exposure**:
your sign-in page can be found and attacked by anyone. Choose it only if you
understand what each step does, are prepared to keep every part of it up to
date, and accept that risk.

It needs four things, set up with each product's own documentation:

1. **A domain name** that points at your home's internet address (a dynamic
   DNS service can keep it pointed there if your address changes).
2. **A certificate** from a recognised authority, so the connection is
   encrypted (Let's Encrypt issues them free, and many reverse proxies obtain
   and renew them automatically).
3. **A reverse proxy** on the WealthHorizon computer or on your network (Caddy
   and nginx are examples). It accepts HTTPS from the internet, holds the
   certificate, and passes requests on to WealthHorizon at
   `http://localhost:8082`.
4. **A port-forwarding (NAT) rule on your router** that sends port **443**
   (HTTPS) to the reverse proxy, and nothing else.

Rules that matter:

- **Never forward port 8082** (or any WealthHorizon port) to the internet.
  WealthHorizon speaks plain HTTP on it, so passwords would cross the
  internet unencrypted. Only the reverse proxy, on 443, should be reachable.
- **Two-factor sign-in for everyone is a must** with this option, not a
  nice-to-have.
- **Keep everything updated:** WealthHorizon, the reverse proxy, the
  operating system and the router's firmware.
- **Check the Audit log** in System Admin now and then for failed or
  throttled sign-ins you don't recognise.
- **Don't sign in from shared or public computers.**
- If your reverse proxy can limit access (to certain countries, addresses or
  a second password), consider using it.

---

## If something looks wrong

1. **Close the door first:** remove the port-forwarding rule from your
   router, or turn the VPN off.
2. **Change passwords** for everyone, starting with System Administrators,
   and check that two-factor sign-in is still on.
3. **Look at the Audit log** in System Admin for sign-ins you don't
   recognise.
4. If anything in your data looks changed, **restore from your backup** under
   **Backup & Restore**.

## How to undo

- **Option 2:** remove the WealthHorizon computer from your VPN, or turn the
  VPN off.
- **Option 3:** delete the port-forwarding rule on your router, then stop or
  uninstall the reverse proxy.
- **Back to Option 1:** with neither in place, WealthHorizon is reachable only
  on your home network again.
