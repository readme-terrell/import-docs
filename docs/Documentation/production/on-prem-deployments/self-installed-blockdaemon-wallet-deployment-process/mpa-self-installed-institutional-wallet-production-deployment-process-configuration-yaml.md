---
title: Wallet Configuration yaml
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
# Overview

The MPA product is centered around the concept of separating keys so that no one thing is together at the same time. This is accomplished by separating the policy nodes so that they are not in one place at one time. This requires a centralized configuration that will become split to achieve this result. The central configuration is currently called the bd-wallet.yml. 

Using scripts, we validate the split conditions before we generate the .conf files that the application uses when it starts up. This shared context can be safely distributed because the downstream policy nodes and wallet installs will not use secrets but references from within this file. 

Other known non-sensitive information can be stored in string format within the wallet configuration file. 

# Reasoning of Wallet YML

Because of the interdependencies of the components, an ill-formatted configuration or value can have disastrous consequences. Therefore it is highly important to validate the configuration before each component consumes them.

## Side Effects of Bad Application Configs

Bad configurations can have bad side effects. For instance, if you push an incorrect configuration, you may need to destroy the database and start over or roll back to a previous data version. Stopping the generation of application configurations dynamically is important so that data loss or application downtime is limited or eliminated.

## Security Ramifications

If improper keys or security configurations are used within the configuration, it could open up the wallet to unacceptable risk. Validating the configuration before deployment is therefore highly recommended to mitigate this risk as much as possible.

# How It Splits

<Image align="center" src="https://files.readme.io/b7d588c-Asset_5300x_5.png" />

When we generate a bd-wallet.yml, we ask the users a series of questions to generate the proper format so that we can fit the configuration to the target environment. Once generated, these configuration values can be changed from within the bd-wallet.yml file to obtain the desired configuration. 

For instance, if one needs to change the secret location of a particular secret, one can change the secret provider, prefix, and/or namespace to ensure that the secret is accessed properly from the reference.

## Dynamic Infrastructure

Using the bd-wallet.yml, dynamic infrastructure can be created for the deployment paradigms that are using the Cloud Development Kit (CDK).

## Static Infrastructure

Some customers may want to deploy static infrastructure in their environments using CloudFormation, Terraform, Helm, Ansible, or raw scripts. This static infrastructure will need a configuration file for each of the components. 

These configurations must be generated with every deployment to validate them before deployment.

# bd-wallet.yaml specification

The bd-wallet.yml file is the centralized specification for the Institutional Vault deployment. It is generated during the initial setup process by answering environment-related questions. It contains customizable configuration values for various wallet components, such as policies, blockchains, secret locations, providers, and namespaces. During the second installation phase, this file generates individual config files for each wallet component, storing pointers to the seeded secrets rather than the secrets themselves.

Note: for customized deployments that use static infrastructure (e.g., Terraform, Helm, Ansible, or raw scripts), configurations need to be generated and validated with each deployment to ensure compatibility and security. To avoid disastrous consequences from ill-formatted configurations, validating these files before consumption is crucial.

The below specification includes inline comments describing the purpose of each field. 

> 📘 Note:
>
> This file is not to be used for installs, as certain duplicated configurations have been removed for brevity.

```yaml
api_version: v1
deployer:
  namespace: customer # string, mandatory
  secret_driver: awsSecret
  secret_prefix: bd-wallet
  type: ecs
environments:
- account_id: '918838575074'
  components:
  - approvalService
  - facade
  - wallet
  - policyNode0
  - policyNode1
  - policyNode2
  hosted_zone: bankmerc.io
  hosted_zone_id: Z0609465GZE6OM3315SO
  name: testnet
  region: us-east-2
  testnet: true
  users:
  - group: owner
    name: Customer
    user_id: name@customer-bank.com
  - group: owner
    name: Customer
    user_id: name@customer-bank.com
  - group: owner
    name: Customer
    user_id: name@customer-bank.com
- account_id: '918838575074'
  components:
  - approvalService
  - facade
  - wallet
  - policyNode0
  - policyNode1
  - policyNode2
  hosted_zone: bankmerc.io
  hosted_zone_id: Z0609465GZE6OM3315SO
  name: mainnet
  region: us-east-2
  testnet: false
  users:
  - group: owner
    name: Customer
    user_id: name@customer-bank.com
  - group: owner
    name: Customer
    user_id: name@customer-bank.com
  - group: owner
    name: Customer
    user_id: name@customer-bank.com
kind: deployment-sandbox-ecs # string, mandatory
mpa:
  approval_service:
    apple_key_id: HU65BQVL7J
    apple_push_key_string:
      name: approval-service.apple-push-key # AUTHKEY # string, mandatory
      type: awsSecret
    apple_team_id: AF38MFZ82R
    bundle_id: com.blockdaemon.Advanced-MPC-Approver
    confirmation_callback: []
    count: 3
    environment_id: customer{{ env `ENVIRON_SUFFIX` }}
    min_version: v1.0.4
    port: 9876
    timeout: 5s
  assets:
  - abbreviation: BTC
    fee_precision: 8
    has_flat_fee: false
    is_account_based: false
    name: Bitcoin
    provider: ubiquity
    stable_height: 6
    transaction_poll_interval_in_seconds: 60
    unit_precision: 8
    unit_string: sat/byte
  - abbreviation: ETH
    fee_precision: 9
    has_flat_fee: false
    is_account_based: true
    name: ethereum
    provider: ubiquity
    stable_height: 12
    transaction_poll_interval_in_seconds: 20
    unit_precision: 18
    unit_string: gwei/gas
  - abbreviation: SOL
    fee_precision: 9
    has_flat_fee: true
    is_account_based: true
    name: solana
    provider: ubiquity-sol
    stable_height: 1
    transaction_poll_interval_in_seconds: 30
    unit_precision: 9
    unit_string: lamport
  - abbreviation: WND
    fee_precision: 9
    has_flat_fee: false
    is_account_based: true
    name: Polkadot
    provider: ubiquity
    stable_height: 12
    testnet: true
    transaction_poll_interval_in_seconds: 20
    unit_precision: 12
    unit_string: mWND
  - abbreviation: DOT
    fee_precision: 7
    has_flat_fee: false
    is_account_based: true
    name: Polkadot
    provider: ubiquity
    stable_height: 12
    testnet: false
    transaction_poll_interval_in_seconds: 20
    unit_precision: 10
    unit_string: mDOT
  blockchains:
    btcmain:
      name: BTC
      service:
        auth_token:
          name: ubiquity_auth_token
          type: awsSecret
        name: bd_ubiquity
        test_network: false
      utxo_strategy: mostconfirmations
    btctest:
      name: BTC
      service:
        auth_token:
          name: ubiquity_auth_token
          type: awsSecret
        name: bd_ubiquity
        test_network: true
      utxo_strategy: mostconfirmations
    ethmain:
      name: ETH
      service:
        auth_token:
          name: ubiquity_auth_token
          type: awsSecret
        name: bd_ubiquity
        test_network: false
    ethtest:
      name: ETH
      service:
        auth_token:
          name: ubiquity_auth_token
          type: awsSecret
        name: bd_ubiquity
        test_network: true
    polkadot:
      name: DOT
      service:
        auth_token:
          name: ubiquity_auth_token
          type: awsSecret
        name: sidecar
        test_network: false
        url: https://svc.blockdaemon.com/polkadot/mainnet/native
    solanamain:
      name: SOL
      service:
        auth_token:
          name: ubiquity_auth_token
          type: awsSecret
        name: bd_ubiquity
        test_network: false
    solanatest:
      name: SOL
      service:
        auth_token:
          name: ubiquity_auth_token
          type: awsSecret
        name: bd_ubiquity
        test_network: true
    westend:
      name: WND
      service:
        auth_token:
          name: ubiquity_auth_token
          type: awsSecret
        name: sidecar
        test_network: true
        url: https://svc.blockdaemon.com/polkadot/westend/native
  # Configuration of the MQTT client.
  broker:
    broker_clients:
      approvalService:
        # ClientID must be a unique value which the broker uses to ensure delivery of messages to the client.
        client_id: b41c4cf5-8856-4663-9b7f-80e3e8ea9a7a # string, mandatory
        password: # Password of the client. Must match the password hash in broker passwd. Use the utility mosquitto_passwd to add users.
          name: approval-service.broker-info# PASSWORD # string, mandatory
          type: awsSecret
        pub_pass_hash:
          name: approval-service.broker-password-hash
          type: awsSecret
        # Username of the client. Must match the username in broker passwd. Use the utility mosquitto_passwd to add users.
        username: approver  # string, mandatory
      facade:
        # ClientID must be a unique value which the broker uses to ensure delivery of messages to the client.
        client_id: f21eece6-fe63-4a29-8bed-c69fde11fd03 # string, mandatory
        password: # Password of the client. Must match the password hash in broker passwd. Use the utility mosquitto_passwd to add users.
          name: facade.broker-info#PASSWORD # string, mandatory
          type: awsSecret
        pub_pass_hash:
          name: facade.broker-password-hash
          type: awsSecret
        # Username of the client. Must match the username in broker passwd. Use the utility mosquitto_passwd to add users.
        username: facade # string, mandatory
      policyNode0:
        # ClientID must be a unique value which the broker uses to ensure delivery of messages to the client.
        client_id: 73935715-10db-46a3-897b-657bf8f84e34 # string, mandatory
        password: # Password of the client. Must match the password hash in broker passwd. Use the utility mosquitto_passwd to add users.
          name: policy-node0.broker-info#PASSWORD # string, mandatory
          type: awsSecret
        pub_pass_hash:
          name: policy-node0.broker-password-hash
          type: awsSecret
        # Username of the client. Must match the username in broker passwd. Use the utility mosquitto_passwd to add users.
        username: node0 # string, mandatory
      policyNode1:
        # ClientID must be a unique value which the broker uses to ensure delivery of messages to the client.
        client_id: 870e11f6-a27b-472d-9d83-4648391b8059 # string, mandatory
        password: # Password of the client. Must match the password hash in broker passwd. Use the utility mosquitto_passwd to add users.
          name: policy-node1.broker-info#PASSWORD # string, mandatory
          type: awsSecret
        pub_pass_hash:
          name: policy-node1.broker-password-hash
          type: awsSecret
        # Username of the client. Must match the username in broker passwd. Use the utility mosquitto_passwd to add users.
        username: node1 # string, mandatory
      policyNode2:
        # ClientID must be a unique value which the broker uses to ensure delivery of messages to the client.
        client_id: 658981a2-fab8-4e66-8732-0766c8c20ce5 # string, mandatory
        password: # Password of the client. Must match the password hash in broker passwd. Use the utility mosquitto_passwd to add users.
          name: policy-node2.broker-info#PASSWORD # string, mandatory
          type: awsSecret
        pub_pass_hash:
          name: policy-node2.broker-password-hash
          type: awsSecret
        # Username of the client. Must match the username in broker passwd. Use the utility mosquitto_passwd to add users.
        username: node2 # string, mandatory
      wallet:
        # ClientID must be a unique value which the broker uses to ensure delivery of messages to the client.
        client_id: fd34953b-1fd3-4a3a-8baf-fbab3cef2d9d # string, mandatory
        password: # Password of the client. Must match the password hash in broker passwd. Use the utility mosquitto_passwd to add users.
          name: wallet.broker-info#PASSWORD # string, mandatory
          type: awsSecret
        pub_pass_hash:
          name: wallet.broker-password-hash
          type: awsSecret
        # Username of the client. Must match the username in broker passwd. Use the utility mosquitto_passwd to add users.
        username: wallet # string, mandatory
    broker_private_key:
      name: broker-private-key
      type: awsSecret
    broker_public_key:
      name: broker-public-key
      type: awsSecret
    # Protocol, host and port of the broker. Port found in broker configuration.
    broker_url: mqtts://mosquitto:8883
    platform: mosquitto # string, mandatory
    use_aws_certificate_authority: true # boolean, mandatory
  # Configuration of the database.
  database:
    creds: # string, mandatory
      approvalService: 
        hostname:
          name: approval-service.db-info#DB_HOST # string, mandatory
          type: awsSecret
        password:
          name: approval-service.db-info#DB_PASSWORD # string, mandatory
          type: awsSecret
        username:
          name: approval-service.db-info#USERNAME # string, mandatory
          type: awsSecret
      facade:
        hostname:
          name: facade.db-info#DB_HOST # string, mandatory
          type: awsSecret
        password:
          name: facade.db-info#DB_PASSWORD # string, mandatory
          type: awsSecret
        username:
          name: facade.db-info#USERNAME # string, mandatory
          type: awsSecret
      policyNode0:
        # Password used to encrypt the database. Either EncryptorMasterPassword or EncryptorKeyFile must be set.
        encryptor_master_password:
          name: policy-node0.encryptor-master-password # string, mandatory
          type: enclaveSecret
        hostname:
          name: policy-node0.db-info#DB_HOST # string, mandatory
          type: awsSecret
        password:
          name: policy-node0.db-info#DB_PASSWORD # string, mandatory
          type: awsSecret
        username:
          name: policy-node0.db-info#USERNAME # string, mandatory
          type: awsSecret
      policyNode1:
        # Password used to encrypt the database. Either EncryptorMasterPassword or EncryptorKeyFile must be set.
        encryptor_master_password:
          name: policy-node1.encryptor-master-password # string, mandatory
          type: enclaveSecret
        hostname:
          name: policy-node1.db-info#DB_HOST # string, mandatory
          type: awsSecret
        password:
          name: policy-node1.db-info#DB_PASSWORD # string, mandatory
          type: awsSecret
        username:
          name: policy-node1.db-info#USERNAME # string, mandatory
          type: awsSecret
      policyNode2:
        # Password used to encrypt the database. Either EncryptorMasterPassword or EncryptorKeyFile must be set.
        encryptor_master_password:
          name: policy-node2.encryptor-master-password # string, mandatory
          type: enclaveSecret
        hostname:
          name: policy-node2.db-info#DB_HOST # string, mandatory
          type: awsSecret
        password:
          name: policy-node2.db-info#DB_PASSWORD # string, mandatory
          type: awsSecret
        username:
          name: policy-node2.db-info#USERNAME # string, mandatory
          type: awsSecret
      wallet:
        hostname:
          name: wallet.db-info#DB_HOST # string, mandatory
          type: awsSecret
        password:
          name: wallet.db-info#DB_PASSWORD # string, mandatory
          type: awsSecret
        username:
          name: wallet.db-info#USERNAME # string, mandatory
          type: awsSecret
    # Types supported: mysql, pgx, sqlite.
    driver_name: pgx # string, mandatory
    # Maximum amount of idle connections.
    max_idle_conns: 10 # integer, mandatory
    # Maximum amount of open connections.
    max_open_conns: 10 # integer, mandatory
  features: []
  ganache: false
  # IdPs are whitelisted here
  oidc_config:
  # OIDCConfig.x # where x is a unique key. # string, mandatory
    audience:
      name: auth0#AUDIENCE # string, mandatory
      type: awsSecret
    # Used for matching IdP tokens.
    client_id_native:
      name: auth0#CLIENT_ID_NATIVE # string, mandatory
      type: awsSecret
    # Used for matching IdP tokens.
    client_id_spa:
      name: auth0#CLIENT_ID_SPA # string, mandatory
      type: awsSecret
    # Used for matching IdP tokens.
    issuer:
      name: auth0#ISSUER # string, mandatory
      type: awsSecret
    type: auth0
  # Configuration of policy remote nodes.
  policy_nodes:
  # ERS public key. Private key gen: 'openssl genrsa -out private-key.pem 3072'. Upload private-key.pem to 1Password.
  # Public key gen: 'openssl rsa -in private-key.pem -pubout -outform D | base64'. Insert public key in config.
  # Note: For 1Password downloaded private keys, the format needs to be changed back into PEM format for public key gen: 'ssh-keygen -p -f id_rsa -m PEM'.
    ers_public_key:
      name: ers-public-key # string, mandatory
      type: awsSecret
    # Configuration of remote nodes.
    nodes:
      # MPA endpoint of the node.
      '0':
        address: policyNode0:9080
        attestation: false
        port: 9080 # MPA port of the node.
         # Private key of the node.
        private_key:
          name: policy-node0.node-private-key
          type: awsSecret
         # Public key of the node.
        public_key:
          name: policy-node0.node-public-key
          type: awsSecret
      # MPA endpoint of the node.
      '1':
        address: policyNode1:9080
        attestation: false
        port: 9080 # MPA port of the node.
         # Private key of the node.
        private_key:
          name: policy-node1.node-private-key
          type: awsSecret
         # Public key of the node.
        public_key:
          name: policy-node1.node-public-key
          type: awsSecret
      # MPA endpoint of the node.
      '2':
        address: policyNode2:9080
        attestation: false
        port: 9080 # MPA port of the node.
         # Private key of the node.
        private_key:
          name: policy-node2.node-private-key
          type: awsSecret
         # Public key of the node.
        public_key:
          name: policy-node2.node-public-key
          type: awsSecret
    # Configuration of policies.
    policies:
      # Map of operation types to policies.
      transfer:
        Policies:
        - AmountCurrency: USD
          ApproverExpression:
            Groups: # string, mandatory
            - owner
            RequiredCount: 1 # integer, mandatory
          DestinationType: internal
          MinAmount: '500' # string, mandatory
          TxCurrencies: # string, mandatory
          - BTC
        - AmountCurrency: USD # string, mandatory
          ApproverExpression:
            Groups: # string, mandatory
            - owner
            RequiredCount: 1 # integer, mandatory
          DestinationType: internal # string, mandatory
          MinAmount: '1000' # string, mandatory
          TxCurrencies: # string, mandatory
          - ETH
        - ApproverExpression:
            Op: allow # string, mandatory
          DestinationType: internal # string, mandatory
          TxCurrencies: # string, mandatory
          - BTC
          - ETH
        - ApproverExpression:
            Groups: # string, mandatory
            - owner
            RequiredCount: 1 # integer, mandatory
        PolicyOperationType: transfer # string, mandatory
      # Map of operation types to policies.
      update policy set:
        Policies:
        - ApproverExpression:
            Groups: # string, mandatory
            - owner
            RequiredCount: 1 # integer, mandatory
          PolicyUpdateOpType: transfer # string, mandatory
        - ApproverExpression:
            Groups: # string, mandatory
            - owner
            RequiredCount: 1 # integer, mandatory
          PolicyUpdateOpType: stake # string, mandatory
        - ApproverExpression:
            Groups: # string, mandatory
            - owner
            RequiredCount: 1 # integer, mandatory
          PolicyUpdateOpType: unstake # string, mandatory
        - ApproverExpression:
            Op: block # string, mandatory
          PolicyUpdateOpType: '' # string, mandatory
        PolicyOperationType: update policy set # string, mandatory
    rpc_port: 9080 # integer, mandatory
    # port for HTTP server
    server_port: 8080 # integer, mandatory
  # Exchange rate services. A number rate services can be configured. To lookup a symbol the first one for that symbol is used.
  rate_service:
  # coinlayer.com access key
  - access_key:
      name: rateservice-accesskey # string, mandatory
      type: awsSecret
    service_name: coinlayer
    # List of symbols that this service will be used for
    symbols:
    - BTC
    - ETH
    - ADA
    # Time to cache the rate.
    ttl: 1h13m
    validate: true
  - service_name: coincap
    # List of symbols that this service will be used for
    symbols:
    - SOL
    - NEAR
    - DOT
    - WND:DOT
    # Time to cache the rate.
    ttl: 43m
    validate: true
  skip_confirmations: false
  tags: {}

```

<Support />
