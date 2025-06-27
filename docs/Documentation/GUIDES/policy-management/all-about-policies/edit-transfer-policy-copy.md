---
title: Edit Staking Policy
excerpt: ➡️Customize your staking policy easily
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
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

1. Click the **Settings**.

<Image align="center" src="https://files.readme.io/d078e8bf04c39f0f73092b153e917d1a8714caf8a93ba193eeb0895cd8aaaf6b-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Policies** Tab.

<Image align="center" src="https://files.readme.io/20a3328d1f1039ec4dfaff7e8f71fc7574b0a7e79c2e45fe2ed97fd7891526d6-Group_18_-_2024-09-11T134219.243.png" />

3. Select the **Stake** tab.

<Image align="center" src="https://files.readme.io/0660a003f2a30a47a30b0fd8da7e7464d61fc407ba06d09e4c83409ec03e98ce-Group_18_-_2024-09-11T143246.323.png" />

4. Select the **Edit** button on the top right.

<Image align="center" src="https://files.readme.io/1b33298c89d2235462bd2790d6ad49b9d6950879161caea1a5b677c3420d6f58-Group_18_-_2024-09-11T143256.906.png" />

4. Select the rule you want to remove and Click the **trash icon** at the end of the line for the rule.

<Image align="center" src="https://files.readme.io/e3b79d5be9bd7cb7a33e90bb6b69e098d4c089ad962f3aeb6ea277cc162319a3-Group_18_-_2024-09-11T143701.852.png" />

5. Click **Remove** to confirm the rule's removal.

<Image align="center" src="https://files.readme.io/23a4189cb004374111c488b499ad95f7cd636871bab634ce1f744355246de77d-Group_18_-_2024-09-11T134748.249.png" />

# Add a New Rule

To add a new rule, follow the steps below:

1. Click the **Settings**.

<Image align="center" src="https://files.readme.io/d3ecba1f7dff63ec463bd61fe56a2fc5fb0efdbb8230ae585e4cfeb8cc583d36-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Policies** Tab.

<Image align="center" src="https://files.readme.io/505bb12f3dc4bf2cf4dc75557f73744138476d2e54cac6b5e21168dcf86ec9ea-Group_18_-_2024-09-11T134219.243.png" />

3. Select the **Stake** tab.

<Image align="center" src="https://files.readme.io/1d8ad228cc93350e23da69e2dddcf29936e4808dc8dae02d02da4ed7e359b565-Group_18_-_2024-09-11T143246.323.png" />

4. Select the **Edit** button on the top right.

<Image align="center" src="https://files.readme.io/b30204be9541ad49ae4201879f54bdf02af9f40d503309501744443a61a3d740-Group_18_-_2024-09-11T143256.906.png" />

4. Click the **Add Policy** button on the top right side of your screen.

<Image align="center" src="https://files.readme.io/7dcdbb0e82eb517522173dad4c61042b33bfb20da7b87927e3ca7b362d713103-Group_18_-_2024-09-11T143805.606.png" />

5. Fill in all the fields to specify a new policy.

<Image align="center" src="https://files.readme.io/8b1db7646ed984cfdf31f36882e4772684cf7e69d8be169c91ee55ce23f7de57-Group_18_-_2024-09-11T144208.512.png" />

| Field            | Description                                                                                                                                                                                                                                   |
| :--------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Triggered By     | This field refers to the user who initiated the operation. More specifically, it refers to the group the user belongs to. Applying different policies to operations is possible depending on who initiated that operation.                    |
| Source           | This field refers to the account that initiates fund transfers. This could be “any account, " meaning any address created and governed by the wallet.                                                                                         |
| Fee Recipient    | This field refers to the designated account or wallet address that receives any fees or rewards generated from the staking process.                                                                                                           |
| Greater Than     | This field specifies the minimum amount staked (or requested to be staked). Any stake with an amount more significant than this will qualify the staking request to be subject to this policy rule.                                           |
| Assets           | This field can be specified individually, as a group of available assets, or as “All” assets. Staking only supports **ETH** as of now.                                                                                                        |
| Action Type      | This field can be specified with either allow, meaning no additional approval is required, or block, which means the operation is rejected and will not be completed. Finally requires approval, which will open up more choices if selected. |
| Withdrawal To    | This field refers to the destination wallet address where you intend to send or transfer your staked assets after you decide to unstake them.                                                                                                 |
| Approval Group   | This field refers to the approval group that you want to select.                                                                                                                                                                              |
| No. of Approvals | This field refers to the number of approvals required from the approval group.                                                                                                                                                                |

<br />

> 📘 Note:
>
> New rules will always be added to the end of the rule list, but you have the flexibility to change their order if required.

# Modify an Existing Rule

To modify an existing rule, follow the steps below:

1. Click the **Settings**.

<Image align="center" src="https://files.readme.io/b96e479bbee2a9aa715952601a6151fb85bb3c4f3ebbcff5850be3db56823f0a-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Policies** Tab.

<Image align="center" src="https://files.readme.io/8ca823f202ff0cbd6973c65c43b1e7b5e4e67b209e6f590b8ba83c8184783793-Group_18_-_2024-09-11T134219.243.png" />

3. Select the **Stake** tab.

<Image align="center" src="https://files.readme.io/dd8084381df4a80e7b4c19a3cb1e95b4d2964d02a106b33c00e21877a6c51343-Group_18_-_2024-09-11T143246.323.png" />

4. Select the **Edit** button on the top right.

<Image align="center" src="https://files.readme.io/d8b49ff25379dd51d155c26a196adb16b4b1e3c993a9ac1cd75318e63d8d8da7-Group_18_-_2024-09-11T143256.906.png" />

5. Select the rule you want to edit, and click the **pencil icon**.

<Image align="center" src="https://files.readme.io/6bae1f2bad26f27999899eb9a6d0e9e427b1c084f9599826521db1553ded68a3-Group_18_-_2024-09-11T143816.360.png" />

6. A drop-down menu will appear; modify the rule as desired.

<Image align="center" src="https://files.readme.io/a876d3b30df24412261f160a6f9c2a85dc43e3d38e2d9bf434f3d9c09d1f6cb9-Group_18_-_2024-09-11T144449.251.png" />

7. Click **Apply Changes** to confirm the changes.

<Image align="center" src="https://files.readme.io/16fc380b78661a9ad5d8d435967c29b40b7c1152ea9999b954c44a00f68e8dba-Group_18_-_2024-09-11T144719.068.png" />

8. Click **Submit** to apply the changes.

<Image align="center" src="https://files.readme.io/c7449e5a6f8c013c25a955a606772031cb513491f20cd8a05ee2607c74502478-Group_18_-_2024-09-11T144729.448.png" />

# Reposition the Rule on the List

The order of the list is crucial since rearranging the same set of rules might completely alter the wallet's behaviour. When the policy engine looks up the policy for a staking request, it goes through the available rules from the top (level 1) and checks whether the rule's conditions apply to the staking request; if they do, it performs the action that follows (allow, block, require approval) and disregards the remaining rules in the list. If not, the program will go to the following rule in the list, and so on.

To change the order of the rule, follow the steps below:

1. Click the **Settings**.

<Image align="center" src="https://files.readme.io/f34c2746ce24edc8617af9979b15b733a382fd6e9d8b5b808d2a19bbe7456e1b-Group_18_-_2024-09-10T140320.704.png" />

2. Select the **Policies** Tab.

<Image align="center" src="https://files.readme.io/1c855d0986fff1e0203b090415e847d17243e48975d6b69711cfca389de17319-Group_18_-_2024-09-11T134219.243.png" />

3. Select the **Stake** tab.

<Image align="center" src="https://files.readme.io/669e22e4a13a18f850efa36b4fce5b417cf3b10a06c8b1a8f34a0a5816dcb166-Group_18_-_2024-09-11T143246.323.png" />

4. Select the **Edit** button on the top right.

<Image align="center" src="https://files.readme.io/4f4b6e878e4c077fdbcaaaaf7058d8876df1e9e899b95430ac4236a14b270aff-Group_18_-_2024-09-11T143256.906.png" />

4. Click the **square icon** of the rule you want to reorder. Drag the rule up or down the list.

<Image align="center" src="https://files.readme.io/754d74b078cbd895d6e1792433f8e88463d7053f1b6fc3db87b2ee55486bae9e-Group_18_-_2024-09-11T140835.372.png" />

> 📘 Note:
>
> Ensure to click the Submit button when modifying the rule to finalize the request for modifying the rule.

<Support />
