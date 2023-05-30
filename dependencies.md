# Using MFA (One-Time-Password) to get Initial System Access 

Any standard operating procedures (SOPs) in this repository are fully dependent on Red Hat Enterprise Linux, version 7.9, at least through March 2024.

We make use of Google's Github repo google-authenticator and RHEL's PAM.d / SSHD configuration settings.

Users will rely on having a .ssh folder to meet the minimum SELinux settings for V1.

On Google's GA Issue 101, there was talk of having a protected .config/[usage-subfolder] for GA, YubiKey, etc. Other than supporting GA and SSH access to these servers, all other considerations in Issue 101 are out of scope for this RHEL 7.9 focused repo.

## References
[SELinux Perms Error Solved] (https://github.com/google/google-authenticator-libpam/issues/101#issuecomment-557267513)
  - see Github/Google/google-authenticator recommendation by "jdbarnes-isi" Nov 21, 2019
I won't re-test on RHEL7-equivalent:  Fedora, CentOS, etc.  Left as exercise for Interested.

## Issues faced

1. Red Hat has not backported google-authenticator to RHEL7.  There are multiple articles and blogs to perform RHEL9 - that is out of scope.

2. My primary SOP testing is Ubuntu Fossa 20:04, RHEL 7.9 and Alma 9 Cloud

3. SELinux permission errors need to be addressed when you solve everything else

4. My focus is on secured SSH access with MFA for least privileged user (and deny privileged user any SSH access)


# TO DO

- Repeat MFA expansion via sudo which is only available to privileged users that the least priv-user must "su - adminuser" before being eligible for sudo

/Tim @ AchieveYourNextGoal
