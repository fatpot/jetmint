# jetmint
this is zhangnan's workspace，service for jetmint

##dapp
###airdrop
####1. 版本计划
版本|版本内容|
:---:|:-|
V1.0|用户可快照目标资产对空投资产进行持仓平均发放|
V1.1|添加快照时间与空投时间设定|
V1.2|添加空投活动页<br>领取空投功能（1XYZ一次）|
V1.3|添加空投白名单/黑名单<br>添加空投规则|

#####2. V1.0版本内容
######2.1 操作流程
1.用户选择快照币种（币种调用用户账户资产，但不包括XLM）
2.根据持仓用户数计算手续费(100XYZ/holder)
- 查询持仓用户(holderscount)
- 计算费用holderscount*100XYZ

3.缴纳手续费
- 获取手续费地址(feeaddress)
- 调用萤火dappAPI支付
- 到账check，推送支付结果(checkstatus)

4.选择空投资产，选择空投数量（第一版本按持仓平均空投）
- 调用萤火dappAPI读取用户资产种类与额度

5.空投充值
- 获取空投充值地址(airdropaddress)
- 调用萤火dappAPI支付
- 到账check，推送支付结果(checkstatus)

6.空投


######2.2 函数
########2.2.1 接口：查询持仓用户数，包含balance=0的
    调用范例：https://0.0.0.0/holderscount/?issueaddress=GACUHFTLPN47XYZMPPCFMCQQ...3RHE4FASFDZJPFHMBXYF&assetcode=XYF
 - param str issueaddress:GACUHFTLPN47XYZMPPCFMCQQ...3RHE4FASFDZJPFHMBXYF
 - param str assetcode:XYF
 - param int trustlinecount:30

########2.2.2 接口：获得手续费地址
    调用范例：https://0.0.0.0/feeaddress/
 - param str toaddress:GCFHMPIORCNB5AT6XU...N7U52TXWNJSX4YWSG567
  
########2.2.3 接口：到账check
    调用范例：https://0.0.0.0/checkstatus/?fromaddress=GCFHMPIORCNB5AT6XU...N7U52TXWNJSX4YWSG567&toaddress=GCFHMPIORCNB5AT6XU...N7U52TXWNJSX4YWSG567&amount=1000&hash=c86b3228ffafc5e...61bad5fedce3f5286e5
 - param str fromaddress:GCFHMPIORCNB5AT6XU...N7U52TXWNJSX4YWSG567
 - param str toaddress:GCFHMPIORCNB5AT6XU...N7U52TXWNJSX4YWSG567
 - param float amount:1000
 - param str hash:c86b3228ffafc5e...61bad5fedce3f5286e5
 - param int result:0：成功；1：失败

########2.2.4 接口：获得空投充值地址
    调用范例：https://0.0.0.0/airdropaddress/
 - param str toaddress:GCFHMPIORCNB5AT6XU...N7U52TXWNJSX4YWSG567


