---
title: Edit Transfer Policy
excerpt: ➡️Customize your transfer policy easily
deprecated: false
hidden: false
metadata:
  title: Edit Transfer Policy
  description: >-
    Effortlessly edit transfer policies in Blockdaemon Wallet. Explore how to
    customize and manage transfer rules for secure and controlled digital asset
    transfers.
  image: https://files.readme.io/649785a-image_3.png
  robots: index
next:
  description: ''
---
# Overview

An admin user can edit policies by clicking the Policies tab under the Settings menu. This will take the user to the policy editor, where they can modify the policy set, such as:

1. Remove a rule.
2. Add a new rule.
3. Modify an existing rule.
4. Reposition the rule on the list.

> 🚧 Warning:
>
> If a policy change is not approved/rejected by an owner within a week, the policy edit button in any environment is deactivated. The timeout for the approvals can be modified.

> 📘 Note:
>
> Ensure you've hit the Submit button to modify the policy set. To undo the modifications, click the Cancel button.

# Remove a Rule

To remove a rule, follow the steps below:

1. Click **Settings**.

<Image align="center" src="https://files.readme.io/b40eee7366920cc05c1cb055e572afa35b4c30b1096240a362ce9aeea7767e46-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Policies** Tab.

<Image align="center" src="https://files.readme.io/48a5283121117d5f5234d32ad5190f67f8b0e37c881514b74a175a55205126a8-Group_18_-_2024-09-11T134219.243.png" />

3. Select the **Edit** button on the top right.

<Image align="center" src="https://files.readme.io/0b1e266764d349c81b536e63db44740a84d4283264fd44e666725ee75cc9d7d9-Group_18_-_2024-09-11T134230.714.png" />

4. Select the rule you want to remove and Click the **trash icon** at the end of the line for the rule.

<Image align="center" src="https://files.readme.io/2db84a70076c28d7d0000db20847fdb9d7db2ecf8dc27a5f2ac4d56f6e25a8eb-Group_18_-_2024-09-11T134531.274.png" />

5. Click **Remove** to confirm the rule's removal.

<Image align="center" src="https://files.readme.io/0ce2642948f2f7c739febd49e0fde9e78fe4d049054689bcadd9e9d0ab81c0b0-Group_18_-_2024-09-11T134748.249.png" />

# Add a New Rule

To add a new rule, follow the steps below:

1. Click **Settings**.

<Image align="center" src="https://files.readme.io/d3fe67706830a9118df648a9044d821be0f8f7807966c8856c1626a4e996f9c7-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Policies** Tab.

<Image align="center" src="https://files.readme.io/124a571ad5b0b01802aa87eea2c366b609118dfee5ac1cbd99fd3dcc3724b07b-Group_18_-_2024-09-11T134219.243.png" />

3. Select the **Edit** button on the top right.

<Image align="center" src="https://files.readme.io/5e177b017c7d03b5cfb6dcbc1b412ed3ba84e4e49c252ba018c71ba4e1d2b99f-Group_18_-_2024-09-11T134230.714.png" />

4. Click the **Add Policy** button on the top right side of your screen.

<Image align="center" src="https://files.readme.io/0619a6a67b158849301ba227cd64d1ce49ed3786d7f840fcfa84ef94bb19c554-Group_18_-_2024-09-11T135121.692.png" />

5. Fill in all the fields to specify a new policy.

<Image align="center" src="https://files.readme.io/f96b47dc9daaa8409aba835235654d02db2d81b23601d6e8146d39101225189c-Group_18_-_2024-09-11T135842.121.png" />

| Field            | Description                                                                                                                                                                                                                                                                       |
| :--------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Triggered By     | This field refers to the user who initiated the operation. More specifically, it refers to the group the user belongs to. Applying different policies to operations is possible depending on who initiated that operation.                                                        |
| Source           | This field refers to the account that initiates fund transfers. This could be “any account, " meaning any address created and governed by the wallet.                                                                                                                             |
| Destination Type | This field refers to the destination account. Additionally, “any external address” means a transfer that takes funds outside the wallet. It could also be a specific account inside the wallet as well.                                                                           |
| Greater Than     | This field specifies the minimum amount that is transferred (or requested to be transferred). Any transfer with an amount more significant than this will qualify the transfer request.                                                                                           |
| Assets           | This field can be specified individually, as a group of available assets, or as “All” assets.                                                                                                                                                                                     |
| Action Type      | This field can be specified with either allow, meaning no additional approval is required, and the operation can be completed, or block, which means the operation is rejected and will not be completed. Finally requires approval, which will open up more choices if selected. |
| Approval Group   | This field refers to the approval group that you want to select.                                                                                                                                                                                                                  |
| No. of Approvals | This field refers to the number of approvals required from the approval group.                                                                                                                                                                                                    |

# Modify an Existing Rule

To modify an existing rule, follow the steps below:

1. Click **Settings**.

<Image align="center" src="https://files.readme.io/53edbd4f0a9c3c8d39c5400628aad3d12e29b84192bc2cd12bfa59e0bcf630aa-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Policies** Tab.

<Image align="center" src="https://files.readme.io/2bd034110da288894b2ecbed5d6a74582a1a0780b27d701ced6c2f6721ada022-Group_18_-_2024-09-11T134219.243.png" />

3. Select the **Edit** button on the top right.

<Image align="center" src="https://files.readme.io/1282826fb5bd6387bd3f9081ebbd3480f06f608c87fa5aba5734be34b6e3e716-Group_18_-_2024-09-11T134230.714.png" />

4. Select the rule you want to edit, and click the **pencil icon**.

<Image align="center" src="https://files.readme.io/fbfd92a6b5429310902dbbacb2e6b61be3fdd100db29a5f5435bd1d85eb6ee01-Group_18_-_2024-09-11T140044.702.png" />

5. A drop-down menu will appear. Modify the rule as desired.

<Image align="center" src="https://files.readme.io/0d4961e5a58fbcbfe1e352981bce09f8de04b26c19d75a0bf9de6c6f3eb89de7-Group_18_-_2024-09-11T135842.121.png" />

6. Click **Apply Changes** to confirm the changes.

<Image align="center" src="https://files.readme.io/3d1480c7b65df2c6df7a58f3728c52550f0333a44d5b5d1b1a8406160b41d37c-Group_18_-_2024-09-11T140405.879.png" />

# Reposition the Rule on the List

The order of the list is crucial since rearranging the same set of rules might completely alter the wallet's behaviour. When the policy engine looks up the policy for a transfer request, it goes through the available rules from the top (level 1) and checks whether the rule's conditions apply to the transfer request. If they do, it performs the action that follows (allow, block, require approval) and disregards the remaining rules in the list. If not, the program will go to the following rule in the list, and so on.

To change the order of the rule, follow the steps below:

1. Click **Settings**.

<Image align="center" src="https://files.readme.io/00bf4c834b65854b5be853e1cc3c85298583b6fa87e46769c6e2e23b36380d34-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Policies** Tab.

<Image align="center" src="https://files.readme.io/fa03563e554dd8683d6b5fd37cb670fe3a7ac1961ab241037786c115b2e023c3-Group_18_-_2024-09-11T134219.243.png" />

3. Select the **Edit** button on the top right.

<Image align="center" src="https://files.readme.io/195cb4c9edeeebbc7d3137d217c33503262d05365c6af88ed733afde6b6bc8f7-Group_18_-_2024-09-11T134230.714.png" />

4. Click the **square icon** of the rule you want to reorder. Drag the rule up or down the list.

<Image align="center" src="https://files.readme.io/a52e6a1b450849af7b68d2673d1b0f094d414f146dec5f2442a7e2c03d791a94-Group_18_-_2024-09-11T140900.430.png" />

> 📘 Note:
>
> Ensure to click the **Submit** button when modifying the rule to finalize the request for modifying the rule.

<Support />
