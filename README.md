# MTopSdkSMS.Core
阿里大于短信发送(只有短信发送功能，其他功能移除)
## 说明
根据官方topsdk修改，支持.net core，去除除了短信之外的其他功能
## 使用说明
            ITopClient client = new DefaultTopClient(url, Appkey, Appsecret);
            AlibabaAliqinFcSmsNumSendRequest req = new AlibabaAliqinFcSmsNumSendRequest();
            req.Extend = Extend;                                                       //公共回传参数，在“消息返回”中会透传回该参数；
            req.SmsType = "normal";                                                    //短信类型，传入值请填写normal
            req.SmsFreeSignName = SmsFreeSignName;                                          //短信签名
            req.SmsParam = _template;                 //短信模板变量
            req.RecNum = _phoneNo;                                                      //短信接收号码
            req.SmsTemplateCode = SmsTemplateCode;                                       //短信模板ID
            AlibabaAliqinFcSmsNumSendResponse response = client.Execute<AlibabaAliqinFcSmsNumSendResponse>(req);
            if (response.Result == null)
            {
                return GetErrorMsg(response.SubErrCode);
            }
            else
            {
                return response.Result.Success.ToString();
            }
