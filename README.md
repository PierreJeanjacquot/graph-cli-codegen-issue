# `graph codegen` fails with events exposing tuples

## to reproduce

```sh
# clone this repo
git clone git@github.com:PierreJeanjacquot/graph-cli-codegen-issue.git
cd graph-cli-codegen-issue

# install graph-cli
npm install -g @graphprotocol/graph-cli@0.27.0

# run codegen
graph codegen
```

result:

```
✖ Failed to generate types for contract ABIs: Failed to generate types for contract ABI: Conversion from 'AssemblyScript' to 'ethereum' for source type 'BroadcastAppOrderApporderStruct' is not supported
```

here is the event causing the error:

```json
{
  "anonymous": false,
  "inputs": [
    {
      "components": [
        {
          "internalType": "address",
          "name": "app",
          "type": "address"
        },
        {
          "internalType": "uint256",
          "name": "appprice",
          "type": "uint256"
        },
        {
          "internalType": "uint256",
          "name": "volume",
          "type": "uint256"
        },
        {
          "internalType": "bytes32",
          "name": "tag",
          "type": "bytes32"
        },
        {
          "internalType": "address",
          "name": "datasetrestrict",
          "type": "address"
        },
        {
          "internalType": "address",
          "name": "workerpoolrestrict",
          "type": "address"
        },
        {
          "internalType": "address",
          "name": "requesterrestrict",
          "type": "address"
        },
        {
          "internalType": "bytes32",
          "name": "salt",
          "type": "bytes32"
        },
        {
          "internalType": "bytes",
          "name": "sign",
          "type": "bytes"
        }
      ],
      "indexed": false,
      "internalType": "struct IexecLibOrders_v5.AppOrder",
      "name": "apporder",
      "type": "tuple"
    }
  ],
  "name": "BroadcastAppOrder",
  "type": "event"
}
```

## worked with @graphprotocol/graph-cli@0.26.0

```sh
# install graph-cli@26.0.0
npm install -g @graphprotocol/graph-cli@0.26.0

# run codegen
graph codegen
```

result:

```
Types generated successfully
```
