# SFTP with WinSCP to auth with a Password and a Private key

## Description

Normally, an SFTP server requires a Password OR a Private key to connect and authenticate the user. The libraries Linx uses expects this. You can only use a password OR a private key when connecting to an SFTP server through the Linx FTP plugin. However, in rare cases, an SFTP server is set up to require both a Password and a Private key to connect. In order to do this via Linx, this solution uses WinSCP through CommandLine in order to succesfully connect.

This solution should give you a good base to build your project if you need to connect to SFTP with both a password and a private key. Just note that this solution is not complete. No error messages are extracted, but you should be able to extract it easily enough from the text from the CommandLine component.

## Installation

- Both a Linx 5 and Linx 6 solution is added to this Repo. You can download the Free Linx 6 Designer from https://linx.software to try this solution out.
- There's a Setting for the location of your WinSCP.COM file. You'll have to install WinSCP first though. You can download it here: https://winscp.net/eng/download.php
- If you want to set up your own SFTP server, you can Google "OpenSSH Install". Below. however is a couple of config lines you can work with in your sshd_config file, simply comment out what you don't need:

PubkeyAuthentication yes
#PasswordAuthentication yes
AuthenticationMethods "password,publickey"
#AuthenticationMethods "publickey"
#AuthenticationMethods "password"
ChrootDirectory "C:\SFTP"


## Usage

- There are 6 functions provided for:
-- FTPDirectoryCreate
-- FTPDirectoryDelete
-- FTPDownload
-- FTPFileDelete
-- FTPList
-- FTPUpload

Here is a typical ConnectionString you can amend for your own server. The private key data should be read from the file as a string and placed as a whole into the ConnectionString. This JSON is just an example, but you can use Linx Designer to create your connection string using the Field Editor:

{"Type":"SFTP", "Host":"ServerName", "Port":"22", "Timeout":"60", "Authentication":"Basic", "Username":"sftpuser", "Password":"abc123", "PrivateKeys":[{"Data":"PuTTY-User-Key-File-3: ssh-ed25519\nEncryption: none\nComment: sftpuser@ServerName\nPublic-Lines: 2\nABCDC3NzaC1lZDI1NTE6AAAAIH9mtuvKJ/xoUG6YUEeuLADZskOg1ssb4Fj1nOah\nfadn\nPrivate-Lines: 1\nCCCCIEgAFIYtGgfDdCc+VK03oZw+ocIFB3CFiYd3wkWZpWXh\nPrivate-MAC: dfc1277fb3b6de2d3923f5d1414f6f853c2b8474626432d01b769f5f18d31e9e\n"}]}

To learn more commands to use with WinSCP: https://winscp.net/eng/docs/scripting#commands

## Contributing

For questions please ask the [Linx community](https://linx/software/community) or use the [Slack channel](https://linxsoftware.slack.com/archives/C01FLBC1XNX). 

## License

[MIT](https://github.com/linx-software/template-repo/blob/main/LICENSE.txt)
