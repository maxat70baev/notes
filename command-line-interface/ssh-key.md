# Setting up SSH Key
```bash
ssh-keygen -t rsa -b 4096 -C "maxat70baev@gmail.com" 
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

## Copy SSH Key
`cat ~/.ssh/id_rsa.pub | pbcopy` - copy SSH key from command line

## Adding or changing a passphrase
**Passphrase**: 19Mxxxxxxxe89
You can change the passphrase for an existing private key without regenerating the keypair. Just type the following command:

```sh
ssh-keygen -p
# Start the SSH key creation process
Enter file in which the key is (/Users/you/.ssh/id_rsa): [Hit enter]
Key has comment '/Users/you/.ssh/id_rsa'
Enter new passphrase (empty for no passphrase): [Type new passphrase]
Enter same passphrase again: [One more time for luck]
Your identification has been saved with the new passphrase.
```

If your key already has a passphrase, you will be prompted to enter it before you can change to a new passphrase.

```sh
The key fingerprint is:
SHA256:XUcdp2wY6jbO5EYrEeQcFTXKD6ySQA4yCaKJ/VMBkYg maxat70baev@gmail.com
The key's randomart image is:
+---[RSA 4096]----+
|*o..++. o.oo+ .oo|
|E=.+.  = + o * .o|
|+ . o . + * o =  |
|   . o . = + o   |
|    o o S B .    |
|     . . O o     |
|        . *      |
|         o       |
|                 |
+----[SHA256]-----+
```