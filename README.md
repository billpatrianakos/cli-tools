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

### Why is this helpful?

- It turns `ssh me@123.456.78.90` into `connect pluto`. 
- No more remembering IP addresses. 
- No more specifying or remembering alternate .pem files for Azure or AWS: `ssh me@123.456.78.9 -i ~/.ssh/my_special_key.pem` into `connect whatever`
- It'll use the right IP address and default username every time after initial setup
- You can always override the default username with `connect my_server jimmy`

## `rando`

Rando is a random string generator. It's useful for generating secure long strings. Inspect the code yourself before using this in production but generally the strings generated should be damn secure.

### Setup

You need to have the Trollop gem installed to run this program. `gem install trollop` and you're set.

### Usage

Run `rando -h` to get help and options at any time.

```
Options:
  -q, --quick         Generate a quick random string from `SecureRandom.hex`
  -a, --alnum         Use alphanumeric characters only
  -l, --length=<i>    Length of generated string (default: 8)
  -f, --fort-knox     Generate an incredibly long and random string of
                      craziness. Ignores all other options
  -h, --help          Show this message
```

Example use and output

```
rando -q        #=> d658f30a78b8564a8bd0a72f8aef7868
rando -a        #=> iVCnPV3J
rando -a -l 12  #=> 0NUd7h4SOq83
rando -f        #=> &0<x=RsgaLVpPc$az\QY\{GUdZ0vKm[UN!a{EY&!)kUHo|IVd$X>*emkZ2ho*tu%4N#2p*qe{8A6TR@W{WDVo):.VIsr/#Rvb?6Q2uX[@h^`*Bcd<U+1[+W]CNz_P/%pBl-sT3.G$TY~ogT*r~bn:$`Gt<ry4r2t$}d#7O^^<H|N}ID|.2;QHSH5o~eCr.}:US[yPowkv{uh-h<Hn;Zp[Y^:#*}$sUj\+CYT_;^&+K]h\l8ZV<:y/@8cg*#Jg&-r
```