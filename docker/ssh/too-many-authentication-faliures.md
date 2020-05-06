# Too Many Authentication Faliures

## When you try to login via SSH and are greated by "Received disconnect from 192.168.**.** port 22:2: Too many authentication failures"

---
Use the option
```bash
-o IdentitiesOnly=yes
```

Or you can spend your time allowing/disallowing hosts in your `~/.ssh/config` file.

🤷