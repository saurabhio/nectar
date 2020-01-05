### Sitemap
```
https://www.google.com/ping?sitemap=https://www.example.com/sitemap.xml
https://www.bing.com/ping?sitemap=https://www.example.com/sitemap.xml
```

### WLAN
```
netsh wlan set hostednetwork mode=allow ssid=anyname key=12345678
netsh wlan start hostednetwork

netsh wlan stop hostednetwork
netsh wlan show hostednetwork
```

### Email Authenticity

Open Original Message of the email,

- In **Received field**, check domain name and IP address 
- In **Received-SPF** field, check pass
- In **Authentication-Results** field, check **spf=pass** and **dkim=pass**


