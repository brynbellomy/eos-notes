
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