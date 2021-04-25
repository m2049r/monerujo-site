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

## How it works from now on:
Form now on, and following upcoming guidelines for Android apps, Monerujo will save your wallet files on the *internal* storage. This storage is encrypted and can be accessed only by the app that created the files. This storage doesn't require any permission from the user, since it cannot read or modify anything else that is not created by this particular app. This storage is technically safer from a security perspective, but it has its quirks. Let's explore them.

### Pros:
* The wallet files are going to be encrypted on top of being already encrypted with the CrAzYpass. Double security!
* No request for authorization to access the storage on first use of the app. Monerujo doesn't care about your other files, it will save its wallets on its own private storage space.
* Removed chance of wallet files being copied, or accesed, or seen by any other app installed on the phone, being them good or evil.

### Cons:
*fgfgh
*fghfgh



## How to backup your wallet
## How to restore your backup
## How to move your wallet to another app
