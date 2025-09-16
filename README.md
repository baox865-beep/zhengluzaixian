# wxcloudrun-express

[![GitHub license](https://img.shields.io/github/license/WeixinCloud/wxcloudrun-express)](https://github.com/WeixinCloud/wxcloudrun-express)
![GitHub package.json dependency version (prod)](https://img.shields.io/github/package-json/dependency-version/WeixinCloud/wxcloudrun-express/express)
![GitHub package.json dependency version (prod)](https://img.shields.io/github/package-json/dependency-version/WeixinCloud/wxcloudrun-express/sequelize)

å¾®ä¿¡äºæç®¡ Node.js Express æ¡æ¶æ¨¡çï¼å®ç°ç®åçè®¡æ°å¨è¯»åæ¥å£ï¼ä½¿ç¨äºæç®¡ MySQL è¯»åãè®°å½è®¡æ°å¼ã

![](https://qcloudimg.tencent-cloud.cn/raw/be22992d297d1b9a1a5365e606276781.png)

## å¿«éå¼å§

åå¾ [å¾®ä¿¡äºæç®¡å¿«éå¼å§é¡µé¢](https://cloud.weixin.qq.com/cloudrun/onekey)ï¼éæ©ç¸åºè¯­è¨çæ¨¡æ¿ï¼æ ¹æ®å¼å¯¼å®æé¨ç½²ã

## æ¬å°è°è¯
ä¸è½½ä»£ç å¨æ¬å°è°è¯ï¼è¯·åè[å¾®ä¿¡äºæç®¡æ¬å°è°è¯æå](https://developers.weixin.qq.com/miniprogram/dev/wxcloudrun/src/guide/debug/)

## å®æ¶å¼å
ä»£ç åå¨æ¶ï¼ä¸éè¦éæ°æå»ºåå¯å¨å®¹å¨ï¼å³å¯æ¥çåå¨åçææãè¯·åè[å¾®ä¿¡äºæç®¡å®æ¶å¼åæå](https://developers.weixin.qq.com/miniprogram/dev/wxcloudrun/src/guide/debug/dev.html)

## Dockerfileæä½³å®è·µ
è¯·åè[å¦ä½æé«é¡¹ç®æå»ºæç](https://developers.weixin.qq.com/miniprogram/dev/wxcloudrun/src/scene/build/speed.html)

## é¡¹ç®ç»æè¯´æ

```
.
âââ Dockerfile
âââ README.md
âââ container.config.json
âââ db.js
âââ index.js
âââ index.html
âââ package.json
```

- `index.js`ï¼é¡¹ç®å¥å£ï¼å®ç°ä¸»è¦çè¯»å API
- `db.js`ï¼æ°æ®åºç¸å³å®ç°ï¼ä½¿ç¨ `sequelize` ä½ä¸º ORM
- `index.html`ï¼é¦é¡µä»£ç 
- `package.json`ï¼Node.js é¡¹ç®å®ä¹æä»¶
- `container.config.json`ï¼æ¨¡æ¿é¨ç½²ãæå¡è®¾ç½®ãåå§åéç½®ï¼äºå¼è¯·å¿½ç¥ï¼
- `Dockerfile`ï¼å®¹å¨éç½®æä»¶

## æå¡ API ææ¡£

### `GET /api/count`

è·åå½åè®¡æ°

#### è¯·æ±åæ°

æ 

#### ååºç»æ

- `code`ï¼éè¯¯ç 
- `data`ï¼å½åè®¡æ°å¼

##### ååºç»æç¤ºä¾

```json
{
  "code": 0,
  "data": 42
}
```

#### è°ç¨ç¤ºä¾

```
curl https://<äºæç®¡æå¡åå>/api/count
```

### `POST /api/count`

æ´æ°è®¡æ°ï¼èªå¢æèæ¸é¶

#### è¯·æ±åæ°

- `action`ï¼`string` ç±»åï¼æä¸¾å¼
  - ç­äº `"inc"` æ¶ï¼è¡¨ç¤ºè®¡æ°å ä¸
  - ç­äº `"clear"` æ¶ï¼è¡¨ç¤ºè®¡æ°éç½®ï¼æ¸é¶ï¼

##### è¯·æ±åæ°ç¤ºä¾

```
{
  "action": "inc"
}
```

#### ååºç»æ

- `code`ï¼éè¯¯ç 
- `data`ï¼å½åè®¡æ°å¼

##### ååºç»æç¤ºä¾

```json
{
  "code": 0,
  "data": 42
}
```

#### è°ç¨ç¤ºä¾

```
curl -X POST -H 'content-type: application/json' -d '{"action": "inc"}' https://<äºæç®¡æå¡åå>/api/count
```

## ä½¿ç¨æ³¨æ
å¦æä¸æ¯éè¿å¾®ä¿¡äºæç®¡æ§å¶å°é¨ç½²æ¨¡æ¿ä»£ç ï¼èæ¯èªè¡å¤å¶/ä¸è½½æ¨¡æ¿ä»£ç åï¼æå¨æ°å»ºä¸ä¸ªæå¡å¹¶é¨ç½²ï¼éè¦å¨ãæå¡è®¾ç½®ãä¸­è¡¥å¨ä»¥ä¸ç¯å¢åéï¼æå¯æ­£å¸¸ä½¿ç¨ï¼å¦åä¼å¼åæ æ³è¿æ¥æ°æ®åºï¼è¿èå¯¼è´é¨ç½²å¤±è´¥ã
- MYSQL_ADDRESS
- MYSQL_PASSWORD
- MYSQL_USERNAME
ä»¥ä¸ä¸ä¸ªåéçå¼è¯·æå®éæåµå¡«åãå¦æä½¿ç¨äºæç®¡åMySQLï¼å¯ä»¥å¨æ§å¶å°MySQLé¡µé¢è·åç¸å³ä¿¡æ¯ã


## License

[MIT](./LICENSE)
