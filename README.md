## stableJPY 稳定日元项目

# 在多边形上发布稳定日元币技术路线图

# 多边形LAYER2 侧链 概念

- 可以把以太坊比作为操作系统，侧链类比于在操作系统上构造的虚拟机 
- 比如WINDOS系统里面 安装了 VMWARE 然后再 VMWARE 里面安装了 LINUX WINDOWS操作系统
- 虚拟机类似于一个子进程，在子进程里面又跑了一套操作系统

# 如何同步？

- 虚拟机里面自己有一套CONCENSYS 的算法称为 DPOS， DPOS 里面又有 ZK-rollup 和 plasma 运行同步算法的是另外一批人（并非以太坊矿工）

# 以太坊和多边形通讯问题

- 类似进程之间通信问题，通过同步信号量等复杂逻辑（这里就不 一一赘述，学过操作系统的同学应该懂）

# 怎么把以太坊上的代币 映射到 多边形

- <https://docs.polygon.technology/docs/develop/ethereum-polygon/pos/mapping-assets>
- 根本不需要在多边形上重新写代码，只需要把在以太坊上的TOKEN 按照上述文档映射过来即可
- 他会自己生成一个CHILDTOKEN然后把以太坊上的TOKEN合约映射过来。
- <https://mapper.polygon.technology/> 可以在这里搜索查询一下 USDC USDT POS 桥合约怎么写的 <https://polygonscan.com/address/0x7ffb3d637014488b63fb9858e279385685afc1e2#code>

# 多边形 以太坊 代币映射原理

- 主链与侧链之间代币转换可以看作 农行和工行转账的过程
- 1，农行在工行开立存款账户（所谓的在以太坊上的多边形桥）
- 2，工行在农行开立存款账户（在多边形上的以太坊桥）
- 3，一旦以太坊上的TOKEN要转到多边形来
- 4，TOKEN进入桥中LOCKED住，多边形这边调用CHILD合约的Deposit方法存入用户的钱包
- 5，用户提款到以太坊，多边形这边调用WITHDRAW，以太坊那边的合约将用户资产释放给用户

# 代币的属性会变码？分红类，通缩类，动物币

- 不会，因为这边的代码是通过代理合约实现，实际上主链上代币的ABICODE都已经包括进来了。
- 所以，这里的代币属性和以太坊上的是一模一样的。转账销毁，添加流动性，或者分红。但是要注意的是，代币里面调用了UNISWAP等LP地址的合约。都无法在多边形使用了。


## 怎么将日元稳定币映射到SOLANA上

# <https://portalbridge.com/#/transfer> 使用虫洞直接将ERC20代币映射到SOLANA上来，原理类似多边形

- 按照操作步骤将该ERC20资产映射到SOLANA上