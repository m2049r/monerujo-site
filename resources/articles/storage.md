# Where Monerujo stores your wallets

Since version 2.0.3 'Puginarug' Monerujo changed the place where it saves your wallets files. Let's break it down:

## How it was before:
Until now, wallets were saved in the *external storage* the apps on your phone use for all the files or stuff you produce in them. For example, that's the place your camera app stores the photos you take. This regular storage has no particular protection, and technically every app has access to every file that's in there. That's how you can install two different audio players, and they can find the same stored mp3 songs. That's also why Monerujo (and any other app that works with files) needed to ask for your permission to "Access your files and photos." when you install it for the first time. Monerujo needed your permission to save stuff on that storage.

When Monerujo creates a new wallet or restores a previous one, it creates a couple of files with that wallet's name, and encrypts the sensitive one of them with the CrAzYpass. [You can read more about it on this article](https://anhdres.medium.com/how-monerujos-crazypass-crazy-secure-password-scheme-works-dc4f99a99ff0). But basically the CrAzYpass is a crazy secure password made up of a combination of the password you choose, and an identifier of the phone. It is very long and impossibly hard to crack, so your funds were very safe, even though they were on this easily accesible storage.

### Pros:
* Files were easily accesible. If you wanted to backup them, you just needed to open a file browser app on your phone or connect it to a computer with your USB cable, look for the monerujo folder, and copy them from there.
* If a wallet file got corrupted, [it was trivial to just go there and delete the cache file](https://anhdres.medium.com/how-to-solve-a-corrupt-wallet-file-with-monerujo-19fc621b1f2d).
* Files were not deleted when you uninstalled the app. That meant that if you reinstalled Monerujo, the wallets were magically there. You only had to know their matching CrAzYpasses.

### Cons:
* Wallet files couldn't be cracked open without the matching CrAzYpass, but they could be deleted or corrupted with ease by any malicious app on the phone.
* When users opened the app for the first time, they got presented with a request for access to the "Files and photos" storage. That sounded like way more than Monerujo needs, and was a source of suspicion from the anybody not familiarized with the inner workings of Android.
* From Android 11 and onwards, apps are required to not use this storage anymore, so this method wasn't future-proof.
* Files were not deleted when you uninstalled the app. Which meant that users could believe that traces of Monero usage dissapeared with just removing the app, while the wallet files remained on the external storage.
* Wallets couldn't be properly deleted from the app. They were merely archieved because files remained in the storage. Even if deleted, Monerujo couldn't assure you they were actually out of the capabilities of a special recovery program.

## How it works from now on:
Form now on, and following upcoming guidelines for Android apps, Monerujo will save your wallet files on the *internal* storage. This storage is encrypted and can be accessed only by the app that created the files. This storage doesn't require any permission from the user, since it cannot read or modify anything else that is not created by this particular app. This storage is technically safer from a security perspective, but it has its quirks. Let's explore them.

### Pros:
* The wallet files are going to be encrypted on top of being already encrypted with the CrAzYpass. Double security!
* No request for authorization to access the storage on first use of the app. Monerujo doesn't care about your other files, it will save its wallets on its own private storage space.
* Removed chance of wallet files being copied, or accesed, or seen by any other app installed on the phone, being them good or evil.
* In case of need, wallets can be actually deleted from within the app, and since they were encrypted, there's no way to recover them.

### Cons:
* Wallet files are now out of reach of the user. So backup is only possible using Monerujo itself to *export* the files, no more easy copy and paste.
* Having no access to the wallet files renders the previous fix for corrupted cache files useless. You will be forced to restore from a backup or start fresh from seed (keeping all funds but losing all notes and subaddresses labels).
* If you uninstall the app, your access to the wallet files is lost forever. When you reinstall the app, no wallets will automatically appear. You'll have to restore from seed or a previous backup. This is a problem because there's no way to put a big notice in front of you when you remove the app.

## Ok what do I do now?

If you haven't done already and you haven't updated yet:
1. Make a manual backup of your wallets. Find the files inside the _monerujo_ folder in your external storage and copy them somewhere safe.
2. Be sure to also write down the wallet's CrAzYpass (wallet recovery password). It's shown in the _secrets_ screen. You get to it by pressing on ⋮ next to each wallet's name on the main screen.

If you already are in the new version:
1. On the main screen, press the ⋮ next to your wallet's name and choose _Backup_
2. You'll be ask where to save a .zip file containing the wallet's files. That .zip file will be unencrypted, so you can easily open it anywhere and restore your wallet in another program or in a different Monerujo installation.
3. Copy the wallet's CrAzYpass. The wallet file inside the .zip file will be encrypted with it. You'll need it to restore that wallet anywhere or anytime else.

---
But besides it all, always, please, always...
#### WRITE DOWN YOUR SEED
... because if you keep your seed secure & secret, at the end of the day, all is never lost.
