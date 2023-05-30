# MFA-resolved-for-RHEL7
Interim and Final MFA for SSHD setup using google-authenticator on RHEL7

## Basics plus changes to let remote SSH work with SELinux Enforcing mode
Most users just type ```$ google-authenticator``` which places file in ~/.google_authenticator with perms 0600.

However, for SSH, you'll see SELinux, when Enforcing, does not let this file to be updated as it is in the user's home directory.

You can discovery more if you use SELinux commands like
  ```$ sudo semanage fcontext -l | grep 'unconfined_u:object_r:ssh_home_t' ```
that have a line for SSHD such as:
  ```/home/[^/]+/\.ssh(/.*)?    all files   unconfined_u:object_r:ssh_home_t:s0```
  
As recommended in referenced issue response below in Google GA repo issue 101, if the user has already created their
.google_authenticator file, then follow these two steps before trying to remote SSH again to the same user:

```
  $ cd
  $ mv .google_authenticator .ssh/
  $ restorecon -Rv .ssh/
  ... you will see comment about "Relabeled /home/user/.ssh/.google_authenticator"
```

Alternatively, if GA has not been used as of yet, run GA command following your site's recommended answers, and using your iPhone or Android mobile device with a GA app (or other OTP apps):

```
  $ google-authenticator --secret=~/.ssh/.google_authenticator
  
```
Then attempt remote SSH access to this server again. 

## References

[Liked this answer](https://github.com/google/google-authenticator-libpam/issues/101#issuecomment-557267513) <Solution to resolve SELinux sshd permissions issues - failed to update secret file: Permission denied>
