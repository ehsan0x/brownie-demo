# BROWNIE COMMANDS

`brownie init`  
`brownie compile`  
`brownie run`  
`brownie networks`  
`brownie test`  
 `-k name_of_function` test only one function  
 `-pdb` if results wrong console opens a python shell to debug further  
 `-s` shows a more verbose result of test  
`brownie console` kicks user off into a brownie console. `import` statements are already imported there too alongside `accounts` and other brownie keywords.

# DEPLOYMENT REQUIREMENTS

1. account (three ways to access accounts)
    1. `accounts[0-9]` local ganache account
    2. `accounts new` and `accounts.load('account-name')` password encrypted account
    3. `.env file` referenced in `brownie-config.yaml` file used with `accounts.load(config["wallets"]["from_key"]))` after `import config`
2. private key
3. network
    1. `import network` `network.show_active()`
    2. adding a netowrk to brownie's networks list: `brownie networks add Ethereum ganache-local host=http://172.28.48.1:8545 chainid=1337`

# DEPLOY SCRIPT PREPARATION STEPS

1. import accounts, config, CONTRACT_NAME
2. `CONTRACT.deploy({"from": account})`
3. make sure test files in `tests` folder start with `test` prefix
4. to deploy mocks create a `test` folder inside `contracts` folder

# TESTING

## Phases

1. Arrange
2. Act
3. Assert (`assert var_name == expected_condition`)

## Commands

1. `brownie test` runs all tests in the tests folder
2. `brownie test -k <module_name> --network <network_name>` skips a module during testing on deployed network that has been flagged with `pytest.skip()`.<br> Removing `--network` skips the module in all tests.

## Mainnet forking

1. add data feed address from Chainlink to brownie-config file `networks` section
2. run deploy or test scripts with `--network mainnet-fork` flag
