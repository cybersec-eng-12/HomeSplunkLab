# Defense Evasion IOC

## Alert Name: *Windows Security Event Log Cleared*

## Description
- Alerts if the Windows Secruity log is deleted.

## Data Source & Identifiers
- Windows EventCode 1102.

### SPL Query:
`index=* EventCode=1102
| table _time, host, user`

- The `table` command is to display the most relevant information to the SOC Analyst investigating.

# Alert Being Triggered: 

<img width="2555" height="351" alt="image" src="https://github.com/user-attachments/assets/97005d70-2406-4afb-886d-756c6af42a4f" />

## Query Result:

<img width="2551" height="391" alt="image" src="https://github.com/user-attachments/assets/12c4c76f-573b-4b10-9614-03232793ebaa" />

# False Positives:
- Retention policy had been reached & log is offloaed into a separate database instead of stored locally.

