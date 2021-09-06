# Hyperledger Fabric框架

### 1.1背书节点和账本

```yaml
###fabric中的背书策略，要完成一笔交易，这个交易的过程就是背书策略，安装链码时需要指定背书策略好，交易提案会发送给组织a和组织b的节点。
Organizations :
- &OrdererOrg
    Name:
 #每个节点都有一个账本，默认把账本数据存储到levelDB中
```

### 2配置fabric网络

##### 2.1fabric的核心模块

|    模块名称    |        功能        |
| :------------: | :----------------: |
|      peer      | 存储数据，维护链码 |
|    orderer     | 排序节点，交易打包 |
|   cryptogen    | 组织和证书生成模块 |
|  configtxgen   | 区块和交易生成模块 |
| congfigtxlator | 区块和交易解析模块 |

###### 2.1.1证书的生成cryptogen.yaml



```yaml
OrdererOrgs:							## 定义管理orderer节点的组织
  - Name: Orderer					## 这个组织的名字叫 Orderer
    Domain: example.com		## 这个组织的根域名是 example.com 
    
    # 生成证书的时候，证书内会包含Name和Domain信息,orderer.example.com就是这个组织的地址
    
    EnableNodeOUs: true		## 如果设置了 EnableNodeOUs ，就在msp下生成config.yaml文件
    
    # 对于一个Spec来说，配置了CommonName，那么文件夹则命名为CommonName
    # 如果没有配置CommonName，则文件名为：{{.Hostname}}.{{Domain}}
    # 在下面的例子中,在 crypto-config/ordererOrganizations/example.com/orderers 目录下
    # 则会产生两个文件orderer.test.com和orderer5.test.com，
    # 如果没有加CommonName，则目录名为order.example.com与order5.example.comn
    Specs:
      - Hostname: orderer
        CommonName: orderer.test.com
      # - Hostname: orderer2
      # - Hostname: orderer3
      # - Hostname: orderer4
      - Hostname: orderer5
        CommonName: orderer5.test.com

PeerOrgs:											## 定义管理peer节点的组织
  - Name: Org1								
    Domain: org1.example.com	
    EnableNodeOUs: true
  	
  	# Template是按照Template模板生成多个文件，数量由Count决定，起始编号由Start决定
  	# 如下配置会在crypto-config/peerOrganizations/org1.example.com/peers目录下，
  	# 生成两个文件，分别是 peer0.org1.example.com 和 peer1.org1.example.com
  	# 如果把Start注释去掉，那么会生成 peer5.org1.example.com 和 peer6.org1.example.com
    Template:
      Count: 2
      # Start: 5
      
    # Users是生成除了Admin之外多少个user，数量由Count决定
    # 对于orderer组织，这个值设置了也没有效果
    # 如果配置会在crypto-config/peerOrganizations/org1.example.com/users目录下，
    # 生成两个文件，分别是Admin@org1.example.com和User1@org1.example.com
    # 如果改为2，那么会多一个User2@org1.example.com
    Users:
      Count: 1
	
		# 如下如果在这里加入一个Specs，那么会在peers目录下生成3个文件了
		# 包括，peer0.org2.example.com, peer1.org2.example.com 和 test.org2.example.com
  - Name: Org2
    Domain: org2.example.com
    EnableNodeOUs: true
    # Specs:
    #  - Hostname: test
    Template:
      Count: 2
    Users:
      Count: 1

```

