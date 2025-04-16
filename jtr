# John the Ripper

# Automatic Cracking
john --wordlist=/usr/share/wordlists/insertwordlisthere /path/to/file
wget https://gitlab.com/kalilinux/packages/hash-identifier/-/blob/kali/master/hash-id.py for automatic (not 100% accurate) hash identifier
python3 hash-id.py for use

# Format-Specific Cracking
john --format=raw-md5 (or whatever) --wordlist=/usr/share/wordlists/insertwordlisthere /path/to/file

# Format listing
john --list=formats
or
john --list=formats | grep -iF "md5" (or whatever)

# Cracking Windows Authentication Hashes
only change here is to "--format=nt"

# Cracking Hashes from /etc/shadow
STEP 1 : unshadow
unshadow /path/to/shadow /path/to/passwd
EXAMPLE
unshadow local_passwd local_shadow > cracked.txt
FILE 1 - local_passwd
Contains the /etc/passwd line for the root user:
root:x:0:0::/root:/bin/bash
FILE 2 - local_shadow
Contains the /etc/shadow line for the root user: root:$6$2nwjN454g.dv4HN/$m9Z/r2xVfweYVkrr.v5Ft8Ws3/YYksfNwq96UL1FX0OJjY1L6l.DS3KEVsZ9rOVLB/ldTeEL/OIhJZ4GMFMGA0:18576::::::
STEP 2 : cracking
john --wordlist=/usr/share/wordlists/insertwordlisthere --format=sha512crypt (or whatever) cracked.txt

# Single Crack Mode
john --single --format=format /path/to/file
EXAMPLE
john --single --format=raw-sha256 hash.txt

# Cracking Password Protected Zip Files
zip2john [options] [zip file] > [output file]
EXAMPLE
zip2john secure.zip > cracked.txt
john --wordlist=/usr/share/wordlists/insertwordlisthere cracked.txt
(cracked password)
unzip zipfile.zip | input passwd
extract files

# Cracking Password-Protected RAR Archives
rar2john secure.rar > cracked.txt
/opt/john/rar2john secure.rar > cracked.txt 
OR 
rar2john secure.rar > cracked.txt
john --wordlist=/usr/share/wordlists/insertwordlisthere cracked.txt
unrar x secure.rar

# Cracking SSH Key Passwords
ssh2john [id_rsa private key file] > [output file]
EXAMPLE
/opt/john/ssh2john.py id_rsa > cracked.txt
john --wordlist=/usr/share/wordlists/insertwordlisthere cracked.txt
