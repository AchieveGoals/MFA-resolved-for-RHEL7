# Phase I - get it working

## Add line to /etc/pam.d/sshd
```auth required pam_google_authenticator.so secure=~/.ssh/.google_authenticator nullok```

## Notes

In Phase I: 
- all users will require a ~/ssh folder with standard .ssh permissions
- all users will copy and re-register .google_authenticator to be sure SELinux allows access

In Phase II:
- Once all users have MFA enabled, comment out "auth substack password-auth" as recommended

