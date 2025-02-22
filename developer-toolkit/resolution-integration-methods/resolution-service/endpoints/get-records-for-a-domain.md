---
title: Get Records for a Domain | Unstoppable Domains Developer Portal
description: This page covers the documentation for the `Get Records for a Domain` endpoint.
---

# Get Records for a Domain

```bash
https://resolve.unstoppabledomains.com/domains/{domain}
```

This endpoint returns all the resolution records configured to a domain in a single response.

## Request Method

* GET

## Authentication

* Bearer Token

## URL Params

| Name | Type | Mandatory | Description |
| - | - | - | - |
| domain | STRING | YES | A domain name registered by Unstoppable Domains. See all the [supported domain endings](../overview.md#supported-domains-endings) |

## Returns

An object with the following fields:

* `meta`: A key-value dictionary with general information about the domain.
    * `domain`: (string) Name of the domain.
    * `tokenId`: (string) The unique identifier of the domain used by smart contracts.
    * `namehash`: (string) The hexadecimal representation of the domain's `token ID`.
    * `owner`: (string) The wallet address that owns the domain.
    * `resolver`: (string) The Resolver smart contract address. This contract is responsible for managing domain records.
    * `registry`: (string) The Registry smart contract address. Registry manages domain ownership, minting domains and subdomains, storing domain metadata, and burning domains. The registry also stores and manages domain records in the Unstoppable Name Service (UNS).
    * `blockchain`: (string) The blockchain the domain is located (MATIC, ETH, ZIL). The blockchain names are coin types according to [SLIP-0044](https://github.com/satoshilabs/slips/blob/master/slip-0044.md).
    * `networkId`: (number) The blockchain network ID.
        * 1 - Ethereum or Zilliqa Mainnet
        * 137 - Polygon (Matic) Mainnet
        * 80001 - Polygon (Matic) Mumbai Testnet
        * 4 - Ethereum Rinkeby Testnet
        * 5 - Ethereum Goerli Testnet
    * `reverse`: (boolean) A boolean indicating if the domain has a reverse record.
* `records`: A key-value dictionary with all domain records set on-chain. This includes wallet addresses and IPFS website hashes. To get more details, visit the Unstoppable Domains [Records Reference](/developer-toolkit/reference/records-reference.md) documentation.

## Example

Here is an example request to query for the records and metadata of the `brad.crypto` domain:

```bash Request
curl \
--request GET 'https://resolve.unstoppabledomains.com/domains/brad.crypto' \
--header 'Authorization: Bearer {SECRET_API_TOKEN}'
```

```json Response
{
    "meta": {
        "domain": "brad.crypto",
        "tokenId": "53115498937382692782103703677178119840631903773202805882273058578308100329417",
        "namehash": "0x756e4e998dbffd803c21d23b06cd855cdc7a4b57706c95964a37e24b47c10fc9",
        "blockchain": "ETH",
        "networkId": 1,
        "owner": "0x8aad44321a86b170879d7a244c1e8d360c99dda8",
        "resolver": "0xb66dce2da6afaaa98f2013446dbcb0f4b0ab2842",
        "registry": "0xd1e5b0ff1287aa9f9a268759062e4ab08b9dacbe",
        "reverse": false
    },
    "records": {
        "ipfs.html.value": "QmTiqc12wo2pBsGa9XsbpavkhrjFiyuSWsKyffvZqVGtut",
        "crypto.ADA.address": "DdzFFzCqrhsuwQKiR3CdQ1FzuPAydtVCBFTRdy9FPKepAHEoXCee2qrio975M4cEbqYwZBsWJTNyrJ8NLJmAReSwAakQEHWBEd2HvSS7",
        "crypto.BTC.address": "bc1q359khn0phg58xgezyqsuuaha28zkwx047c0c3y",
        "crypto.ETH.address": "0x8aaD44321A86b170879d7A244c1e8d360c99DdA8",
        "gundb.username.value": "0x8912623832e174f2eb1f59cc3b587444d619376ad5bf10070e937e0dc22b9ffb2e3ae059e6ebf729f87746b2f71e5d88ec99c1fb3c7c49b8617e2520d474c48e1c",
        "social.picture.value": "1/erc1155:0xc7e5e9434f4a71e6db978bd65b4d61d3593e5f27/14317",
        "gundb.public_key.value": "pqeBHabDQdCHhbdivgNEc74QO-x8CPGXq4PKWgfIzhY.7WJR5cZFuSyh1bFwx0GWzjmrim0T5Y6Bp0SSK0im3nI",
        "ipfs.redirect_domain.value": "https://abbfe6z95qov3d40hf6j30g7auo7afhp.mypinata.cloud/ipfs/Qme54oEzRkgooJbCDr78vzKAWcv6DDEZqRhhDyDtzgrZP6"
    }
}
```

<embed src="/snippets/_discord.md" />
