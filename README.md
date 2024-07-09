# Blockscout-example

## 简介

该项目是自用的Blockscout浏览器

官方可以查看以下地址：

[Blockscout示例浏览器地址](https://eth.blockscout.com/)

[Blockscout浏览器文档](https://docs.blockscout.com/)

[Blockscout浏览器Github地址](https://github.com/blockscout/blockscout)

## 项目构建

1. 在服务器上使用git拉取该项目 或使用  `rz ` 命令上传该项目文件

2. 进入  `docker` 目录，执行 `vim Makefile` 命令修改docker image名字

   ![](/readme/makefile.png)

3. 执行 `make build` 命令生成docker image

4. 打开服务器上的 `/blockscout-example` 文件夹

   （ps：如果没有 从把该项目的下的 `explorer` 文件夹拷贝过来）

5. 修改 `docker-compose.yaml`  和 `docker-compse-db.yaml` 文件

   （ps：`docker-compse-db.yaml` 文件是配置 postgres 数据库的文件）

   将 `docker-compose.yaml` 文件中的image 替换成刚刚打包好的镜像

6. 进入 `envs` 文件夹修改 `common-blockscout.env` 文件

   （ps：具体修改查看修改配置文件）

7. 执行命令启动 docker image

   启动命令：`docker-compose up -d`

   停止命令：`docker-compose down`

8. 执行 `docker ps` 命令查看image是否正常启动

   正常启动在浏览器输入 `http://服务器IP:4000` 查看浏览器页面


## 修改配置文件

##### 注意：

配置文件是外挂，修改配置文件后重启镜像即可

修改代码、添加修改logo图片等需要重新打包镜像



##### 以下是常修改的配置文件参数，更多参数修改请查阅Blockscout文档

| 参数                       | 示例                                                        | 备注                                       |
| -------------------------- | ----------------------------------------------------------- | ------------------------------------------ |
| ETHEREUM_JSONRPC_HTTP_URL  | http://10.0.0.1:8545                                        | 节点地址                                   |
| DATABASE_URL               | postgresql://postgres:@10.0.6.142:7432/blockscout?ssl=false | 数据库地址                                 |
| ETHEREUM_JSONRPC_TRACE_URL | http://10.0.0.1:8545/                                       | 节点地址                                   |
| NETWORK                    | Chain                                                       | 标题                                       |
| SUBNETWORK                 | Eth                                                         | 标题                                       |
| LOGO                       | /images/blockscout.svg                                      | 头部logo                                   |
| LOGO_FOOTER                | /images/blockscout.svg                                      | 底部logo                                   |
| BLOCKSCOUT_HOST            | explorer.xxx.com                                            | 域名，直连节点使用IP:端口号(10.0.0.1:4000) |
| BLOCKSCOUT_PROTOCOL        | https                                                       | 直连节点用http                             |
| BLOCKSCOUT_VERSION         | 1.0                                                         | 底部版本号                                 |
| BLOCKSCOUT_DESCRIPTION     | Blockchain explorer for……                                   | 底部文字                                   |
| API_URL                    | https://explorer.xxx.com                                    | 直连节点                                   |

