# Python DNSBrute

A simple DNS subdomain brute-force and enumeration tool written in Python using the `dnspython` library.

The tool reads a wordlist, combines each entry with a target domain, and attempts to resolve valid subdomains.

## Features

- DNS subdomain enumeration
- Custom wordlist support
- Lightweight and simple Python code
- Uses the `dnspython` library
- Includes a common subdomain wordlist in the repository
- Displays valid subdomains and their resolved IP addresses

## Requirements

- Python 3
- dnspython

## Installation

Clone the repository:

```bash
git clone https://github.com/gemelligabriel/python-dnsbrute.git
```

Enter the project directory:

```bash
cd python-dnsbrute
```

It is recommended to create a Python virtual environment:

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

Install the required dependency:

```bash
pip install dnspython
```

## Usage

Open the Python file and set the target domain:

```python
alvo = "example.com"
```

Then run the tool:

```bash
python3 dnsbrute.py
```

The script will test the subdomains contained in the wordlist and display the ones that successfully resolve.

Example output:

```text
www.example.com -> 192.0.2.1
mail.example.com -> 192.0.2.2
api.example.com -> 192.0.2.3
```

## Wordlist

This repository includes a common subdomain wordlist that can be used directly with the tool.

The included wordlist contains common names such as:

```text
www
mail
admin
api
dev
test
staging
vpn
portal
server
```

You can also replace the included wordlist with your own custom wordlist.

The script expects the wordlist file to be located in the same directory as the Python script:

```python
arquivo = open("wordlist.txt", "r")
```

This allows the project to work regardless of where the repository is located on the system.

## How It Works

The tool follows a simple process:

1. Loads the wordlist.
2. Reads each possible subdomain.
3. Combines the subdomain with the target domain.
4. Attempts to resolve the DNS `A` record.
5. Prints the subdomain and IP address when the DNS resolution succeeds.

For example:

```text
Wordlist entry:
admin

Target:
example.com

Generated subdomain:
admin.example.com
```

If the DNS resolution is successful, the tool displays the result.

## Example Code

```python
import dns.resolver

res = dns.resolver.Resolver()

arquivo = open("wordlist.txt", "r")
subdominios = arquivo.read().splitlines()

alvo = "example.com"

for subdominio in subdominios:
    try:
        sub_alvo = subdominio + "." + alvo
        resultado = res.resolve(sub_alvo, "A")

        for ip in resultado:
            print(sub_alvo, "->", ip)

    except:
        pass
```

## Project Structure

```text
python-dnsbrute/
│
├── dnsbrute.py
├── wordlist.txt
├── README.md
└── requirements.txt
```

## requirements.txt

The project uses the following dependency:

```text
dnspython
```

You can install all dependencies with:

```bash
pip install -r requirements.txt
```

## Disclaimer

This project was created for educational purposes and cybersecurity learning.

Only use this tool against systems, domains, and environments that you own or have explicit authorization to test.

The author is not responsible for misuse of this software.

## Author

Gabriel Gemelli

Cybersecurity Student | Pentesting | Red Team | Python
