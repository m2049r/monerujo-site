---
layout: resource
---

# Where Monerujo stores your wallets

Since version 2.x 'Puginarug' Monerujo changed the place where it saves your wallets' files. Let's break it down:

## How it was before:
Until now, wallets were saved in the *external storage* which the apps on your phone can use to store files or stuff you produce in them. For example, that's the place your camera app stores the photos you take. This is the storage you have access to when you connect your phone to a PC. Technically, every app has access to every file that's in there when you give the app persmissions to do so. That's how you can install two different audio players, and they can find the same stored mp3 songs. That's also why Monerujo (and any other app which works with files) needed to ask for your permission to "Access your files and photos." when you install it for the first time. Monerujo needed your permission to save stuff in that storage.

When Monerujo creates a new wallet or restores a previous one, it creates a couple of files with that wallet's name, and encrypts them with the CrAzYpass. [You can read more about it on this article](https://anhdres.medium.com/how-monerujos-crazypass-crazy-secure-password-scheme-works-dc4f99a99ff0). Basically, the CrAzYpass is a crazy secure password made up of a combination of the password you choose, and an identifier of the phone. It is very long and impossibly hard to crack, securing your funds even though they were on this easily accesible storage.

### Pros:
* Files were not deleted when you uninstalled the app. That meant that if you reinstalled Monerujo, the wallets were magically there. You only had to know their matching CrAzYpasses.
* Files were easily accesible. If you wanted to backup them, you just needed to open a file browser app on your phone or connect it to a computer with your USB cable, look for the monerujo folder, and copy them from there.
* If a wallet file got corrupted, [it was easy to just go there and delete the cache file](https://anhdres.medium.com/how-to-solve-a-corrupt-wallet-file-with-monerujo-19fc621b1f2d).

### Cons:
* Wallet files couldn't be cracked open without the matching CrAzYpass, but they could be deleted or corrupted with ease by any malicious app on the phone.
* When users opened the app for the first time, they got presented with a request for access to the "Files and photos" storage. That sounded like way more than Monerujo needs, and was a source of suspicion from the anybody not familiarized with the inner workings of Android.
* From Android 11 and onwards, apps are required to not use this storage anymore, so this method isn't future-proof.
* Files were not deleted when you uninstalled the app. Which meant that users could believe that traces of Monero usage dissapeared with just removing the app, while the wallet files remained on the external storage.
* Wallets couldn't be properly deleted from the app. They were merely archieved because files remained in the storage. Even if deleted, Monerujo couldn't assure you they were actually out of the capabilities of a special recovery program.

## How it works from now on:
Form now on, and following guidelines and best practices for Android apps, Monerujo will save your wallet files on the *internal* storage. This storage is encrypted and can be accessed only by the app that created the files. This storage doesn't require any permission from the user, since it cannot read or modify anything else that is not created by this particular app. This storage is technically safer from a security perspective, but it has its quirks. Let's explore them.

### Pros:
* The wallet files are going to be additonally encrypted (on most newer devices) by Android on top of being already encrypted with the CrAzYpass. Double security!
* No request for authorization to access the storage on first use of the app. Monerujo doesn't care about your other files, it will save its wallets on its own private storage space.
* Removed chance of wallet files being copied, or accesed, or seen by any other app installed on the phone, be it good or evil.
* When necessary, wallets can be actually deleted from within the app, and since they were encrypted, there's no way to recover them.
* Backups are created as separate ZIP files with all necessary encrypted wallet files.

### Cons:
* Wallet files are now out of reach of the user. So backup is only possible using Monerujo itself to *export* the files, no more easy copy and paste.
* Having no access to the wallet files renders the previous fix for corrupted cache files useless. You will be forced to restore from a backup or start fresh from seed (keeping all funds but losing all notes and subaddresses labels).
* If you uninstall the app, your wallet files are deleted by Android and thus access to your wallets is lost forever. When you reinstall the app, no wallets will automatically appear. You'll have to restore from seed or a previous backup using the CrAzYpass. There's no way to show you a big warning sign before the app is removed.

## Ok, what do I do now?

If you haven't done it already and you haven't updated yet:
1. Make a manual backup of your wallets. Find the files inside the ´monerujo´ folder in your external storage and copy them somewhere safe.
2. Be sure to also write down the wallet's CrAzYpass (wallet recovery password). It's shown in the _secrets_ screen. You get to it by pressing on ⋮ next to each wallet's name on the main screen.

If you are already using the new version (2.x):
1. On the main screen, press the ⋮ next to your wallet's name and choose _Backup_
2. You'll be ask where to save a .zip file containing the wallet's files. You can easily open it anywhere and restore your wallet in another program or in a different Monerujo installation.
3. Write down the wallet's CrAzYpass. The wallet file inside the .zip file will be encrypted with it. You'll need it to restore that wallet anywhere or anytime else.

---
But besides all this, always, please, always...
#### WRITE DOWN YOUR SEED
... because if you keep your seed secure & secret, at the end of the day, your funds are never lost.
