---
title: Receive Funds
excerpt: 🤑 Learn how to receive funds within your Institutional Vault
deprecated: false
hidden: false
metadata:
  title: Receive Funds
  description: >-
    Effortlessly receive funds with Blockdaemon Wallet. Explore the steps to
    securely accept and manage incoming transactions for your digital assets
  image: https://files.readme.io/1a21f38-image_3.png
  robots: index
next:
  description: ''
---
# Overview

To receive funds, a user must possess an account within the Institutional Vault. An Institutional Vault Account serves as a feature that segregates wallet addresses. For balance-based chains like Ethereum, each account is associated with a unique address. For UTXO-based chains like Bitcoin, an account can contain multiple addresses. Accounts can be further restricted by policies. It plays a vital role in securely storing and managing digital assets, facilitating the sending and receiving of digital assets, tracking balances, and providing access to transaction history. 

To secure your assets within the Institutional Vault, generating addresses to which assets can be directed is essential. Within the Institutional Vault, assets are grouped inside accounts, permitting the configuration of transaction policies that apply to various assets based on their associated account. Whenever an asset is added to an account, a corresponding address is generated. The option to include additional addresses is available for assets following the UTXO (Unspent Transaction Output) model.

> 🚧 Warning:
>
> Ensure that all **potentially receivable** assets are enabled on your wallet's account. If they are not, you will be unable to spend or use them within the wallet.

# How to Receive Funds

You can receive funds through the online wallet’s menu by following the steps below:

1. Click on the **Accounts** menu.

<Image align="center" src="https://files.readme.io/c63c285db061e331abaf368dbda846a889af9f2e43f03ab732134a2cfafca351-Group_18_-_2024-09-13T131757.393.png" />

2. Click the **New Account** button.

<Image align="center" src="https://files.readme.io/670477cdb8fb5ebde58449bfbfbca149d528cb26ff6e75e4b53f58bd54cb3d5e-Group_18_-_2024-09-13T130955.109.png" />

3. Enter the **name** of the account.

<Image align="center" src="https://files.readme.io/230b62842ca665c2e8db4d0682e7a3bee4f7cb40007df63b40465ef7efa01e7c-Group_18_-_2024-09-13T131021.700.png" />

4. Click **Create**. 

<Image align="center" src="https://files.readme.io/7b78e015e3da4477f0ff22006c9361ca4785b6f42c7a29f273d5fc690ddddd7a-Group_18_-_2024-09-13T131033.008.png" />

> 📘 Note:
>
> The name has to be unique.

5. The account is added to the wallet's list of accounts and labeled "**Creation in Progress**". Below is a comprehensive overview of how to create an account:
6. When the account is created, you will receive a notification in the web wallet telling you the account is ready. The “Creation in Progress” label disappears.
7. Click on the **newly created account** to go to **Account details**.
8. Click the **Add Asset** button.

<Image align="center" src="https://files.readme.io/641f2b310ac6247729ce44bd8a8f96858c96ccff3e3ec133de43d1f67291e93f-Group_18_-_2024-09-13T131116.487.png" />

9. Select the asset from which you want to receive funds.

<Image align="center" src="https://files.readme.io/805a498774c3350b3c34586c6d6107b2f511321f31ab66018011564aaee6b14d-Group_18_-_2024-09-13T131314.635.png" />

10. Click **Add Crypto**. The asset will be included in the account, and a unique address will be generated for it.

<Image align="center" src="https://files.readme.io/aaf347560e8dfd6651344a2e4df9d50edd958abfd36d6fb4382526ab3a00ad74-Group_18_-_2024-09-13T131331.258.png" />

11. Go to the **Addresses submenu** to see and copy the address.

<Image align="center" src="https://files.readme.io/dd800e17af3319d6df8d5e7879141db52ac9b0d4c0f088d696a6bd2ed4af623d-Group_18_-_2024-09-13T131402.071.png" />

<Image align="center" src="https://files.readme.io/cc8c0f9c2e9e512aac0aa7ec291d7a90f19ef0ce49c72cbd64c1f35fe4bff67f-Group_18_-_2024-09-13T131529.920.png" />

> 📘 Note:
>
> By default, if no configuration is specified, Bitcoin addresses are of the `P2PKH` (legacy) type. However, we also support `P2SH-P2WPKH` type address for Bitcoin.

12. You can transfer funds from this address to the recently created account using either another address or a testnet faucet.
13. Click the **Transaction History** menu to track the incoming transaction. The transaction will start appearing when it is confirmed on the blockchain.
14. When the transaction is confirmed on the blockchain, the account balance is updated to reflect how much has been received.

<br />

<Support />
