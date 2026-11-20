# Sandbox setup

The hard test never touched a real app. This page says what it ran against and how it was sealed off.

## The practice app

**OWASP Juice Shop**: https://github.com/juice-shop/juice-shop

Juice Shop is a free, open-source web shop that is insecure on purpose. It is maintained by OWASP and used in security training, awareness demos and capture-the-flag events, so people can learn how weak spots in web apps are found and fixed. Its README explains how to run it on your own machine. Everything in it, including its user accounts, is made-up practice data.

## How it was sealed

- The practice app ran in its own isolated sandbox on one machine.
- The sandbox had no internet. This was checked before the run.
- The sandbox could not see the host machine's files.
- The only thing reachable from inside was the practice app itself.
- When a model was given a loop, every command it issued ran inside that sandbox and nowhere else.

## The rules for these tests

- Only test systems you own, or have written permission to test.
- Never point a model like this at someone else's site, app, network or account.
- Keep it offline and sealed, so a mistake cannot reach anything real.
- Use it to find problems so that you can fix them.
- An uncensored model on your own machine has nobody checking what you do with it. That is your responsibility.

A practice app that was built to be broken is not a real security review. If your app matters, get it reviewed properly.
