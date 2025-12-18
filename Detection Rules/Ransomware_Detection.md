# Possible Ransomeware Indicator of Compromise(IOC)

## Alert Name: Shadow Delete Command Attempt

## Description
- Detects execution of vssadmin.exe attempting to delete volume shadow copies.
- This is a common precoursor to ransomeware encyrption.
- Attackers do this in order to prevent restoration from any previous file/folder versions.

## Data Source & Identifiers
- Sysmon Event ID 1 -> Used to identify a process creation on the system.
- vssadmin command
- "delete" flag followed 
- "shadows" inside of the path

### SPL Query:
`index=* source="*Sysmon*" EventCode=1 CommandLine="*vssadmin* *delete* *shadows*" | table _time, host, ParentUser, CommandLine`

The table command is to display relevant information to the SOC Analyst investigating this alert. Reasons why each were included:
- _time -> the time the command was run
- host -> the machine running the command
- ParentUser -> user who initiated this command
- CommandLine -> entire command that was run

### False Positives: Legitimate backup software may trigger this.

# Alert Being Triggered: 

<img width="2546" height="268" alt="image" src="https://github.com/user-attachments/assets/35f62015-6740-4607-a353-e97eb4d044c7" />

## Viewed Result:

<img width="2558" height="384" alt="ransomeware_resullt" src="https://github.com/user-attachments/assets/f05030dc-2684-4c70-9893-abfb6e81615d" />
