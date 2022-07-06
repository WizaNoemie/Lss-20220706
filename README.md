# VLESS-heroku  Trojan-heroku
## Deploy VLESS and Trojan server on heroku

## Do not promote any website

# 部署提示

|**注意事项**|
|:---------|
|**如果能继续使用的，请保持低调！！！**|
|**选择不向任何网站转传是为了更长久的相聚，愿你能发现墙外美好而又有趣的地方。**|
|**带有删除线的部分表示不适用或已经废弃。**|
|**自2021.11.18起不再部署caddy，改为单一部署以减少项目大小，提高项目稳定性，不保证本项目有被封的可能。**|

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/WizaNoemie/Lss-tro-20220706.git)

# VLESS Client Setup

|Connection Variables|Values|
|:------------------:|:----:|
|**`Address`**|yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy IP|
|**`SNI`**|none|
|**`AllowInsecure`**|false|
|**`Port`**|443|
|**`Host`**|yourAppName.herokuapp.com </br> Cloudflare Reverse Proxy Domain Name|
|**`Path`**|/$ID-vless|
|**`id`**|Generate using UUID generator or V2RayN/V2RayNG client generate</br>[uuidgenerator](https://www.uuidgenerator.net/)|
|**`Flow`**|none|
|**`encryption`**|none|
|**`Transport`**|ws|
|**`Tls`**|Tls must open, otherwise your network was insecure!|

# Trojan Client Setup
|Connection Variables|Values|
|:------------------:|:----:|
|**`Address`**|yourAppName.herokuapp.com</br>Cloudflare Reverse Proxy IP|
|**`SNI`**|Cloudflare Reverse Proxy Domain Name|
|**`Port`**|443|
|**`Host`**|yourAppName.herokuapp.com</br>Cloudflare Reverse Proxy Domain Name|
|**`Path`**|/$ID-trojan|
|**`password`**|Generate using UUID generator or V2RayN/V2RayNG client generate</br>[uuidgenerator](https://www.uuidgenerator.net/)|
|**`Transport`**|ws|
|**`Tls`**|Tls must open, otherwise your network was insecure!|

# Client Ws+Tls+Xtls-rprx-direct(Flow) Support Status
|**Client**|**Status**|
|:--------:|:--------:|
|**`2dust V2RayN`**</br>**`2dust V2RayNG`**|Ws+Tls+Flow|
|**`OpenWrt SSRPlus`**|Ws+Tls|
|**`OpenWrt Passwall`**|Ws+Tls|
|**~~`QV2Ray`~~**|~~Ws+Tls~~|

# Trojan Ws+Tls Support Status
|Client|Support Trojan ws+tls?|
|:----:|:--------------------:|
|**`2dust V2RayN`**</br>**`2dust V2RayNG`**|No, Please use VLESS ws+tls|
|**`OpenWrt SSRPlus`**|Yes|
|**`OpenWrt Passwall`**|Yes, Use latest passwall|

# Cloudflare Reverse Proxy Code (Choose one from both examples)

example 1
```
addEventListener(
  "fetch", event => {
    let url = new URL(event.request.url);
    url.host = "appname.herokuapp.com";
    let request = new Request(url, event.request);
    event.respondWith(
      fetch(request)
    )
  }
)
```

example 2
```
const SingleDay = 'appname.herokuapp.com'
const DoubleDay = 'appname.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname="appname.herokuapp.com";
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```

example 3
```
const Day0 = 'app0.herokuapp.com'
const Day1 = 'app1.herokuapp.com'
const Day2 = 'app2.herokuapp.com'
const Day3 = 'app3.herokuapp.com'
const Day4 = 'app4.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        let day = nd.getDate() % 5;
        if (day === 0) {
            host = Day0
        } else if (day === 1) {
            host = Day1
        } else if (day === 2) {
            host = Day2
        } else if (day === 3){
            host = Day3
        } else if (day === 4){
            host = Day4
        } else {
            host = Day0
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```

# Acknowledgments

- [Project V](https://github.com/v2fly/v2ray-core.git)
- [Project X](https://github.com/XTLS/Xray-core.git)
- [HeroKu](https://heroku.com)
- [heroku-vless](https://github.com/DanyTPG/heroku-vless.git)
- [CloudflareSpeedTest](https://github.com/XIU2/CloudflareSpeedTest.git)
- [Better Cloudflare IP](https://github.com/badafans/better-cloudflare-ip.git)

# Important information

New users only need to modify the id

Abuse is strictly prohibited, I am not responsible for all problems arising from abuse, and use and cherish!

This project is not suitable for long-term use over the wall.

For security reasons, please use cdn instead of custom domain names to achieve VLESS+WS+TLS.

It is forbidden to promote this project on any website!!!!
