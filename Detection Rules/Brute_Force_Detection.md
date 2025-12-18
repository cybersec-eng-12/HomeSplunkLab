# Possible Brute Force Attack

## Alert Name: *Multiple Failed Login Attempts*

## Description
- Detects if user has failed to input their password correctly > 3 times.

## Data Source & Identifiers
- Windows Security Log Event ID 4625

### SPL Query:
`index=* EventCode=4625
| stats count by host, user
| where count > 3`

- The `stats` command is to count the amount of times a user on a specific host failed to enter their password correctly. 
- The `where` command filters all results that are <= 3.

# Alert Being Triggered: 



## Viewed Result:


# False Positives:
- User was legitmately trying to gain access but they forgot their password

