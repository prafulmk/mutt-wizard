# mutt-wizard

The mutt-wizard is a simple interface gives you:

- a fully-functioning neomutt-based terminal email workflow with vim bindings, vibrant display.
- email backed up offline with offlineIMAP, allowing mobile and offline access of all your mail.
- automatically generated shortcuts for jumping between different accounts or mailboxes within an account.
- sensible binds that make managing, moving and reading mail quicker and easier than ever.
- your passwords safely encrypted on your machine so you (and only you) can access your account easily (uses GPG).

I maintain mutt-wizard for GNU/Linux, but individual contributors have also made it compatible with Mac.

## Use mutt-wizard

Clone the repo to `~/.config/mutt`. Either move to backup or delete your old `~/.config/mutt` directory if you have one. Remove/backup your old offlineimap and msmtp configs if you have them as well.

Be sure to install the following programs:

- `neomutt` - the email client. If you delete a lot of the neomutt-specific settings in the muttrc, you can run vanilla mutt if you want.
- `offlineimap` - downloads the email. Required for installation.
- `msmtp` - sends your email.

**You must have a GPG public/private key pair as well.** This is what will safely encrypt your passwords. Run `gpg --full-gen-key` (or `gpg2 --full-gen-key`) to get one.

## Install

Once the repository is in place in `~/.config/mutt/`:

- Select to add an account. This will autogenerate your config files for mutt, offlineimap and msmtp.
- Run `offlineimap` once (at least a partial sync). This will create all the directories you need to finalize installation and will start downloading your mail.
- Select the option to autodetect mailboxes. This will use the directories offlineimap creates to detect your mailboxes and make your mail readable by mutt.

### Optional dependencies

mutt-wizard is configured by default for you to use other useful tools, but these are not strictly necessary.

- `w3m` - You'll probably want this one at least. It will help you read HTML email from those terrible people who send it... if you want to. It will also enable viewing images in mutt.
- `notmuch` - can index your mail to be easily searched. Install it and run `notmuch setup`, tell it that your mail is in `~/.local/share/mail/`. You can run it in mutt with `ctrl-f`. Remember to run `notmuch new` to process new mail, although the included `mailsync` script does this for you.
- `abook` - a terminal-based address book. Pressing tab while typing an address to send mail to will suggest contacts that are in your abook.
- A cron manager - if you want to enable the auto-sync feature.

## New stuff and improvements since the original release

- `dialog` is no long used (le bloat) and the interface is simply text.
- More autogenerated shortcuts that allow quickly moving and copying mail between boxes.
- More elegant attachment handling. Image/video/pdf attachments without relying on the neomutt instance.
- abook integration by default.
- The messy template files have been removed and are now a part of the script itself.
- Optimal XDG standards compliance, moving offlineimap and msmtp configs to `~/.config/` and moving mail to `~/.local/share/mail/`.
- `accounts/` hold account data and `bin/` holds script run by or for mutt. All other directories have been disintegrated.
- Better handling of different gpg versions.
- Script is POSIX sh compliance.

## Known issues (not my fault!)

- If you're using a Gmail account, check the pinned issue on the Github. Gmail accounts haven't been working properly with offlineimap recently, but there's an easy fix. Remember also to enable third-party ("""less secure""") applications.
- Check the ProtonMail issue as well. ProtonMail recently allows IMAP usage with their Bridge program for paid users. I don't have this, so I can't bugtest on it, but many users have gotten it working. Either way, it requires a little more work than just using the wizard.
- Don't expect mutt-wizard to work out the box on a university email. Universities often have special IMAP policies and server settings. You might be lucky, but you might have to changes some settings in the offlineimap config file to get it to work properly with a university email.
- If you use an email server whose mailboxes are not in English, mutt-wizard might not be able to guess which is which, so you may have to manually set your Inbox, Sent, Trash, Drafts, etc. in your mutt config file.

## Help!

- Try mutt-wizard out on weird machines and weird email addresses and report any errors.
- Open a PR to add new server information into `domains.csv` so their users can more easily use mutt-wizard.
- If nothing else, [Donate!](https://paypal.me/LukeMSmith)

See Luke's website [here](https://lukesmith.xyz). Email him at [luke@lukesmith.xyz](mailto:luke@lukesmith.xyz).
