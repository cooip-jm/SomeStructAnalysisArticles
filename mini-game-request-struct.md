## 请求体协议

主要基于protobuf封装而成的二进制序列化结构

nodejs实现参考：https://github.com/protobufjs/protobuf.js

protoc工具可参考：https://github.com/protocolbuffers/protobuf

## 请求结构示例
```protobuf
# c.proto

syntax = "proto3";

message a {
    string key = 1;
    string value = 2;
}

message b {
    string method = 1;
    int32 iv = 2;
}

message JudgeTimingBusiBuff {
  int64 Seq = 1;
  string qua = 2;
  string deviceInfo = 3;
  JudgeTiming busiBuff = 4;
  string traceid = 5;
  string Module = 6;
  string Cmdname = 7;
  LoginSig loginSig = 8;
  b Crypto = 9;
  int32 Extinfo = 10;
  int32 contentType = 11;
}

message GetAppInfoByLinkBusiBuff {
    int64 Seq = 1;
    string qua = 2;
    string deviceInfo = 3;
    bytes busiBuff = 4;
    string traceid = 5;
    string Module = 6;
    string Cmdname = 7;
    LoginSig loginSig = 8;
    b Crypto = 9;
    int32 Extinfo = 10;
    int32 contentType = 11;
}

message d {
    int32 Seq = 1;
    int64 retCode = 2;
    bytes errMsg = 3;
    bytes busiBuff = 4;
    repeated a Extinfo=5;
}


message LoginSig {
    string uin=1;
    string sig=2;
    string platform=3;
    int32 type=4;
    string appid=5;
    string openid=6;
    bytes sessionkey=7;
    repeated a Extinfo=8;
}

message q2b {
    repeated a mapInfo = 1;
    string attachInfo = 2;
}
 
// mini_app_growguard - JudgeTiming
message JudgeTiming{
    q2b extInfo = 1;
    string appid = 2;
    int32 factType = 3; // 12  13
    int32 duration = 4; 
    int64 reportTime = 5; 
    int32 afterCertify = 6;
    int32 appType = 7;
    int32 scene = 8;
    int32 totalTime = 9;
    string launchId = 10; 
    string via = 11; 
    int32 AdsTotalTime = 12; 
    string hostExtInfo = 13;
}

// mini_app_info - GetAppInfoByLink
message GetAppInfoByLink {
    string link = 1;
    int32 linkType = 2; 
}
```
