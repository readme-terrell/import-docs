---
title: Offline & Online Accounts Pairing
excerpt: 🤝 Pair your hot and cold wallet!
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Overview

The Blockdaemon Institutional Vault provides a secure offline storage option to safeguard the environment for overseeing your digital assets. This feature ensures the safety of your wallet by supporting both hot and cold wallet services as standard, with the option of incorporating cold storage. Integration allows some Hot wallet features, such as transaction creation and policy enforcement. To pair them, you must have accounts for both wallets.

> 📘 Note:
>
> Remember that Hot wallet and Cold wallet are separate entities.

## Pairing the Hot & Cold Wallet

To integrate the Hot and Cold wallet, follow the steps below:

1. Navigate to your Hot wallet, and log in.

2. Click **Settings** on the main navigation menu.

<Image align="center" src="https://files.readme.io/4494c21ad5264950eb4790d8b349a0b90f403374f31a2bfdc38d9e52d93088e9-Group_18_-_2024-09-10T140320.704.png" />

3. Click the **Wallet Pairing** tab.

<Image align="center" src="https://files.readme.io/44b553d9ffa80f54f6000fadf766f77fa4f4fd483c6374fd41397b6a12426c48-Group_18_-_2024-09-13T141056.114.png" />

4. Click the **Download Hot Pairing Message** button, and you'll receive a prompt to download the pairing message file. This file initiates and authenticates the connection with the Cold wallet.

<Image align="center" src="https://files.readme.io/8746951d51c08eb140a94993a850a4051be2581ec294c02a7f7796105cec0d02-Group_18_-_2024-09-13T141105.960.png" />

5. Navigate to the Cold wallet.

> 📘 Note:
>
> Ensure that you have accessed the Cold wallet from an air-gapped computer/device.

6. Click **Settings** on the main navigation menu.

<Image align="center" src="https://files.readme.io/5db7572-d564426a-5829-420a-ae1c-8c912fed23d4.png" />

7. Under the **Wallet Information** tab, click the **Upload pairing message** button.

<Image align="center" src="https://files.readme.io/17720a3-8abf5fb1-d890-4722-acb4-97554e1cb25c.png" />

8. Select your downloaded pairing message file from your Hot Wallet and click **Upload**.

<Image align="center" src="https://files.readme.io/598eeba-87a024ac-6507-4456-91cb-2e5a45ae41b9.png" />

9. Navigate back to the **Wallet Pairing** tab under **Settings** on your Hot wallet. Click the **Upload pairing message** button.

<Image align="center" src="https://files.readme.io/2c8a2739aa824c866b45792f7cd1cdc9f5032502166a1d6417e434c5f2c10309-Group_18_-_2024-09-13T141117.730.png" />

10. Upload the file you downloaded from the Cold wallet. This action will automatically populate the extended public key and master key fields, ensuring a secure Hot and Cold wallet integration.

<Image align="center" src="https://files.readme.io/e7b5683-00c6b487-e526-429c-aca8-30b1e152eebb.png" />

11. Once paired, you can create new accounts. Click **Accounts** on the main navigation menu.

<Image align="center" src="https://files.readme.io/44f3173ec40855769ccc709c4b9317598b6dbda8f46c492e26ac7005963fd86f-Group_18_-_2024-09-13T131757.393.png" />

12. Click the **New Account** button.

<Image align="center" src="https://files.readme.io/8821126998f57d345f37bc9c4788e89b038ee4acbb4a570dddf2e44e5415a701-Group_18_-_2024-09-13T130955.109.png" />

13. Fill in the account name, enable the **Cold Account** to enable the cold storage feature, and click **Create**.

<Image align="center" src="https://files.readme.io/0f76c91-bf831c12-b9e9-47d9-99fb-c093e676381a.png" />

14. A notification window will appear, confirming the successful pairing of keys between the Hot and Cold wallet.

> 📘 Note:
>
> Keep in mind that the security architecture involves both the parent keys and a multi-layered security system structure. As a result, even if the parent keys are compromised, the overall security of the system remains resilient and intact.

<Support />
