# Face-IPC-FSH

####运行前提
1. Redis


#### 介绍

Face-IPC-FSH 是 OSCHINA 推出的基于 Git 的代码托管平台（同时支持 SVN）。专为开发者提供稳定、高效、安全的云端软件开发协作平台
无论是个人、团队、或是企业，都能够用 Gitee 实现代码托管、项目管理、协作开发。企业项目请看 [https://gitee.com/enterprises](https://gitee.com/enterprises)}

#### 软件架构
软件架构说明
1. 设备发送心跳，主动访问心跳接口
2. 设备从心跳返回信息判断是否有操作指令
    a. 有指令则主动访问请求指令接口，执行完指令判断是否有返回信息:
        Stop&&Stop==1   Result
    b. 执行完指令集，返回空指令。
3. 下发操作指令：
    a. 指令放入redis 设置过期时间
    b. 把指令前缀放入定期Map中
    c. 更新心跳信息，设置通知过期时间
4. 设备访问心跳接口：
    a. 在通知有效期内访问,获取通知，更新命令通知心跳信息时间。
    b. 主动访问指令接口。
5. 设备访问指令接口：
    a. 删除操作指令通知信息（清空命令请求）
    b. 判断是否为操作指令执行返回信息，
        i. 是则将返回结果信息放入redis 设置过期时间
        ii. 不是则执行指令集中的指令，无指令则下发空串。
     
    


#### 安装教程

1.  xxxx
2.  xxxx
3.  xxxx

#### 使用说明

1.  xxxx
2.  xxxx
3.  xxxx

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request


#### 特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  Gitee 官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解 Gitee 上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是 Gitee 最有价值开源项目，是综合评定出的优秀开源项目
5.  Gitee 官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  Gitee 封面人物是一档用来展示 Gitee 会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)
