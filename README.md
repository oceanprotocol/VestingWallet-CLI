# VestingWallet CLI

CLI for wallet contracts with vesting functionality. Based on OpenZeppelin's VestingWallet.sol.

Functionality is via `vw` tool:

```text
vw new_TYPE - deploy new wallet with TYPE = cliff, linear, or exponential vesting
vw transfer - transfer funds to wallet
vw release - request vesting wallet to release funds
..
```

Other features:

- Via [brownie](https://eth-brownie.readthedocs.io/en/latest/), easy to interact with contract in console
- Thorough unit tests

# Installation

Ensure pre-requisites:

- Linux/MacOS
- Python 3.8.5+
- solc 0.8.0+ [[Instructions](https://docs.soliditylang.org/en/v0.8.9/installing-solidity.html)]
- ganache. To install: `npm install ganache-cli --global`

Now, open a new terminal and:

```console
#clone repo
git clone https://github.com/oceanprotocol/vw-cli.git
cd vw-cli

#create a virtual environment
python -m venv venv

#activate env
source venv/bin/activate

#install dependencies
pip install -r requirements.txt

#install openzeppelin library, to import from .sol (ignore FileExistsErrors)
brownie pm install OpenZeppelin/openzeppelin-contracts@2.1.1
brownie pm install OpenZeppelin/openzeppelin-contracts@4.0.0
```

# Main Usage: CLI

First, compile. From terminal:

```console
brownie compile
```

The `vw` CLI needs needs a chain to persist between commands: either a remote chain, or a separate local process (vs one auto-started for each command). To run a local chain, open a new terminal and:

```
ganache-cli
```

Then, in the main terminal:

```console
#add pwd to bash path
export PATH=$PATH:.

#see vw help
vw
```

**Then, simply follow the usage directions:)**

# Other Usage

## Running Tests

In terminal:

```console
#run one test
brownie test tests/test_Simpletoken.py::test_transfer

#run tests for one module
brownie test tests/test_Simpletoken.py

#run all tests
brownie test
```

## Brownie Console

From terminal:

```console
brownie console
```

In brownie console:

```python
>>> t = Simpletoken.deploy("TEST", "Test Token", 18, 100, {'from': accounts[0]})
Transaction sent: 0x3f113379b70d00041068b27733c37c2977354d8c70cb0b30b0af3087fca9c2b8
  Gas price: 0.0 gwei   Gas limit: 6721975   Nonce: 0
  Simpletoken.constructor confirmed   Block: 1   Gas used: 551616 (8.21%)
  Simpletoken deployed at: 0x3194cBDC3dbcd3E11a07892e7bA5c3394048Cc87

>>> t.symbol()
'TEST'
```

# License

    Copyright ((C)) 2022 Ocean Protocol Foundation

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
