# DNS-Server
NITKPCのLANで使えるDNSServerです。

## DNS設定方法
volumes/config/hosts に IP DOMAIN の形式で入力すればOKです。  
```例: 192.168.10.53 example.com```  
hostsに記載されていないドメインは```1.1.1.1```に対して解決を要求します。  
また、ホットリロードが有効ですので設定変更後コンテナの再起動は必要ありません。  

## 注意
本DNSサーバーは53/udp,tcpで受け付けるよう設定しているため、  
システムがデフォルトで使用しているDNSリゾルバとlistenするポートが衝突します。  
```
#/etc/systemd/resolved.conf
[Resolve]
DNSStubListener=no
```
こちらの設定を行ってDNSリゾルバのlistenを停止させてください。 
また、簡易サーバーですのでセキュリティ対策等はガバガバです(多分)  
公開されたネットワーク上での利用は推奨しません。


