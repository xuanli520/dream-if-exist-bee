# 梦想赞助家 v0.11

这是一个原生微信小程序餐饮项目，覆盖门店首页、点餐下单、扫码点餐、外卖配送、自提取餐、排队取号、订单支付、会员中心、优惠券、积分、储值卡等业务能力。项目接口主要通过 `apifm-wxapi` 对接远程后台，不是离线可独立运行的纯前端仓库。

## 技术栈

- 原生微信小程序
- `apifm-wxapi`
- `@vant/weapp`
- `wxbarcode`

## 功能范围

- 首页与导流：轮播、会员中心、优惠券、储值卡、门店介绍、多语言切换
- 门店与点餐：定位选店、分类商品列表、连续滚动点餐、商品详情、SKU、多配件、时段价格、秒杀、拼团
- 下单与支付：购物车、立即购买、优惠券抵扣、会员卡抵扣、微信支付、余额支付、配送费、预约时间、备注、提货点
- 堂食与自提：扫码点餐、桌号场景、取餐码、扫码核销
- 履约与订单：订单列表、订单详情、进行中订单、配送信息、联系门店
- 会员运营：会员中心、余额、充值记录、提现记录、积分签到、积分日志
- 营销能力：优惠券领取/兑换、优惠买单、会员卡购买/转赠/领取/兑换
- 其他能力：预约报名、意见反馈、商家入驻申请

## 目录结构

```text
.
├─app.js
├─app.json
├─config.js
├─components/
├─i18n/
├─images/
├─miniprogram_npm/
├─pages/
├─utils/
├─project.config.json
└─project.private.config.json
```

## 页面分组

- Tab 页面：`pages/home/index`、`pages/index/index`、`pages/queue/index`、`pages/order-details/doing`、`pages/my/index`
- 点餐交易：`pages/goods`、`pages/goods-details`、`pages/cart`、`pages/pay`、`pages/all-orders`、`pages/order-details`
- 门店地址：`pages/shop`、`pages/ad`、`pages/about`
- 会员资产：`pages/member-center`、`pages/asset`、`pages/coupons`、`pages/score`、`pages/sign`
- 卡券买单：`pages/card`、`pages/youhui-pay`
- 其他页面：`pages/notice`、`pages/booking`

## 关键配置

`config.js` 当前包含以下本地接入配置：

- `subDomain`
- `merchantId`
- `customerServiceType`

`app.js` 启动后会从远程后台读取并缓存一批运行时配置，包括但不限于：

- `mallName`
- `share_profile`
- `shop_goods_split`
- `QQ_MAP_KEY`
- `create_order_select_time`
- `packaging_fee`
- `customerServiceChatCorpId`
- `customerServiceChatUrl`
- `alipay`
- `share_pic`
- `tihuodianOpen`

这些配置未准备好时，登录、地图、支付、客服、提货点等能力会受到影响。

## 本地开发

1. 使用微信开发者工具导入仓库根目录。
2. 确认 `project.config.json` 与本机开发环境兼容。
3. 根据自己的后台环境修改 `config.js` 中的 `subDomain` 和 `merchantId`。
4. 确认后台已配置支付、门店、地图、客服、分享图、预约时间等运行时参数。

## 开发注意事项

- 这是原生微信小程序，不要按 `uni-app`、`Taro`、`Vue` 项目方式改造。
- 新增或移动页面时，必须同步更新 `app.json`。
- 业务文案和语言切换依赖 `i18n/`，文案改动要同步检查中英文资源。
- `miniprogram_npm/` 为依赖产物，除非明确需要，不要直接手改。
- 支付、登录、门店、配送、会员卡等流程都依赖微信环境和远程后台配置。
- `project.private.config.json` 是本地覆盖配置，不应当作团队公共配置来源。
