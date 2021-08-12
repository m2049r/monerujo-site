---
layout: resource
---

# Mystical Monerujo Manual

---
## How to…

### How to get your wallet back if you have your seed

1. Click on the + button on the main screen.
2. Choose *Restore wallet 25 word seed*.
3. Choose a name and password for you wallet.
4. Enter your 25 word mnemonic seed.
5. Enter a restore height or a date you’re sure it’s prior to the wallet’s creation, otherwise some transactions may not appear on your transactions list.
6. Click on *MAKE ME A WALLET ALREADY*
7. Done. Monerujo will need to sync your wallet (scan the blockchain for transactions belonging to you). Duration will be proportional to how far away in time you’re making it check for them.

### How to send bitcoins or other cryptocurrencies with the moneroj on your wallet

Monerujo has the [SideShift.ai](https://sideshift.ai) exchange service integrated in the app. At the moment, it allows you to trade XMR for BTC, LTC, ETH, DASH, or DOGE. This mean that you can for example pay for a service online that doesn't accept Monero, but does some of the other currencies, without leaving the app.

1. Open a wallet. It will make you wait until it’s fully synced.
2. Click on *GIVE*
3. You need to provide the receiver’s address now. You can either paste a Bitcoin, Litecoin, Ethereum, Dash, or Dogecoin address or scan a QR code. It will let you know that you’ve entered one, what's the selected destination currency, and that the conversion is going to be handled by SideShift.ai
4. Click on *AMOUNT*
5. Enter the amount you want to send. You can choose to do this in any of the other currencies by switching the ticker button.
6. Click *CONFIRM*
7. It will prepare your transaction. Once it’s ready, it will display its details. If everything looks right, just click on *SPEND MY SWEET MONEROJ*

### How to create a completely new wallet

1. On the main screen, click on the + button.
2. Click on *Create new wallet*
3. Choose a name for your wallet. This is how it will be called everywhere in the app. You can change this later.
4. Enter a password. Monerujo will ask for it to allow access to the wallet, sending funds, or see its secret details.
5. Choose between using fingerprint access or not. This is less safe (somebody could use your thumb while you sleep) but more convenient. Risk assessment is a very personal task.
6. Click on MAKE ME A WALLET ALREADY!
7. Monerujo will display the details screen. It's very important that you write down the Mnemonic Seed. This list of random words give you (or anybody with it) the power to recreate this wallet in Monerujo or any other standard Monero wallet. Don't copy and paste it on your phone. Write it down physically and store it somewhere both safe and secret.
8. Optionally you can also write down the Restore Height and the Restore Password. These may come in handy if you need to backup or troubleshoot a wallet corruption. Convenient but not critical like the Mnemonic Seed.
9. Click on I HAVE NOTED THE MNEMONIC SEED. You'll be taken back to the main screen and the newly created wallet should be there. 

### How to make a backup of your wallet

1. On the main screen, click on the dots menu next to your wallet's name.
2. Click on *Backup*
3. Monerujo will open your phone's file browser and ask for a destination folder and suggest a filename. Once you press *SAVE* it will create and save a zip file with your wallet's files in it, on that location.

Please remember that the zip file will be encrypted with your *Wallet Files Restore Password* also known as *CrAzYpass*. If you haven't written it down before, you can find it on the secrets screen of your wallet. Please write it down as it's very helpful to recover past backups.

Please also be aware that the backup is for that specific wallet. If you have more than one, you'll need to make a separate backup with specific restore passwords for each.

### How to restore a backup of your wallet

1. On the main screen, click on the dots menu at the top right of your screen.
2. Click on *Import wallet*
3. Monerujo will open a file browser asking for you wallet's backup zip file. Find and select yours.
4. If everything goes well, it should take you back to the main screen, and you should see a new wallet there, with the name of your backup wallet.

If you're using the same device and Monerujo installation that you used to create the backup, you will be able to open the wallet with your chosen password just as if nothing happened. But in case you switched devices or uninstalled Monerujo in between, you'll need the *Wallet Files Restore Password* to open your wallet again, and being able to change the password to one of your liking. You can find that password on the wallet's secrets screen. Please write it down when you make a backup.

---

## FAQ…

### Why does Monerujo ask for access to my external storage?

Monerujo will need your permission to create files on your phone if you create a manual backup of your wallet files, and then it will have to read from them to restore them. If you're not making or restoring backups, that permission is not necessary.

### Why does Monerujo ask for access to my camera?

The app needs permission from you to turn on the camera to scan QR codes. That feature can be very useful to send money to another wallet without having to copy and pasting address "manually". This is not a critical permission.

### What is the CrAzYpass?

The CrAzYpass or *Wallet Files Restore Password* if the password Monerujo uses to encrypt your wallet files on you phone. It's very long and crazy secure, and generated when you create your wallet in Monerujo. The magic trick is allowing you to open the wallet and spend funds from it with the easier human-friendly password you choose, while encrypting the wallet files with that secure password, so anyone with access to your wallet files can't brute force them.

You should write the CrAzYpass down along with your mnemonic seed when you create a new wallet, since it's useful to restore your wallet in a future Monerujo installation, or take it to any other standard Monero wallet, and carry your transaction notes, and subaddresses and accounts labels with you.

You can find this restore password on the secrets screen of each wallet, by clicking on the wallet's dots menu and choosing *Show Secrets!*
