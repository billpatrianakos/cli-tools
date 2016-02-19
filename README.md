# ClI Shortcut Apps

> A collection of useful CLI tools for completing common tasks

## Installing

You can simply move all of the files in this repository to `/usr/local/bin`. Once moved you can just type the name of any program contained in this repo and it'll run.

__Troubleshooting__

If you have any issues using the tools be sure that the files are executable by running `chmox +x program_name` and that the ownership of the files is correct.

## `connect`

Connect is a script for people who run multiple servers and don't want to have to remember IP addresses and don't want their SSH logins tied to a domain name (because we all know domain names change IP addresses all the time).

Connect will log you into a server via SSH by specifying a hostname.

### Usage

Open the file `connect` and fill in the settings variables. You'll enter the default username you use for most of your server, a list of hostnames and their IP addresses, descriptions for each server, and a list of alternate usernames to use for specific hosts. It'll make sense when you open and run the script.

#### Logging into a server

```
connect myhost
```

This will log you into the server you defined as `myhost`. 

#### Override the default username

```
connect myhost myuser
```

#### Use a different public key

You should set any alternate public keys in the settings variables defined in the file.