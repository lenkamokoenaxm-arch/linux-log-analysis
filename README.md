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
[Screenshots/Failed Login Attempts.png](https://github.com/lenkamokoenaxm-arch/linux-log-analysis/blob/abf41a01c3aa01df959a4b86e1775a4ecc6e22e5/Screenshots/Failed%20Login%20Attempts.png)

### Findings
The investigation identified SSH (Secure Shell) as the suspected service of interest based on the sshd entries found in auth.log. The logs showed errors involving port 22, which is commonly used by SSH. However, these errors do not confirm that the attacker successfully gained access through SSH. Further authentication log evidence would be required to confirm successful access..

SSH allows users to connect to and manage remote systems. Attackers may target this service by attempting to guess passwords or use stolen credentials.

**Screenshot 2:** [Screenshots/ssh-evidence.png](https://github.com/lenkamokoenaxm-arch/linux-log-analysis/blob/4dcca05ca615605b5e211af4e6667e88af017bc9/Screenshots/ssh-evidence.png)

### Conclusion
By analyzing `auth.log` with `grep`, I identified SSH as the service associated with the attack activity. This exercise demonstrated how Linux command-line tools can help investigate suspicious login attempts.
