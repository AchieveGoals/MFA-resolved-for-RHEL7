# Errata

So far, what works consistently is running ```$ google-authenticator``` without the --secret option; and then 
running the two commands for existing ~/.google_authenticator file

```
$ mv .google_authenticator .ssh
$ restorecon -Rv .ssh
```
