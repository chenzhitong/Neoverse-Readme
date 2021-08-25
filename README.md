# Neoverse Contract

**2021/8/23** Neoverse

Neo 3.0 Testnet: 

Script Hash: 0xd41cdd7d5dc9024bd6857073175b9a39f3b9c21a

Address: NNMU2ZwYKogK3jh8QaKNLyFYLubRwjTGbo

Owner: NSuyiLqEfEQZsLJawCbmXW154StRUwdWoM

**2021/8/12**（2）BlindBox

Neo 3.0 Testnet: 

Script Hash: 0x2bcc9c9ad6626396f507f088c5ae06ebf6fa5efa

Address: NdHmtPcQdwPVYqBfKeBuwAHKhkVKFoiow6

Owner: Nijou4aogcbVvVfGGtu8eycTYqPsquKCHf

**2021/8/12** BlindBox

Neo 3.0 Testnet: 

Script Hash: 0xe16e6e13d17f491ad59adcb76a2e90a472db99be

Address: NdHmtPcQdwPVYqBfKeBuwAHKhkVKFoiow6

Owner: NSuyiLqEfEQZsLJawCbmXW154StRUwdWoM

**2021/8/11** BlindBox

Neo 3.0 Testnet: 

Script Hash: 0x3d50c5ecc2df22ad95ea15aaf398f9cdcaa7fb53

Address: NTa2k1Cc9eTbs6Em9FRnxxy2coq2SotyGb

Owner: NSuyiLqEfEQZsLJawCbmXW154StRUwdWoM

**2021/8/10 **BlindBox

Neo 3.0 Testnet: 

Script Hash: 0x29a880b9381714d3dc9124ebd934a3642de048c0

Address: NdSgE5Yy4ZXvXmvqHDr7WuiJiBju3GWvEB

Owner: NSuyiLqEfEQZsLJawCbmXW154StRUwdWoM

**2021/8/8 **BlindBox

Neo 3.0 Testnet: 

Script Hash: 0x4af0b52d128d0b7bdbccc459147a46a354cf9250

Address: NTG17dcRWwxmM6eyPGvrJcyD8PwkBKWTDr

Owner: NSuyiLqEfEQZsLJawCbmXW154StRUwdWoM

[English](#en) [中文](#zh)

<a name="en"></a>

## Methods and Events

### NEP-11 Methods

| name                             | parameter                                              | return           | description                                                  |
| -------------------------------- | ------------------------------------------------------ | ---------------- | ------------------------------------------------------------ |
| symbol                           | --                                                     | String           | Return string "N3"                                           |
| decimals                         | --                                                     | Integer          | Returns an integer 0                                         |
| totalSupply                      | --                                                     | Integer          | totalSupply = totalMint - totalBurn                          |
| balanceOf                        | Hash160（owner）                                       | Integer          | The total number of blind boxes, fragments, and cards for the user |
| ownerOf                          | ByteArray（tokenId）                                   | Hash160          | Find the owner of a blind box, fragment, card                |
| [properties](#查询-nft-属性)     | ByteArray（tokenId）                                   | Map              | Query the properties of a token                              |
| [tokens](#查询所有-NFT)          |                                                        | InteropInterface | Check all issued blind boxes, fragments, cards               |
| [tokensOf](#查询用户的-nft-资产) | Hash160（owner）                                       | InteropInterface | Query a blind box, fragment, card that someone owns          |
| [transfer](#转账)                | Hash160（to）<br/>ByteArray（tokenId）<br/>Any（data） | Boolean          |                                                              |

### Customization Method

| name | parameter | return | description | remark |
| ------- | ---- | ------ | ------------ | ---- |
| pause   |      | Boolean | Suspend the sale of blind boxes | administrator |
| resume  |      | Boolean | Resume selling blind boxes | administrator |
| airdrop | Hash160（to）<br/>Integer（amount） | Boolean | Air drop blind box | administrator |
| isPaused       |      | Boolean | Check the status of the selling blind box |      |
| getToken | ByteArray（tokenId） | TokenState | Query the full properties of a token | |
| [onNEP17Payment](#购买盲盒-2个gas) | Hash160（from）<br/>Integer（amount）<br/>Any（_） | void | Buy blind box<br/>GAS→blind box |      |
| [unBoxing](#开盲盒) | ByteArray（tokenId） | Boolean | Open the blind box<br/>blind box→fragments |      |
| [compound](#合成) | Array（tokenList） | Boolean | Compound Card<br/>fragments→Card |      |
| totalMint | Integer（firstType）<br/>Integer（secondType） | Integer | Get total Mint of one type of tokens. |      |

### event

| name     | parameter                                                    | description    | remark                                                       |
| -------- | ------------------------------------------------------------ | -------------- | ------------------------------------------------------------ |
| transfer | Hash160（from）<br/>Hash160（to）<br/>Integer（amount）<br/>ByteArray（tokenId） | Transfer event | from is null: Mint<br/>to is null: Burn<br/>amount is always 1 |



<a name="zh"></a>

## 方法和事件

### NEP-11 方法

| 名称                             | 参数                                                   | 返回值           | 说明                                                         |
| -------------------------------- | ------------------------------------------------------ | ---------------- | ------------------------------------------------------------ |
| symbol                           | --                                                     | String           | 返回字符串 "N3"                                              |
| decimals                         | --                                                     | Integer          | 返回整数 0                                                   |
| totalSupply                      | --                                                     | Integer          | 已发行的盲盒、碎片、卡牌的总量<br/>totalSupply = totalMint - totalBurn |
| balanceOf                        | Hash160（owner）                                       | Integer          | 该用户盲盒、碎片、卡牌的总量                                 |
| ownerOf                          | ByteArray（tokenId）                                   | Hash160          | 查询某个盲盒、碎片、卡牌的所有者                             |
| [properties](#查询-nft-属性)     | ByteArray（tokenId）                                   | Map              | 查询某个盲盒、碎片、卡牌的属性                               |
| [tokens](#查询所有-NFT)          |                                                        | InteropInterface | 查询所有已发行的盲盒、碎片、卡牌                             |
| [tokensOf](#查询用户的-nft-资产) | Hash160（owner）                                       | InteropInterface | 查询某个人拥有的盲盒、碎片、卡牌                             |
| [transfer](#转账)                | Hash160（to）<br/>ByteArray（tokenId）<br/>Any（data） | Boolean          |                                                              |

### 自定义方法

| 名称                               | 参数                                               | 返回值     | 说明                        | 备注   |
| ---------------------------------- | -------------------------------------------------- | ---------- | --------------------------- | ------ |
| pause                              |                                                    | Boolean    | 暂停售卖盲盒                | 管理员 |
| resume                             |                                                    | Boolean    | 恢复售卖盲盒                | 管理员 |
| airdrop                            | Hash160（to）<br/>Integer（amount）                | Boolean    | 空投盲盒                    | 管理员 |
| isPaused                           |                                                    | Boolean    | 查询售卖盲盒的状态          |        |
| getToken                           | ByteArray（tokenId）                               | TokenState | 查询 Token 详情             |        |
| [onNEP17Payment](#购买盲盒-2个gas) | Hash160（from）<br/>Integer（amount）<br/>Any（_） | void       | 购买盲盒<br/>GAS→盲盒       |        |
| [unBoxing](#开盲盒)                | ByteArray（tokenId）                               | Boolean    | 开盲盒<br/>盲盒→碎片        |        |
| [compound](#合成)                  | Array（tokenList）                                 | Boolean    | 合约卡牌<br/>碎片→卡牌      |        |
| totalMint                          | Integer（firstType）<br/>Integer（secondType）     | Integer    | 查询某类 Token 已铸币的数量 |        |

### 事件

| 名称     | 参数                                                         | 说明     | 备注                                                         |
| -------- | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| transfer | Hash160（from）<br/>Hash160（to）<br/>Integer（amount）<br/>ByteArray（tokenId） | 转账事件 | from 为 null 即铸币<br/>to 为 null 即销毁<br/>amount 始终为 1 |

## RPC Call example

### Buy a blind box (2 GAS)

#### CLI command

send two GAS to Neoverse contract, e.g.

```
send gas NNMU2ZwYKogK3jh8QaKNLyFYLubRwjTGbo 2
```

#### RPC command

RPC Request

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "invokefunction",
    "params": [
        "0xd2a4cff31913016155e38e474a2c06d08be276cf", //GAS
        "transfer",
        [
            {
                "type": "Hash160",
                "value": "Script hash of your own address"
            },
            {
                "type": "Hash160",
                "value": "Script hash of Neoverse contract"
            },
            {
                "type": "Integer",
                "value": "200000000"
            },
            {
                "type": "String",
                "value": ""
            }
        ],
        [
            {
                "account": "Script hash of your own address",
                "scopes": "CalledByEntry",
                "allowedcontracts": [],
                "allowedgroups": []
            }
        ]
    ]
}
```

### Get log of buy blind box

RPC Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getapplicationlog",
  "params": [
    "0x35a5ac953443922ad241615b911cee1adfa40cbb2f835c9020892353cdb0219a"
  ]
}
```

RPC Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0x35a5ac953443922ad241615b911cee1adfa40cbb2f835c9020892353cdb0219a",
        "executions": [
            {
                "trigger": "Application",
                "vmstate": "HALT",
                "exception": null,
                "gasconsumed": "51982780",
                "stack": [
                    {
                        "type": "Boolean",
                        "value": true
                    }
                ],
                "notifications": [
                    {
                        "contract": "0xd2a4cff31913016155e38e474a2c06d08be276cf",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "ByteString",
                                    "value": "tr4BR1ZlII/YJLYgR2zzcOKZAwU="
                                },
                                {
                                    "type": "Integer",
                                    "value": "200000000"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "QmxpbmQgQm94IDE="
                                }
                            ]
                        }
                    }
                ]
            }
        ]
    }
}
```

### Get NFT properties

RPC Request

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "invokefunction",
    "params": [
        "Script hash of Neoverse contract",
        "properties",
        [
            {
                "type": "ByteArray",
                "value": "QmxpbmQgQm94IDE="
            }
        ]
    ]
}
```

RPC Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "script": "DAtCbGluZCBCb3ggMRHAHwwKcHJvcGVydGllcwwUp+Z/jWYy6X4RYXJsxbpMo6/tNCdBYn1bUg==",
        "state": "HALT",
        "gasconsumed": "6559560",
        "exception": null,
        "stack": [
            {
                "type": "Map",
                "value": [
                    {
                        "key": {
                            "type": "ByteString",
                            "value": "bmFtZQ=="
                        },
                        "value": {
                            "type": "ByteString",
                            "value": "QmxpbmQgQm94IDE="
                        }
                    },
                    {
                        "key": {
                            "type": "ByteString",
                            "value": "b3duZXI="
                        },
                        "value": {
                            "type": "ByteString",
                            "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                        }
                    },
                    {
                        "key": {
                            "type": "ByteString",
                            "value": "Zmlyc3RUeXBl"
                        },
                        "value": {
                            "type": "Integer",
                            "value": "0"
                        }
                    },
                    {
                        "key": {
                            "type": "ByteString",
                            "value": "c2Vjb25kVHlwZQ=="
                        },
                        "value": {
                            "type": "Integer",
                            "value": "0"
                        }
                    },
                    {
                        "key": {
                            "type": "ByteString",
                            "value": "bnVtYmVy"
                        },
                        "value": {
                            "type": "Integer",
                            "value": "1"
                        }
                    },
                    {
                        "key": {
                            "type": "ByteString",
                            "value": "cmFuZG9tSW5kZXg="
                        },
                        "value": {
                            "type": "Integer",
                            "value": "189"
                        }
                    },
                    {
                        "key": {
                            "type": "ByteString",
                            "value": "aW1hZ2U="
                        },
                        "value": {
                            "type": "ByteString",
                            "value": "aHR0cHM6Ly9uM2JhZGdlcy5uZW8ub3JnLzAwLnBuZw=="
                        }
                    }
                ]
            }
        ]
    }
}
```

UInt160 Owner;

string Name;

byte FirstType;      //0 Blind Box; 1 Fragment; 2 Card

byte SecondType;     //Blind Box: 0, Fragment A-I: 0-8, Card N、E、O: 0-2

BigInteger Number;   //Number of Blind Box / Fragment / Card 

uint RandomIndex;    //The block index where the random number is located, 0 means no randomness

string Image;

string Video;

### Querying a user's NFT assets

RPC Request

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "invokefunction",
    "params": [
        "Script hash of Neoverse contract",
        "tokensOf",
        [
            {
                "type": "ByteArray",
                "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
            }
        ]
    ]
}
```

RPC Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "script": "DBRJmBt4siqvHVseGXu3tNeYg+it5xHAHwwIdG9rZW5zT2YMFLa+AUdWZSCP2CS2IEds83DimQMFQWJ9W1I=",
        "state": "HALT",
        "gasconsumed": "2724540",
        "exception": null,
        "stack": [
            {
                "type": "InteropInterface",
                "iterator": [
                    {
                        "type": "ByteString",
                        "value": "QmxpbmQgQm94IDE="
                    }
                ],
                "truncated": false
            }
        ]
    }
}
```

### Open the blind box

RPC Request

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "invokefunction",
    "params": [
        "Script hash of Neoverse contract",
        "unBoxing",
        [
            {
                "type": "ByteArray",
                "value": "QmxpbmQgQm94IDE="
            }
        ],
        [
            {
                "account": "0xe7ade88398d7b4b77b191e5b1daf2ab2781b9849",
                "scopes": "CalledByEntry",
                "allowedcontracts": [],
                "allowedgroups": []
            }
        ]
    ]
}
```

RPC Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "script": "DAtCbGluZCBCb3ggMRHAHwwIdW5Cb3hpbmcMFBf5/gY4g3F7QUaAgc826xx0ehWbQWJ9W1I=",
        "state": "HALT",
        "gasconsumed": "74975300",
        "exception": null,
        "stack": [
            {
                "type": "Boolean",
                "value": true
            }
        ],
        "tx": "APMIbF1ECHgEAAAAABg6EgAAAAAAABgAAAFJmBt4siqvHVseGXu3tNeYg+it5wEANQwLQmxpbmQgQm94IDERwB8MCHVuQm94aW5nDBQX+f4GOINxe0FGgIHPNuscdHoVm0FifVtSAUIMQFIabPbU9rqwS0/0ct/PPEUfZMR1a41yfdKNpeUJwb+Azv7/dwkCzmzxNPy+dc6fstaDxP5qcTmXf7NDinwxFIAoDCEChg/5yRX1ZfSUJrzN2QgjhR1ohDGD0mHrYjG3+79VnoVBVuezJw=="
    }
}
```

Send raw transaction

……

Get application log

……

### Compound

RPC Request

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "invokefunction",
    "params": [
        "Script hash of Neoverse contract",
        "compound",
        [
            {
                "type": "Array",
                "value": [
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgQSAxMDAw"
                    },
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgQiAxMDAw"
                    },
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgQyAxMDAw"
                    },
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgRCAxMDAw"
                    },
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgRSAxMDAw"
                    },
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgRiAxMDAw"
                    },
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgRyAxMDAw"
                    },
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgSCAxMDAw"
                    },
                    {
                        "type": "ByteArray",
                        "value": "RnJhZ21lbnQgSSAxMDAw"
                    }
                ]
            }
        ],
        [
            {
                "account": "0xe7ade88398d7b4b77b191e5b1daf2ab2781b9849",
                "scopes": "CalledByEntry",
                "allowedcontracts": [],
                "allowedgroups": []
            }
        ]
    ]
}
```

RPC Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "script": "DA9GcmFnbWVudCBJIDEwMDAMD0ZyYWdtZW50IEggMTAwMAwPRnJhZ21lbnQgRyAxMDAwDA9GcmFnbWVudCBGIDEwMDAMD0ZyYWdtZW50IEUgMTAwMAwPRnJhZ21lbnQgRCAxMDAwDA9GcmFnbWVudCBDIDEwMDAMD0ZyYWdtZW50IEIgMTAwMAwPRnJhZ21lbnQgQSAxMDAwGcARwB8MCGNvbXBvdW5kDBS1L5/xd2yXD345sZdi9AakbZUGmEFifVtS",
        "state": "HALT",
        "gasconsumed": "195275520",
        "exception": null,
        "stack": [
            {
                "type": "Boolean",
                "value": true
            }
        ],
        "tx": "APKBxmMAq6MLAAAAAMhkFAAAAAAAvU8AAAFJmBt4siqvHVseGXu3tNeYg+it54AAwwwPRnJhZ21lbnQgSSAxMDAwDA9GcmFnbWVudCBIIDEwMDAMD0ZyYWdtZW50IEcgMTAwMAwPRnJhZ21lbnQgRiAxMDAwDA9GcmFnbWVudCBFIDEwMDAMD0ZyYWdtZW50IEQgMTAwMAwPRnJhZ21lbnQgQyAxMDAwDA9GcmFnbWVudCBCIDEwMDAMD0ZyYWdtZW50IEEgMTAwMBnAEcAfDAhjb21wb3VuZAwUtS+f8Xdslw9+ObGXYvQGpG2VBphBYn1bUgFCDEBMCiophp7+hSj/f8f0o7FJv/XqNa5Ykjxtvc4ngKDRQKIWqqIPPFDKgtV/ahXNBWKsuUXsegmQ7S6XlfzMGizHKAwhAoYP+ckV9WX0lCa8zdkII4UdaIQxg9Jh62Ixt/u/VZ6FQVbnsyc="
    }
}
```

Application log

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0x6286199a4ad5b1cf4521ac0c506b72b55b110056cab79e359a1551d9866d6058",
        "executions": [
            {
                "trigger": "Application",
                "vmstate": "HALT",
                "exception": null,
                "gasconsumed": "194535500",
                "stack": [
                    {
                        "type": "Boolean",
                        "value": true
                    }
                ],
                "notifications": [
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgQSAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgQiAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgQyAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgRCAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgRSAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgRiAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgRyAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgSCAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "RnJhZ21lbnQgSSAxMDAw"
                                }
                            ]
                        }
                    },
                    {
                        "contract": "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
                        "eventname": "Transfer",
                        "state": {
                            "type": "Array",
                            "value": [
                                {
                                    "type": "Any"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "SZgbeLIqrx1bHhl7t7TXmIPorec="
                                },
                                {
                                    "type": "Integer",
                                    "value": "1"
                                },
                                {
                                    "type": "ByteString",
                                    "value": "TjMgR29sZCBDYXJkIDE="
                                }
                            ]
                        }
                    }
                ]
            }
        ]
    }
}
```

### Transfer

RPC Request

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "invokefunction",
    "params": [
        "Script hash of Neoverse contract",
        "transfer",
        [
            {
                "type": "Hash160",
                "value": "接收方的地址的脚本哈希"
            },
            {
                "type": "ByteArray",
                "value": "QmxpbmQgQm94IDE=" //TokenId
            },
            {
                "type": "String",
                "value": ""
            }
        ],
        [
            {
                "account": "Script hash of your own address",
                "scopes": "CalledByEntry",
                "allowedcontracts": [],
                "allowedgroups": []
            }
        ]
    ]
}
```

RPC Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "script": "DAAMC0JsaW5kIEJveCAxDBRjqxOu9W+zBPVm2OXoHYkoIJTVlhPAHwwIdHJhbnNmZXIMFFCSz1SjRnoUWcTM23sLjRIttfBKQWJ9W1I=",
        "state": "HALT",
        "gasconsumed": "12934940",
        "exception": null,
        "stack": [
            {
                "type": "Boolean",
                "value": true
            }
        ],
        "tx": "AGfko00cX8UAAAAAAOxLCQAAAAAALq4BAAFMyVIZmZ1CEkPIFh4/wPQpDAZ4RQEATQwADAtCbGluZCBCb3ggMQwUY6sTrvVvswT1Ztjl6B2JKCCU1ZYTwB8MCHRyYW5zZmVyDBRQks9Uo0Z6FFnEzNt7C40SLbXwSkFifVtSAUIMQEXlepaPYpZcf+UnaIRXYzn2iXXsy8lHlsNXvZ5BlGx650s2dhj11BEUiyoJvVIQWr8QqxKaeVzWDrQPBOmSJ2EoDCECe46EiX3N/ny99+bXtp3bbt1jI8vnMupo3Ss9RKgOgPBBVuezJw=="
    }
}
```

### Get all NFT

RPC Request

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "invokefunction",
    "params": [
        "0x4af0b52d128d0b7bdbccc459147a46a354cf9250",
        "tokens",
        []
    ]
}
```

RPC Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "script": "wh8MBnRva2VucwwUUJLPVKNGehRZxMzbewuNEi218EpBYn1bUg==",
        "state": "HALT",
        "gasconsumed": "1454130",
        "exception": null,
        "stack": [
            {
                "type": "InteropInterface",
                "iterator": [
                    {
                        "type": "ByteString",
                        "value": "QmxpbmQgQm94IDE="
                    },
                    {
                        "type": "ByteString",
                        "value": "QmxpbmQgQm94IDI="
                    },
                    {
                        "type": "ByteString",
                        "value": "QmxpbmQgQm94IDM="
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgQSAxMDAw"
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgQiAxMDAw"
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgQyAxMDAw"
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgRCAxMDAw"
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgRSAxMDAw"
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgRiAxMDAw"
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgRyAxMDAw"
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgSCAxMDAw"
                    },
                    {
                        "type": "ByteString",
                        "value": "RnJhZ21lbnQgSSAxMDAw"
                    }
                ],
                "truncated": false
            }
        ]
    }
}
```
