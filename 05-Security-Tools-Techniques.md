
# Cracking password with Hashcat

## Installating Hashcat

- Installation,

$ sudo apt-get update

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/03e5a016-b670-49a7-98c2-4602b25b27a0)

$ sudo apt-get -y install hashid hashcat wget

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/e0f3b014-312a-4d2d-8b33-28c60022283f)


- New directory is created 

$ mkdir hashed
$ cd hashed

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/b40bbb99-ce67-4563-81b6-7f2718f16e78)

- Rockyou dictionary is added

$ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz

$ tar xf rockyou.txt.tar.gz

$ rm rockyou.txt.tar.gz

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/117931b6-b1ec-4a2e-a56d-dbf116a2aff7)


$ head rockyou.txt

$ wc -l rockyou.txt 


![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/976272db-977a-4198-bae8-6ba44fdcd5b2)


## Identify Hash Type

Hashcat needs to know the type of the hash to crack, first we need to analyse the hash

$ hashid -m 6b1628b016dff46e6fa35684be6acc96

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/1f3ac921-a764-429f-ab18-f1352657391c)


## Crack the Hash

$ hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/9d4c58e8-4dc1-497a-ae62-cc5392e5ad9a)


At the end we can request the password 

$ cat solved

Password is : summer

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/bb0aedd8-b2ed-490c-9b50-2808f78c44eb)

Else we can use -show to display the password.

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/bf726630-b0d5-4273-ada9-c4e3ee6efec9)



# Password managers

For people and businesses looking to improve security, privacy, and ease of use while managing their online accounts and passwords, password managers are essential resources. 
By offering a consolidated and safe password management solution, they lessen the need for shoddy or frequently used passwords and strengthen cybersecurity posture overall.

- Popular Password Managers

1. LastPass
2. Dashlane
3. 1Password
4. Bitwarden
5. KeePass


## Bitwarden

### Threats it defends against: 

Bitwarden defends against a number of threats, including keylogging, brute force attacks, and phishing scams. 
By ensuring that users may generate and save complicated, one-of-a-kind passwords for every account, it lowers the possibility of password reuse.
Information that is encrypted:

Passwords, notes, and other sensitive data kept in the vault are all encrypted by Bitwarden. 
Because encryption is end-to-end, Bitwarden cannot access the stored data and only the user has access to the decryption key.


### Licences:

Bitwarden can be obtained through the open-source GNU GPLv3 license. 
The source code may be viewed, altered, and disributed by users under this license, encouraging openness and community involvement.

### Storage of data:

Bitwarden provides self-hosted and cloud-based solutions. 
Data is encrypted and stored on Bitwarden's servers, which are spread across multiple global locations, for the cloud option. 
Bitwarden places a high priority on privacy and security compliance.
Additionally, users have the option to self-host Bitwarden, giving them total control over data storage and access by hosting the program on their own servers.

### Data security:

Bitwarden uses AES-256 encryption to safeguard user information while it's in transit and at rest. 
It also makes use of zero-knowledge encryption, 
  which ensures that Bitwarden cannot acess the user's master password or any decrypted data because all encryption and decryption operations take place locally on the user's device.
Bitwarden significantly improves account security by supporting two-factor authentication (2FA).


## Getting started as an individual user

1. Create an Account
Use your email (ex. thomas@emailprovider.com) to create an account through the Bitwarden self-registration page.
https://vault.bitwarden.com/#/register

2. Create your Master Password
On the create your account screen, you will be prompted to set up a Master Password (https://bitwarden.com/help/master-password/) which you will use to access your vault.
Be sure to store this somewhere securely as Bitwarden can not reset it for you.
Use the Bitwarden Password Generator (https://bitwarden.com/password-generator/) to help create a strong password or a memorable passphrase.

3. Get to know your vault
Your personal vault consists of logins, cards, identities, and secure notes.
These are collectively known as items.

4. Install the browser extension
Downloading the Bitwarden browser extension will enable you to take advantage of keyboard shortcuts and make your most common tasks a breeze!
Use Ctrl/CMD + Shift + L to autofill. Press the shortcut again to cycle through any other matching logins.

It's best to disable the browser's built-in password manager to ensure that Bitwarden is always your go-to password manager.

5. Import your passwords
Why start from scratch? Within your vault tools, you can import data such as previously saved passwords from a wide variety of other password managers or browsers.

6. Start creating new items
The easiest way to to get familiar with creating new items is to create a login.
When using the browser extension, navigate to the site you'd like to save the login for, then select the + Add Item button. You can use the Bitwarden Username and Password Generator to generate a complex password based on your preferences.


# Compile John the Ripper, Jumbo version

## Install prerequisites

$ sudo apt-get update
$ sudo apt-get -y install micro bash-completion git build-essential

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/a1f34418-dd33-494f-b721-887d42562464)

## Download John the Ripper, 

$ git clone --depth=1 https://github.com/openwall/john.git

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/7aa28760-2655-42c5-af38-3b49ec8573f8)

$ cd john/src/	
$ ./configure

Configure will detect the environment and create a Makefile for 'make' command.

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/9e8bb52b-be33-421e-affb-b0ecea2985e6)


But there were some errors

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/78281d21-200f-4e62-b616-4f013c703914)

So I install the development package 

$ sudo apt-get install libssl-dev

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/d40c2e92-16c5-4202-a0c7-194189e5b3f5)

Then ran the configuration again

$ cd john/src/	

$ ./configure

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/69e64184-e7dc-46b5-a018-5c6b5f6234b2)

Then it showed "Configured for building John the Ripper jumbo:"

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/0ddea192-6b8b-4068-a959-b20ad8670bb8)


Then compile

$ make -s clean && make -sj4

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/547f2588-2908-4153-ac89-437855d73f77)


![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/26753096-f6a7-4f8e-a070-56898e26a156)

Once John is compiled, we can find the new executables and scripts in run/.

$ cd ../run/
$ ls -1

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/0eb145a6-9f43-4333-9a5f-e39ad51e79ec)

Now it is running

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/285a67a7-c70c-4a74-8cd4-6744e74074ba)



## Crack ZIP Password

Download a sample zip file 

$ wget https://TeroKarvinen.com/2023/crack-file-password-with-john/tero.zip

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/8a4415d1-5135-4334-940f-7d9f615bd516)


Try to open it.As we don't know the password we can't open it

$ unzip tero.zip 

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/6b915aea-ac16-4962-8a7f-6f785e6f3c86)


## Cracking the ZIP password 

This is a two step process. 
First, extract the hash into a new file called tero.zip.hash.

$ ./zip2john tero.zip >tero.zip.hash


Then, let John perform a dictionary attack against the hash.

$ ./john tero.zip.hash 

But then I got stuck

![image](https://github.com/Ruwan0127/rumarkdown/assets/144318600/3cffffa3-6f9c-426e-967b-1894b5944964)





# Reference

1. https://www.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/10_chap02.html#chap02-sec003
2. https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
3. https://bitwarden.com/learning/getting-started-as-an-individual-user/
4. https://terokarvinen.com/2023/crack-file-password-with-john/
5. https://stackoverflow.com/questions/3016956/how-do-i-install-the-openssl-libraries-on-ubuntu
   



