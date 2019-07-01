# PasswordStore

This page helps configure [pass tool](https://www.passwordstore.org/)

## Setup gpg key
* Execute following command and use all default options but 4096 bits long.
!!! warning
    When prompted for it, enter the password of you gpg key. It will be your master password.
```bash
gpg2 --full-gen-key
```

## Configure pass
* Get gpg key id from following command
!!! information
    GPG id is not in uid part but in sec for gpg2. 
```bash
gpg2 -k
```

* Initialise pass store with your gpg-id
```bash
pass init "<gpg-id>"
```

* Initialise git repository
```bash
pass git init
pass git remote add origin git@github.com:<github_account_id>/pass-store.git
pass git push --set-upstream origin master
```

## Export/Import gpg key
* Export key
```bash
gpg2 --export-secret-keys > secret.gpg
```
* Import key
```bash
gpg2 --import secret.gpg
```

## Synchronize Android phone

* Download [OpenKeychain: Easy PGP](https://play.google.com/store/apps/details?id=org.sufficientlysecure.keychain)
* Download [password store android app](https://play.google.com/store/apps/details?id=com.zeapo.pwdstore)
* Download gpg key on phone and setup OpenKeychain with it
* Setup password store to pull from git repository and select imported gpg key from precedent step

## Setup web browser
* Follow installation instructions [here](https://github.com/browserpass/browserpass-native#configure-browsers)
* Install and configure extension [here](https://github.com/browserpass/browserpass-extension)
