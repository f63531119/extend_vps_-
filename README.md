
# Woiden And Hax Auto Extend <sup>💯</sup>  <img align="right" src="https://img.shields.io/badge/2023.01.10-activity-success"/>

**woiden.id 和 hax.co.id 自动续订**    

`activity` 徽章显示最后执行成功的日期，脚本是否稳定运行，`Github` 是 `UTC` 时区会有时差，一天误差属于正常

> **Note** `Github Action` 运行时所在的服务器IP可能被 `Google` ban 无法使用语音验证，因为公共的服务器被别人用过，IP被识别为机器人，可能上个人刚好也调用了 `Google reCaptcha` ，所以 `Google reCaptcha` 的语音验证调用能否成功随缘，使用 `2Captcha` 和 `YesCaptcha` 的图片验证不受此影响稳如老狗，甚至加载不出来图片也可以验证通过，建议语音图片两个同时使用即稳定也不费钱，或者[托管自己服务器](https://docs.github.com/cn/actions/hosting-your-own-runners/about-self-hosted-runners)，登陆时脚本是先执行语音验证，验证失败再执行图片验证，语音验证频繁调用会被ben ( 没几次就会被ben，不用担心应该就ben一两个小时左右 )，自己服务器使用语音验证最好时间间隔久点


### 环境要求：
 - python：3.9及以上，需要带ssl模块
 - 系统： windwos/macos/debian 11/ubuntu 20+


### 配置文件
文件位置: `config/config.json`，其中参数请自行按照模板更改
``` json
{
  "origin_host": "woiden.id",
  "telegramID_of_hax_or_woiden": "5971007526",
  "password_of_hax_or_woiden": "Zy@19961004",
  "telegram_bot_token_to_send_result": "6035543560:AAFwjubLmjcOiObdkit1k3WZloOf2mCzZdo",
  "telegramID_to_receive_result": "5971007526",
  "pushplus_token_to_send_result": "e21cd7697aa142328a5c0d52fd58a6c1",
  "redis": {
    "host": "redis-18806.c250.eu-central-1-1.ec2.cloud.redislabs.com",
    "username": "default",
    "password": "RFqDKRXheRrqDPz0if1oyeVkRTbllRTl",
    "port": 18806
  },
  "asr_choice": "AZURE",
  "asr_tencent": {
    "secret_id": "AKIDnQp0zCCxUmrhJgqmTwWt1wd5JIH9qLvJ",
    "secret_key": "EF2by72nJadS3PXSDk4A3iAOO9gyPcbv"
  },
  "asr_ibm": {
    "ibm_url": "https://api.us-south.speech-to-text.watson.cloud.ibm.com/instances/7e2f69e7-a5e8-4d56-91ae-f4dc7b4a1f0b",
    "ibm_key": "nblnZuv5E5A_wo5j9eYC-nQVWHKyY5HxJXuEPnNpJgrr"
  },
  "asr_baidu": {
    "app_id": "30453656",
    "api_key": "jubyDhWQZ6FVRXvk2rsiFYaW",
    "secret_key": "ThFn2TyqzV4n9eIG6sOY9LnvDGgT2D0w"
  },
  "asr_azure": {
    "key": "b3ac840c1b24432a897c0f648078ceb8",
    "region": "eastasia"
  },
  "twoCaptcha_api_key": "8349b2ce253f6ddde3805089a26daafa"
}

```


### linux命令执行
```
 1. 配置config/config.json
 2. python3 main.json
```

### docker执行
``` shell
mkdir woiden_extend_temp
cd woiden_extend_temp
# 这里的config.json请自己补充内容
touch config.json

docker run -it --rm  \
    -v $PWD/:/app/config \
    --name woiden_extend_temp \
    mrzyang/woiden_extend:v230219

```