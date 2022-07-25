# near-shardnet
创建云主机：
![image](https://user-images.githubusercontent.com/52590741/180730203-15a960a8-b27b-4153-aa34-df388dedb281.png)
设置安全组：
![image](https://user-images.githubusercontent.com/52590741/180730241-c4effe0c-91a8-40ae-a842-58e358cf83a7.png)
设置环境变量脚本：
![image](https://user-images.githubusercontent.com/52590741/180730335-b4468a47-ed8f-4b79-b4eb-9dbf0a25affb.png)
执行
重新下载 config.json 和 Genesis.json
删除旧的文件
![image](https://user-images.githubusercontent.com/52590741/180730353-8584dae2-ba58-4607-a6cc-09701086cb5a.png)
![image](https://user-images.githubusercontent.com/52590741/180730366-9aceb44d-7391-4fb4-9d2e-711c63f1652e.png)
执行：
./neard --home ~/.near run
![image](https://user-images.githubusercontent.com/52590741/180730406-62834750-bb6d-454b-8f00-11d83ccef496.png)

打开新窗口执行 near login：
根据提示打开网页
![image](https://user-images.githubusercontent.com/52590741/180732208-8b595965-1926-40b7-8aa7-03f4b04c948f.png)
链接完成以后，near login 会中断，并成功
![image](https://user-images.githubusercontent.com/52590741/180732291-bf2fa4e3-5e0d-47fd-98f7-daf97fa92e6f.png)
设置 validator 文件
![image](https://user-images.githubusercontent.com/52590741/180732344-d8fabcaa-6f4e-48df-85e2-9016df6be723.png)
查看当前validator文件内容 
![image](https://user-images.githubusercontent.com/52590741/180732405-f2a8f7f2-8663-4d4e-b501-322c36c24a21.png)
重新执行 near run
![image](https://user-images.githubusercontent.com/52590741/180732448-b72c6274-dcf4-46a7-979a-39bfdbfb7dfc.png)
执行near call factory.shardnet.near create_staking_pool '{"staking_pool_id": "<pool id>", "owner_id": "<accountId>", "stake_public_key": "<public key>", "reward_fee_fraction": {"numerator": 5, "denominator": 100}, "code_hash":"DD428g9eqLL8fWUxv8QSpVFzyHi1Qd16P8ephYCTmMSZ"}' --accountId="<accountId>" --amount=30 --gas=300000000000000
Pool ID: Staking pool name, the factory automatically adds its name to this parameter, creating {pool_id}.{staking_pool_factory} Examples:
If pool id is stakewars will create : stakewars.factory.shardnet.near
Owner ID: The SHARDNET account (i.e. stakewares.shardnet.near) that will manage the staking pool.
Public Key: The public key in your validator_key.json file.
5: The fee the pool will charge (e.g. in this case 5 over 100 is 5% of fees).
Account Id: The SHARDNET account deploying and signing the mount tx. Usually the same as the Owner ID.
![image](https://user-images.githubusercontent.com/52590741/180733132-2928e04f-c458-469d-a60c-6c2c8bc9d52d.png)
返回查看 near 启动日志，会发现现在已经开始提示 validator 了 
![image](https://user-images.githubusercontent.com/52590741/180733237-c916c65f-dc69-4585-9d55-f22e545d1d64.png)
查看节点状态：
curl 127.0.0.1:3030/status
<img width="555" alt="image" src="https://user-images.githubusercontent.com/52590741/180733353-f46b2edb-caa5-484a-8564-1bb14a4ee6ce.png">
