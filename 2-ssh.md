# SSH

## Set up SSH keys for Github

The use of SSH is to allow two computers to talk over the Internet.

* Everything's encrypted
* Unlike HTTPS, not only works between server and browser

## SSH Command

```{bash}
ssh {user}@{host}
```

### Bash commnad mentioned:

* `ls`
* `mkdir`

### Common use cases of SSH:

* Connect to Github; pull, clone, push, etc.
* Remotely access a computer
* SSH into a server; needs to learn how to set up a server for SSH connections

## Saving the day through SSH

### Command flow

To clone a github repo:

```{bash}
ssh root@<ip_address>
sudo apt-get install git
git clone git@github.com:<ssh_repo_info>
git clone git@github.com:<https_repo_info>
```

To install npm:

```{bash}
sudo apt-get install nodejs
nodejs -v
npm install <package>
```

Copy everything in a folder onto the server:

```{bash}
cd <source_folder>
rsync -av . root@<ip_address>:<destination_folder>
```

### Additional Resources

* [Rsync (Remote Sync): 10 Practical Examples of Rsync Command in Linux](https://www.tecmint.com/rsync-local-remote-file-synchronization-commands/)
* [AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

## How SSH Works

Encryption techniques:

* Symmetrical encyption
* Asymmetrical encryption
* Hashing

### Symmetrical encyption

* Use the same, **secret key** to encrypt and decrypt a message.
* Problem: anyone who has the key can view the message
* Solution: Key exchange algorithm
* Secret key is specific to each SSH session and is generated prior to Kline's authentication

### Asymmetrical encryption

* Use the **public key** to encrypt data and **private key** to decrypt data; essentially a *one-way relationship*
* Only used for key exchange algorithm to share secret (public) keys at the beginning of each SSH connection
* Deffie Hellman Key Exchange

### Additional Resources

* [Secret Key Exchange (Diffie-Hellman) - Computerphile](https://www.youtube.com/watch?v=NmM9HA2MQGI)
* [Diffie Hellman -the Mathematics bit- Computerphile](https://www.youtube.com/watch?v=Yjrfm_oRO0w)
* [Key Exchange Problems - Computerphile](https://www.youtube.com/watch?v=vsXMMT2CqqE)
* [Elliptic Curves - Computerphile](https://www.youtube.com/watch?v=NF1pwjL9-DE)

## Hashing

* To deal with the man-in-the-middle issue, someone faking to be the client or host during the session
* A one-way funciton never meant to decrypt anything
* Can help the host and the client verify each other during the SSH session
* HMX: Hash-based Message Authentication codes
  * Each message transmitted must contain Mac
  * Mac is a hash generated from symmetric key, the package sequence number, and the message content that was sent
  * Since both have the information, each can generate the hash, match the hash, and verify the integrity of the message transmitted


## Passwords Or SSH?

Process so far:

1. Diffie-Hellman Key Exchange
2. Arrive at Symmetric Key
3. Verify hashes
4. **Authenticate user**

How to authenticate a user?

* SSH into a server and still use passwords
* Set up SSH for the server and SSH as the user

### Set up SSH

First go to the SSH folder on your computer:

```{bash}
cd ~/.ssh
ls
```

Then generate a key:

```{bash}
ssh-keygen -C "<email>"
```

This will generate two files:

* `id_rsa.pub`: public key; can share with anyone to encrypt the message
* `id_rsa`: private key; NEVER EVER EVER share this

