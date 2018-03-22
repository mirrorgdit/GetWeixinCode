GetWeixinCode

解决微信OAuth2.0网页授权只能设置一个回调域名的问题
使用方法

    部署get-weixin-code.html至你的微信授权回调域名的目录下

    使用方式类似于直接通过微信回调的方式，只是将回调地址改成了get-weixin-code.html所在的地址，另外省去了response_type参数（因为它只能为code）以及#wechat_redirect（它是固定的），它们会在get-weixin-code.html里面自己加上

    get-weixin-code.html页面从微信那里拿到code之后会重新跳转回redirect_uri里面填写的url，并且在url后面带上code和state

详细示例

    前往微信公众平台->接口权限->网页授权获取用户基本信息->修改，填写授权回调页面域名，例如www.abc.com

    在www.abc.com域名下部署get-weixin-code.html，不一定是根目录，例如：http://www.abc.com/xxx/get-weixin-code.html

    假设你的http://www.xyz.com/hello-world.html这个页面需要获取微信授权，那么你应该使用以下地址来获取授权：http://www.abc.com/xxx/get-weixin-code.html?appid=XXXX&scope=snsapi_base&state=hello-world&redirect_uri=http%3A%2F%2Fwww.xyz.com%2Fhello-world.html

    这样最终就会跳转到这样一个地址：http://www.xyz.com/hello-world.html?code=XXXXXXXXXXXXXXXXX&state=hello-world，从而你就拿到了授权code以及自定义的state参数了

特别感谢

感谢以下朋友为本项目提供的贡献（排名不分先后）

    star769706697

    davidqhr

    tianhe1986

    AnthonyHuang001

    sanzhumu

    q250305917

其他说明

    通过多一次的跳转，解决了微信限制回调域名只能设置一个的问题

    牺牲了一点用户体验，换来了项目部署的美感，不需要将各种项目都部署到一个域名下

    如果你有这样的需求，可以使用本项目

    欢迎提交pull request

    建议先弄懂微信授权回调的流程再使用本项目

    很多朋友问我怎么支持第三方微信平台，这个需要对不同的第三方平台的授权方式有所了解，熟悉他们的授权方式，请求参数等。如果他们是通过在网站入口处的URL上进行授权的，那么可以使用本项目，将入口的URL改成上述的方式，如果他们是在流程中的某些页面去获取授权，那么是没法改变他们的获取地址的，所以本项目就不适用了
