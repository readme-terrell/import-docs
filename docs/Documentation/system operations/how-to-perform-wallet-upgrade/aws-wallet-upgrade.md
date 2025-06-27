---
title: AWS Wallet Upgrade
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 Note:
>
> The upgrade process may take up to an hour.

To upgrade your AWS Wallet, follow the steps below:

1. Pull the Makefile version you want to upgrade:

```
aws s3 cp s3://638663786504-prod-mpa-deployment-customer-artifacts/release/<RELEASE VERSION>/Makefile
```

2. Pull corresponding deployer bundle:

```
make pull-deployer
```

3. Re-pull your `bd-wallet.yml` that we generate to ensure that it's still compatible:

```
aws s3 cp s3://638663786504-prod-mpa-deployment-customer-artifacts/customer/<your-namespace>/bd-wallet.yml
```

4. Finally, simply run the following to upgrade:

```
make update
```

<Support />
