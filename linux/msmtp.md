# msmtp

`msmtp` is a commandline smtp client that reads the message body from stdin.

## configuration

You need to first install `msmtp` with the package manager of your choice.  
After installing, create a confi file. `msmtp` looks for those in `$XDG_CONFIG_HOME/msmtp`. The config file simply needs to be called `config`.  
Here's a sample configuration file which you can edit:
```
defaults
auth on
tls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
logfile /home/{user}/.config/msmtp/msmtp.log

account {account1}
host {smtp hostname}
port 465
from {from field}
user {smtp username}
passwordeval "gpg --quiet --for-your-eyes-only --no-tty --decrypt $XDG_CONFIG_HOME/msmtp/.msmtp-{account1}.gpg"
# only if your smtp server doesnt support STARTTLS
#tls_starttls off

# vim:filetype=msmtp
```
The last line exists to make vim highlight the configuration file with the right syntax. Feel free to remove it if you want.  
Make sure you replace all your occurances of:
- `{user}` - the username you are logged in to on your computer
- `{account1}` - a string you have to reference later to select that profile
- `{smtp hostname}` - the hostname of your smtp server
- `{smtp username}` - the username you log in with on the given smtp server

## usage

Using `msmtp` is very simple. Supply the body of the message via stdin, set a subject via the `-s` flag, set the account to use via the `-a` flag and send it to the email supplied at the very end.
