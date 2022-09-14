# 微信云托管·微信支付演示DEMO

## 项目介绍

此示例使用「微信云托管」微信支付实现了从付款到退款的整个闭环基础操作流程。

## 部署步骤

- 将项目下载，使用小程序开发者工具导入，appid填写已认证的非个人小程序
- 按照[此指引](https://developers.weixin.qq.com/miniprogram/dev/wxcloudrun/src/guide/weixin/pay.html)将微信支付商户号授权给小程序，然后获得小程序绑定的子商户号。
- 将绑定的商户号写入 `/server/index.js` 第7行，替换`1XXXXXXXX`。
- 在「微信云托管控制台」云调用打开开放接口服务，参照[此指引](https://developers.weixin.qq.com/miniprogram/dev/wxcloudrun/src/guide/weixin/open.html)。
- 将项目下 `/server` 文件夹上传，部署到微信云托管中，服务名称为`pay`；具体可以参照[此指引](https://developers.weixin.qq.com/miniprogram/dev/wxcloudrun/src/quickstart/custom/)中的部署步骤。
- 获取上一步部署的微信云托管服务名称，以及环境ID，填入 `/miniprogram/pages/index/index.js` 的153行。
- 完成。

- web文件夹展示的是公众号H5发起支付的整体例子，使用前需要配置正确的APPID和环境ID，并上传至服务号网页域名下运行（开发者工具不支持模拟H5支付，只能真机来调试）

## 技术原理

- 服务端使用微信云托管开放接口服务，免令牌
- 客户端使用本地存储来维护订单的持久性
- 支付相关的接口都是使用最简易的输入，扩展数据需要自行开发
- 为了防止用户恶意请求，可以使用header头 `x-wx-source` 来判断微信真实来源

## 注意事项

- 本项目只是用于演示，所以接口直接对应支付事项，仅用于代码交流
- 如果你要开发业务，请结合自身业务逻辑自行拼接订单业务
- 如果你想更改服务名称，需要注意在 `/miniprogram/pages/index/index.js` 的157行更改服务名称。
- server服务中在支付、退款回调参数里，是从header中获取的当前服务名称填入的，在调试时可以在云托管日志中看到回调的内容。

## 作者信息

- zirali李冠宇
