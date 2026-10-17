# linux-log-analysis
A Blue Team lab documenting Linux log analysis using grep to investigate authentication failures, identify targeted services such as SSH, and analyze suspicious login activity.

## Task: Identify the Service Used by the Attacker

### Objective
Identify which service the attacker used to attempt to gain access to the Linux system by analyzing the authentication logs.

### Investigation
I used the `grep` command to search the `auth.log` file for failed authentication attempts.

```bash
grep "fail" auth.log
```

This command searches for log entries containing the word `fail`, helping me identify unsuccessful login attempts.

**Screenshot 1:** 
![Failed login attempts](screenshots/01-failed-logins.png)

### Findings
After reviewing the authentication log entries, I identified **SSH (Secure Shell)** as the service targeted by the attacker.

SSH allows users to connect to and manage remote systems. Attackers may target this service by attempting to guess passwords or use stolen credentials.

**Screenshot 2:** ![SSH-Evidence]([screenshots/02-ssh-evidence.png)](https://github.com/lenkamokoenaxm-arch/linux-log-analysis/blob/main/Screenshots/ssh-evidence.png)

### Conclusion
By analyzing `auth.log` with `grep`, I identified SSH as the service associated with the attack activity. This exercise demonstrated how Linux command-line tools can help investigate suspicious login attempts.
