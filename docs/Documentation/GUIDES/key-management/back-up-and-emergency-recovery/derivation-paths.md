---
title: Derivation Paths
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  image: https://files.readme.io/58aee3a-metadata.png
  robots: index
next:
  description: ''
---
A derivation path is a string representing a sequence of key derivations from the root key used to create different addresses and accounts. 

Below are the common derivation paths using a modified SLIP44-type scheme that generates BIP-32 keys.

## Derivation Path Format

The standard derivation path format is as follows:

```shell
m/purpose/coin_type/account/change/address
```

Each part of the path represents

* **m**: Master node.
* **purpose**: Set to 44 (unhardened) for BIP-44.
* **coin\_type**: SLIP44 identifier for the coin.
* **account**: The account number. Index begins at `0`.
* **change**: `0` for external addresses, `1` for change addresses (not used currently).
* **address**: The address. Index begins at `0`.

## Blockdaemon Derivation Paths

<HTMLBlock>{`
<table>
  <thead>
    <tr>
      <th>Blockchain</th>
      <th>Environment</th>
      <th>Derivation Path</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2"><strong>Bitcoin</strong></td>
      <td>Mainnet</td>
      <td><code>m/44/0/account_index/0/address_index</code></td>
      <td>Multiple receive addresses and accounts</td>
    </tr>
    <tr>
      <td>Testnet</td>
      <td><code>m/44/1/account_index/0/address_index</code></td>
      <td>Multiple receive addresses and accounts</td>
    </tr>
    <tr>
      <td rowspan="2"><strong>Ethereum</strong></td>
      <td>Mainnet</td>
      <td><code>m/44/60/account_index/0/0</code></td>
      <td>Multiple accounts</td>
    </tr>
    <tr>
      <td>Testnet</td>
      <td><code>m/44/1/account_index/0/0</code></td>
      <td>Multiple accounts</td>
    </tr>
    <tr>
      <td rowspan="2"><strong>Polygon</strong></td>
      <td>Mainnet</td>
      <td><code>m/44/966/account_index/0/0</code></td>
      <td>Multiple accounts</td>
    </tr>
    <tr>
      <td>Testnet</td>
      <td><code>m/44/1/account_index/0/0</code></td>
      <td>Multiple accounts</td>
    </tr>
    <tr>
      <td rowspan="2"><strong>Polkadot</strong></td>
      <td>Mainnet</td>
      <td><code>m/44/354/account_index/0/0</code></td>
      <td>Multiple accounts</td>
    </tr>
    <tr>
      <td>Testnet</td>
      <td><code>m/44/1/account_index/0/0</code></td>
      <td>Multiple accounts</td>
    </tr>
    <tr>
      <td rowspan="2"><strong>Solana</strong></td>
      <td>Mainnet</td>
      <td><code>m/44/501/account_index/0/0</code></td>
      <td>Multiple accounts</td>
    </tr>
    <tr>
      <td>Testnet</td>
      <td><code>m/44/1/account_index/0/0</code></td>
     <td>Multiple accounts</td>
    </tr>
  </tbody>
</table>
`}</HTMLBlock>

## Example Commands

When recovering master key shares from an ERS backup, you can specify the derivation path in your commands. Here are examples for macOS and Linux:

### macOS

Replace `{the derivation path}` with the appropriate path.

```shell
./coldwallet-cli-darwin ers  
  --backup-file-path={Where you store the backup file}  
  --private-key-pem-path={the private key path}  
  --derivation-path={the derivation path}
```

### Linux

Replace `{the derivation path}` with the appropriate path.

```shell
./coldwallet-cli-linux ers  
  --backup-file-path={Where you store the backup file}  
  --private-key-pem-path={the private key path}  
  --derivation-path={the derivation path}
```

<Support />
