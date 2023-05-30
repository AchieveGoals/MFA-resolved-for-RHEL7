# Phase I - enable SSH to request One Time Password (OTP)

## Add line enable OTP
1. If present, comment out ChallengeResponseAuthentication no
2. Add ```ChallengeResponseAuthentiucation yes```

## Notes
Especially /etc/ssh/sshd_config, I follow and apply many Linux system hardening conventions that I will not reveal here.  Follow your Linux distro's recommendation, but always start with what you are protecting, from whom, and deny everything else but each type of access you want.

## TODO

- Again, Phase I is minimum changes to get it working.  
