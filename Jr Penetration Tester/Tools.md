# Tools

Short descriptions of the tools I use in these notes.

## Nmap
Network scanner. Finds open ports on a host and identifies the services
and versions behind them. Used at the start of almost every engagement.

Flags I use:
- `-p-` scan all 65535 ports
- `-sV` detect service versions
- `-sC` runs Nmap's default scripts, pulling extra details (banners, auth methods, etc.)
- `-oN ("file.name")` saves the output to a file, good habit for reporting later


## Gobuster
Brute-force tool for web paths. Takes a wordlist, requests each word as a URL
and reports the ones that exist. Used to find hidden pages and directories.

Flags I use:
- `dir` directory mode
- `-w` wordlist
- `-x` extra file extensions

## curl
Command-line HTTP client. Sends a request to a URL and shows the raw response,
without a browser hiding the details. Used to check headers, test endpoints
and send custom requests.

Flags I use:
- `-I` headers only
- `-s` silent mode, hides the progress output
- `-b "NAME=value"` send a cookie, so the request is made as a logged-in user

## grep
Searches text for lines that match a pattern. I pipe the output of other
commands into it to keep only the lines I care about.

Example:
- `curl -s <URL> | grep "fw-semibold"` shows only the lines that contain the profile data

## Netcat (nc)
Simple tool for reading and writing data over network connections. Used here
as a listener to catch an incoming reverse shell.

Flags I use:
- `-l` listen mode (wait for a connection instead of making one)
- `-v` verbose, prints connection info
- `-n` skip DNS resolution (use IPs only, faster)
- `-p` port to listen on

Note: the listener and the command that triggers the shell must run in two
separate terminals. The listener blocks the terminal it's running in while it waits.


## searchsploit
Command-line tool to search Exploit-DB's offline database of public exploits
and vulnerability disclosures. Faster than Googling when you already roughly
know what you're looking for, and works without internet access since the
database is stored locally.

Usage:

`searchsploit <keyword>`