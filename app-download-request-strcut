## 请求体协议

主要基于JceStruct封装而成，这是腾讯系APP的主要的二进制序列化结构

nodejs实现参考：https://github.com/takayama-lily/jce

## 请求交互步骤

* 1.请求获取RSA密钥

* 2.查询有效的APP任务

* 3.提交完成APP任务动作

## 基本结构（展开后的）

举例getTasksReq

```text
{ // need encoded struct reqdata
 fm: seqNo, // seqNo
 fw: 4, // 固定为4
 fx:{ // need encoded adConf reqdata
    cJ: 1,
    cX: 0,
    as: adConf.guid,
    cY: 'b26527',
    // cZ: undefined,
    cw: 6015,
    da: 1,
    db: -1,
    dc: -1,
    // dd: null
  },
  fy: [
       { //  need encoded struct  cmddata
      dO: 5110, // cmdid
      fm: 3,
      fo:  { //  need encoded struct busdata //  encrypt and compressed
        S:  { //  need encoded struct  userinfo
          ap: { //  need encoded struct  productInfo
            ae: productInfo.coin_productId,
            af: productInfo.coin_version
          },
          aq: user.accountId,
          ar: user.loginKey,
          as: adConf.guid,
          at: ''
        },
        Z: [productInfo.coin_unkown3] // productInfo
      },
      ft: 0,
      fp: 4294967296 // 未知固定
       }
   ]
}
```
详细参考代码中的调用
