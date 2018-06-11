
Connect to a local network
```js
let EOS = require('eosjs')

let eos = EOS.Localnet({
    chainId:"a4fe43c897279a677025624555f3835b949f995f87923c97f0392dcff835bfd0",
    keyProvider:['5KcHE3HF4zAecKWFxBiizG3KBPpkBxbbMDAn1HPeHQZecy69bZy','5KQVzEFg4PbDNtCbdhbfgwfaqQYPNzhjna3ZCm5AzrFZCpeoccg'],
    httpEndpoint:'http://127.0.0.1:8888',
})
```

Interact with a contract
```js
let contract = await eos.contract('child.acnt')
let res = await contract.ping('child.acnt', { authorization: ['child.acnt'] })
console.log(res)
```

Fetch a row from a table
```js
eos.getTableRows({
    json: true,
    scope: account,
    code: contract,
    table: table,
    limit: 1,
    lower_bound: id,
    upper_bound: id + 1,
}).then(res => { let row = res.rows[0] })
```


Create a token
```js
async createToken(maxSupply) {
    try {
        const tokenContract = await eos.contract("eosio.token")
        const transaction = await tokenContract.create({
            issuer: "randyt",
            maximum_supply: "100.0000 IOS",
        })

        return transaction
    } catch (error) {
        console.error(error)
    }
}
```