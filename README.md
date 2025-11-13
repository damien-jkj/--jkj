# 🎰 区块链彩票 DApp

一个基于以太坊的去中心化彩票应用，支持代币投注、NFT 票务和交易市场功能。

## 🌟 功能特性

### 核心功能
- **代币投注**: 使用 ZJU 代币参与彩票投注
- **NFT 票务**: 每次投注自动铸造 NFT 作为凭证  
- **交易市场**: NFT 票务可以在二级市场交易
- **智能合约**: 完全去中心化的抽奖逻辑

### 技术特性
- **前端**: React + TypeScript + Ant Design
- **合约**: Solidity + Hardhat
- **网络**: 本地 Ganache 测试链
- **钱包**: MetaMask 集成

## 🚀 快速开始

### 环境要求
- Node.js 16+
- MetaMask 浏览器插件
- Ganache CLI

### 📥 项目获取

#### 方式一：从老师GitHub下载
```bash
# 从老师仓库下载完整项目
git clone https://github.com/LBruyne/blockchain-course-demos
cd blockchain-course-demos

# 找到彩票项目（根据实际目录结构）
cd demo-lottery-application
```

#### 方式二：使用现有项目
如果您已经有项目文件，确保包含以下结构：
```
demo-lottery-application/
├── contracts/                 # 智能合约目录
└── lottery-frontend/         # 前端应用目录
```

**注意**: 由于 `node_modules` 文件过大且可以从依赖配置重新安装，项目不包含这两个目录。

### 🔧 安装步骤

#### 1. 安装合约依赖
```bash
# 进入合约目录
cd contracts

# 安装依赖（这会创建 node_modules）
npm install

# 或者使用 yarn
yarn install
```

#### 2. 安装前端依赖
```bash
# 进入前端目录
cd ../lottery-frontend

# 安装依赖
npm install

# 或者使用 yarn  
yarn install
```

#### 3. 启动本地区块链
```bash
# 在 contracts 目录中启动 Ganache
cd contracts
npx ganache-cli -d -p 8545
```

**保持这个终端窗口打开**，Ganache 会持续运行提供区块链服务。

#### 4. 部署智能合约
```bash
# 在新的终端窗口中，进入 contracts 目录
cd contracts

# 编译合约
npx hardhat compile

# 部署到本地网络
npx hardhat run scripts/deploy.ts --network ganache
```

部署成功后，您会看到类似输出：
```
MyERC20 deployed to: 0x...
MyERC721 deployed to: 0x...
Lottery deployed to: 0x...
```

#### 5. 启动前端应用
```bash
# 进入前端目录
cd ../lottery-frontend

# 启动开发服务器
npm start
```

前端应用将在 http://localhost:3000 启动。

### 🔗 配置 MetaMask

#### 1. 添加本地网络
- 打开 MetaMask
- 点击网络选择器
- 选择 "Add Network"

#### 2. 配置网络参数
```
Network Name: Ganache Test Chain
RPC URL: http://127.0.0.1:8545
Chain ID: 1337
Currency Symbol: ETH
```

#### 3. 导入测试账户
- 在 Ganache 终端中复制私钥
- 在 MetaMask 中选择 "Import Account"
- 粘贴私钥导入测试账户

## 📋 使用指南

### 1. 连接钱包
- 点击"连接钱包"按钮
- 授权 MetaMask 连接到本地网络
- 确认账户连接

### 2. 领取测试代币
- 点击"领取浙大币空投"
- 确认交易（获得 10,000 ZJU 代币）

### 3. 参与彩票
- 点击"投注产生希望"（每次消耗 500 ZJU）
- 授权代币使用
- 确认投注交易
- 自动获得 NFT 票务凭证

### 4. 交易市场
- 切换到"交易市场"页面
- 查看在售的 NFT 票务
- 出售自己的 NFT（默认价格 800 ZJU）
- 购买其他用户的 NFT

### 5. 管理员功能
- **开奖**: 随机选择获胜者并分发奖池
- **退款**: 特殊情况下的资金返还

## 🏗️ 项目结构

```
demo-lottery-application/
├── contracts/                 # 智能合约
│   ├── contracts/
│   │   ├── Lottery.sol       # 彩票主合约
│   │   ├── MyERC20.sol       # 代币合约
│   │   └── MyERC721.sol      # NFT 合约
│   ├── scripts/
│   │   └── deploy.ts         # 部署脚本
│   ├── hardhat.config.ts     # Hardhat 配置
│   └── package.json          # 合约依赖配置
│
└── lottery-frontend/         # 前端应用
    ├── src/
    │   ├── pages/
    │   │   ├── lottery/      # 彩票页面组件
    │   │   └── marketplace/  # 交易市场页面
    │   ├── utils/
    │   │   ├── contracts.ts  # 合约连接配置
    │   │   ├── abis/         # 合约 ABI 文件
    │   │   └── contract-addresses.json # 合约地址
    │   └── App.tsx          # 主应用组件
    └── package.json         # 前端依赖配置
```

## 🔧 故障排除

### 常见问题

#### 1. 依赖安装失败
```bash
# 清理缓存重新安装
npm cache clean --force
rm -rf node_modules
rm -f package-lock.json
npm install
```

#### 2. 端口占用
```bash
# 如果 8545 端口被占用，使用其他端口
npx ganache-cli -d -p 8546

# 记得更新前端配置中的 RPC URL
```

#### 3. MetaMask 连接问题
- 确保 Ganache 在运行
- 检查网络配置是否正确
- 尝试刷新页面重新连接

#### 4. 合约部署失败
- 确认 Ganache 在运行
- 检查 Hardhat 配置
- 查看 Ganache 终端错误信息

### 部署验证清单

- [ ] Ganache 在 8545 端口运行
- [ ] 合约成功编译和部署
- [ ] 前端依赖安装完成
- [ ] MetaMask 连接到本地网络
- [ ] 前端应用在 3000 端口运行

## 📝 开发说明

### 自定义配置
您可以修改以下文件来自定义应用：

- `contracts/scripts/deploy.ts` - 部署参数
- `lottery-frontend/src/utils/contract-addresses.json` - 合约地址
- 各合约文件中的业务逻辑参数

### 重新部署
如果修改了合约代码，需要重新部署：
```bash
cd contracts
npx hardhat compile
npx hardhat run scripts/deploy.ts --network ganache
```

## 🆘 获取帮助

如果遇到问题：

1. 检查终端错误信息
2. 查看浏览器控制台输出
3. 确认所有服务正常运行
4. 参考老师 GitHub 仓库的完整代码

---

**注意**: 本项目为教学演示用途，请在了解风险的前提下使用。实际部署到主网前请进行充分的安全审计。
🔗 智能合约
合约地址（示例）
text
MyERC20: 0x9890DA2Df15f66a8d70E4759c811d8C2d156a87F
MyERC721: 0x341a19A2fA4A6dBa06e987F4fE0a61Aa56f74aac  
Lottery: 0x27690C6B81cC1cC002205DB00243791d98DF2613
我来为您列出所有实现的功能和对应的代码：

# 📋 区块链彩票 DApp 功能清单

## 🏗️ 项目架构

### 项目结构
```
demo-lottery-application/
├── contracts/                 # 智能合约
└── lottery-frontend/         # React 前端
```

## 1. 🎰 彩票核心功能

### 智能合约 - Lottery.sol
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.0;

import "./MyERC20.sol";
import "./MyERC721.sol";

contract Lottery {
    MyERC20 public myERC20;
    MyERC721 public ticketNFT;
    
    address public manager;
    uint256 public PLAY_AMOUNT = 500 * 10**18; // 500 个代币
    uint256 public totalAmount;
    uint256 public playerNumber;
    address[] public players;
    address public winner;
    
    constructor(address _myERC20, address _ticketNFT) {
        manager = msg.sender;
        myERC20 = MyERC20(_myERC20);
        ticketNFT = MyERC721(_ticketNFT);
    }
    
    function play() public {
        require(myERC20.balanceOf(msg.sender) >= PLAY_AMOUNT, "Insufficient balance");
        require(myERC20.transferFrom(msg.sender, address(this), PLAY_AMOUNT), "Transfer failed");
        
        players.push(msg.sender);
        playerNumber++;
        totalAmount += PLAY_AMOUNT;
        
        uint256 tokenId = ticketNFT.mintTicket(msg.sender, 1, 1);
        emit LotteryPlay(msg.sender, tokenId);
    }
    
    function draw() public {
        require(msg.sender == manager, "Only manager can draw");
        require(playerNumber > 0, "No players");
        
        uint256 index = uint256(keccak256(abi.encodePacked(block.timestamp, block.difficulty))) % playerNumber;
        winner = players[index];
        
        require(myERC20.transfer(winner, totalAmount), "Prize transfer failed");
        emit LotteryDraw(winner, totalAmount);
        
        totalAmount = 0;
        playerNumber = 0;
        delete players;
    }
}
```

### 前端页面 - Lottery
```typescript
// 投注功能
const onPlay = async () => {
    if(account === '') {
        alert('You have not connected wallet yet.');
        return;
    }

    if (lotteryContract && myERC20Contract) {
        try {
            const rawPlayAmount = await lotteryContract.methods.PLAY_AMOUNT().call();
            
            await myERC20Contract.methods.approve(lotteryContract.options.address, rawPlayAmount).send({
                from: account
            });
            
            await lotteryContract.methods.play().send({
                from: account
            });

            alert('You have played the game.');
        } catch (error: any) {
            alert(error.message);
        }
    }
};

// 开奖功能（管理员）
const onDraw = async () => {
    if(account === '' || account !== managerAccount) {
        alert('Only manager can invoke this method.');
        return;
    }

    await lotteryContract.methods.draw().send({
        from: account
    });
    alert('You have draw the game.');
};
```

## 2. 💰 代币系统

### 智能合约 - MyERC20.sol
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyERC20 is ERC20 {
    mapping(address => bool) public claimedAirdropPlayerList;

    constructor(string memory name, string memory symbol) ERC20(name, symbol) {}

    function airdrop() external {
        require(claimedAirdropPlayerList[msg.sender] == false, "This user has claimed airdrop already");
        _mint(msg.sender, 10000 * 10**18); // 10,000 个代币
        claimedAirdropPlayerList[msg.sender] = true;
    }
}
```

### 前端空投功能
```typescript
const onClaimTokenAirdrop = async () => {
    if(account === '') {
        alert('You have not connected wallet yet.');
        return;
    }

    if (myERC20Contract) {
        try {
            await myERC20Contract.methods.airdrop().send({
                from: account
            });
            alert('You have claimed ZJU Token.');
        } catch (error: any) {
            alert(error.message);
        }
    }
};
```

## 3. 🎫 NFT 票务系统

### 智能合约 - MyERC721.sol
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract MyERC721 is ERC721 {
    struct Ticket {
        uint256 eventId;
        uint256 ticketId;
        uint256 price;
        bool isActive;
        address seller;
    }
    
    mapping(uint256 => Ticket) public tickets;
    mapping(uint256 => bool) public sellOrders;
    uint256[] public activeSellOrders;
    
    uint256 private _tokenIdCounter;

    constructor() ERC721("LotteryTicket", "TICKET") {}

    function mintTicket(address to, uint256 eventId, uint256 ticketId) external returns (uint256) {
        _tokenIdCounter++;
        uint256 newTokenId = _tokenIdCounter;
        
        _mint(to, newTokenId);
        tickets[newTokenId] = Ticket(eventId, ticketId, 0, false, address(0));
        
        return newTokenId;
    }

    function listForSale(uint256 tokenId, uint256 price) external {
        require(ownerOf(tokenId) == msg.sender, "Not owner");
        tickets[tokenId].price = price;
        tickets[tokenId].isActive = true;
        tickets[tokenId].seller = msg.sender;
        sellOrders[tokenId] = true;
        activeSellOrders.push(tokenId);
    }

    function buyTicket(uint256 tokenId) external payable {
        require(sellOrders[tokenId], "Not for sale");
        Ticket memory ticket = tickets[tokenId];
        require(msg.value >= ticket.price, "Insufficient payment");
        
        address seller = ticket.seller;
        _transfer(seller, msg.sender, tokenId);
        
        tickets[tokenId].isActive = false;
        tickets[tokenId].seller = address(0);
        sellOrders[tokenId] = false;
        
        payable(seller).transfer(msg.value);
    }

    function getActiveSellOrders() external view returns (uint256[] memory) {
        return activeSellOrders;
    }

    function getTicketInfo(uint256 tokenId) external view returns (uint256, uint256, uint256, bool, address) {
        Ticket memory ticket = tickets[tokenId];
        return (ticket.eventId, ticket.ticketId, ticket.price, ticket.isActive, ticket.seller);
    }
}
```

## 4. 🏪 交易市场

### 前端市场页面
```typescript
// 加载市场数据
const loadTickets = async () => {
    try {
        const activeOrders = await myERC721Contract.methods.getActiveSellOrders().call();
        
        const marketTicketsList: Ticket[] = [];
        const myTicketsList: Ticket[] = [];

        // 加载市场中的票
        for (const tokenId of activeOrders) {
            const ticketInfo = await myERC721Contract.methods.getTicketInfo(tokenId).call();
            
            marketTicketsList.push({
                tokenId: Number(tokenId),
                eventId: Number(ticketInfo[0]),
                ticketId: Number(ticketInfo[1]),
                price: web3.utils.fromWei(ticketInfo[2], 'ether'),
                isForSale: ticketInfo[3],
                seller: ticketInfo[4]
            });
        }

        setMarketTickets(marketTicketsList);
        setMyTickets(myTicketsList);
    } catch (error) {
        console.error('加载票务信息失败:', error);
    }
};

// 出售功能
const handleSell = (ticket: Ticket) => {
    setSelectedTicket(ticket);
    setSellPrice('800'); // 默认价格 800
    setSellModalVisible(true);
};

// 购买功能
const handleBuy = async (ticket: Ticket) => {
    try {
        const priceInWei = web3.utils.toWei(ticket.price, 'ether');
        await myERC721Contract.methods.buyTicket(ticket.tokenId).send({
            from: account,
            value: priceInWei
        });
        message.success('购买成功！');
        loadTickets();
    } catch (error: any) {
        message.error('购买失败: ' + error.message);
    }
};
```

## 5. 🔗 钱包连接系统

```typescript
const onClickConnectWallet = async () => {
    const {ethereum} = window;
    if (!Boolean(ethereum && ethereum.isMetaMask)) {
        alert('MetaMask is not installed!');
        return;
    }

    try {
        // 切换到本地网络
        if (ethereum.chainId !== GanacheTestChainId) {
            const chain = {
                chainId: GanacheTestChainId,
                chainName: GanacheTestChainName,
                rpcUrls: [GanacheTestChainRpcUrl],
            };

            try {
                await ethereum.request({method: "wallet_switchEthereumChain", params: [{chainId: chain.chainId}]})
            } catch (switchError: any) {
                if (switchError.code === 4902) {
                    await ethereum.request({ method: 'wallet_addEthereumChain', params: [chain]});
                }
            }
        }

        await ethereum.request({method: 'eth_requestAccounts'});
        const accounts = await ethereum.request({method: 'eth_accounts'});
        setAccount(accounts[0] || 'Not able to get accounts');
    } catch (error: any) {
        alert(error.message);
    }
};
```

## 6. 🛠️ 合约连接工具

### utils/contracts.ts
```typescript
import Addresses from './contract-addresses.json'
import Lottery from './abis/Lottery.json'
import MyERC20 from './abis/MyERC20.json'
import MyERC721 from './abis/MyERC721.json'

declare const Web3: any;

let web3: any;
let lotteryContract: any;
let myERC20Contract: any;
let myERC721Contract: any;

(function initializeContracts() {
    console.log('=== 初始化合约 ===');
    
    try {
        if (typeof window !== 'undefined' && (window as any).ethereum) {
            web3 = new Web3((window as any).ethereum);
            console.log('✅ 使用 ethereum provider 初始化 web3');
        } else {
            web3 = new Web3('http://127.0.0.1:8545');
            console.log('✅ 使用 HTTP provider 初始化 web3');
        }

        const lotteryAddress = Addresses.lottery;
        const lotteryABI = Lottery.abi;
        const myERC20Address = Addresses.myERC20;
        const myERC20ABI = MyERC20.abi;
        const myERC721Address = Addresses.myERC721;
        const myERC721ABI = MyERC721.abi;

        lotteryContract = new web3.eth.Contract(lotteryABI, lotteryAddress);
        myERC20Contract = new web3.eth.Contract(myERC20ABI, myERC20Address);
        myERC721Contract = new web3.eth.Contract(myERC721ABI, myERC721Address);

        console.log('✅ 合约实例创建完成');
        
        // 暴露到全局对象
        if (typeof window !== 'undefined') {
            (window as any).appWeb3 = web3;
            (window as any).appLotteryContract = lotteryContract;
            (window as any).appMyERC20Contract = myERC20Contract;
            (window as any).appMyERC721Contract = myERC721Contract;
        }
        
    } catch (error) {
        console.error('❌ 合约初始化失败:', error);
    }
})();

export { web3, lotteryContract, myERC20Contract, myERC721Contract };
```

## 7. 🎯 部署脚本

### scripts/deploy.ts
```typescript
import { ethers } from "hardhat";

async function main() {
  console.log("Deploying contracts...");
  
  // 部署 MyERC20
  const MyERC20 = await ethers.getContractFactory("MyERC20");
  const myERC20 = await MyERC20.deploy("ZJU Token", "ZJU");
  await myERC20.deployed();
  console.log("MyERC20 deployed to:", myERC20.address);
  
  // 部署 MyERC721
  const MyERC721 = await ethers.getContractFactory("MyERC721");
  const myERC721 = await MyERC721.deploy();
  await myERC721.deployed();
  console.log("MyERC721 deployed to:", myERC721.address);
  
  // 部署 Lottery
  const Lottery = await ethers.getContractFactory("Lottery");
  const lottery = await Lottery.deploy(myERC20.address, myERC721.address);
  await lottery.deployed();
  console.log("Lottery deployed to:", lottery.address);
  
  // 保存地址到文件
  const fs = require('fs');
  const addresses = {
    myERC20: myERC20.address,
    myERC721: myERC721.address,
    lottery: lottery.address
  };
  
  fs.writeFileSync('../lottery-frontend/src/utils/contract-addresses.json', 
    JSON.stringify(addresses, null, 2));
  
  console.log("Addresses saved to frontend!");
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

 ## 8. 📊 关键特性总结

### ✅ 已实现功能
1. **代币系统**: ERC20 代币，支持空投和转账
2. **彩票投注**: 使用代币参与彩票，自动铸造 NFT
3. **NFT 票务**: ERC721 NFT，记录投注凭证
4. **交易市场**: NFT 二级市场交易
5. **钱包集成**: MetaMask 连接和网络切换
6. **管理员功能**: 开奖和退款
7. **响应式 UI**: 基于 Ant Design 的现代界面

### 🔧 技术栈
- **前端**: React + TypeScript + Ant Design
- **合约**: Solidity + Hardhat + OpenZeppelin
- **网络**: Ganache 本地测试链
- **工具**: Web3.js + MetaMask

这个项目完整实现了去中心化彩票应用的所有核心功能，包括代币经济、NFT 系统和二级市场交易。
起始状态，没有钱
<img width="559" height="723" alt="image" src="https://github.com/user-attachments/assets/85af7bbf-0019-4e6c-8ab4-b2ba598a6361" />
四个账户和一个管理
<img width="691" height="481" alt="截屏2025-11-13 17 23 53" src="https://github.com/user-attachments/assets/b08dbcd8-00c3-4d63-a706-c2f0ccb876a3" />
一个赢家，手上的货币多于开始的
<img width="1068" height="662" alt="截屏2025-11-13 17 24 53" src="https://github.com/user-attachments/assets/8749016f-6945-48d6-a2b0-feec0e0a3714" />
已经参加的提醒
<img width="776" height="509" alt="截屏2025-11-13 17 25 41" src="https://github.com/user-attachments/assets/af6e0a34-1b7b-42b7-a765-4bf6e5e9fd24" />
退款的操作
<img width="1030" height="541" alt="截屏2025-11-13 17 30 16" src="https://github.com/user-attachments/assets/b7ea0212-b507-418f-a825-0cd9a2d0d730" />

 ## 🤝 贡献指南
感谢我的助教，给他加了一大堆的工作量，一直有很多问题，学长辛苦了
