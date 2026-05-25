# EOA（Externally Owned Account）

> 由单一私钥直接控制的传统以太坊账户；简单但难以表达 Agent 所需的细粒度规则。

## 解释

EOA 的每次链上操作通常由同一私钥签名。适合个人用户直接控制资产，但不适合把**长期自动化权限**交给 Agent：要么全有要么全无，难以限额、限时、限合约。AI × Web3 自动化更常落在 Smart Account / AA 上。

## 例子

- **个人转账**：用户用 EOA 在钱包里确认一笔 ETH 转账。
- **Agent 误用风险**：若把 EOA 私钥注入 Agent，一次 prompt 注入即可转走全部余额。
- **迁移路径**：高频自动化改用 Smart Account + Session Key，EOA 仅作控制人。

## 误区

- **「EOA 更安全因为简单」**：简单不等于适合机器自动化。
- **「合约账户也是 EOA」**：合约账户无传统私钥，行为由代码定义。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 用户亲自签名、低频操作 | Agent 长期无人值守操作主资产 |
| 与 AA 账户组合（EOA 作 owner） | 细粒度策略仅用 EOA 硬编码 |

## 参见

- [[concepts/wallet]]
- [[concepts/account-abstraction]]
- [[concepts/smart-account]]

## 来源摘要

- [[sources/handbook__web3__wallet]]
