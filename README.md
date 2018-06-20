# ciscoconf

Ciscoconf is a simple shell script which backups the running and the startup configuration of Cisco Routers.
The script uses expect to establish a telnet or ssh connection to a specific Router.
Then it will fetch the current configuration and compare it with the last known config.
The results are saved and send to a list of emails proveded in the maillist file (empty for no mails).
If the configuration has changed, ciscoconf will save the new config in a special folderstructure.

Requires expect and sendmail to be installed on the machine.

# Using ciscoconf

For automation a list of divices can be provided in the divices file.

Format: mode;host;name;passwort;user|(secret-passwort;[user])

Call:
  ./ciscoconf [COMMAND] | mode host name password user|(secret-password [user])

Commands:
  -a,  --all                	backup all devices provided in the devices file

Parameters:
  mode 	telnet, t or ssh, s
  host 	ip address or name of host
  name 	name for the folder
  password 	password
  secret-password   	secret-password for telnet
  user 	username

Examples:
  ciscoconf t myhost1.net myhost1 save saver me
    telnet based bakup of myhost1.net in myhost1/
  ciscoconf s myhost2.net myhost2 save me
    ssh based bakup of myhost2.net in myhost2/
