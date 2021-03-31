# RTM EXPLORER

Сервис предназначен для оповещения клиентов об изменении состояния сети в реальном времени.

### Подключение

#### JS
```html
<script src="//cdn.rawgit.com/centrifugal/centrifuge-js/2.6.4/dist/centrifuge.min.js"></script>
<script type="text/javascript">
    let callbacks = {
        "publish": function (message) {
            // See below description of message format
            console.log(message.data);
        },
        "error": function (errContext) {
            // See below description of subscribe error callback context format
            console.log(err);
        },
    };
    let centrifuge = new Centrifuge("wss://explorer-rtm.minter.network/connection/websocket");
    centrifuge.subscribe("transactions", callbacks);
    centrifuge.connect();
</script>
```


## Status

Канал `status`

Статус сети

```json
{
  "channel": "status",
  "data": {
    "data": {
      "version": "1.2.1-c97913ae",
      "network": "minter-mainnet-3",
      "latest_block_hash": "E65331B684DD7F51FDE8F18900B20521175EAAAAD691DDAF65E69DE3AC8A1C80",
      "latest_app_hash": "2F84CCD784175601A1FAD04AF0716B088D8CE0D91D9007854713BEF2A1B13A60",
      "latest_block_height": 3030742,
      "latest_block_time": "2021-03-30T10:18:30.643932527+02:00",
      "keep_last_states": 1000000,
      "total_slashed": "15748995617969827843118949",
      "public_key": "Mpafbb3473feebb10d0fd9bc357a123056401e8962b3a2756bc2807abbb15456a0",
      "node_id": "67b222c3d751305a9edec2c8b78976626513b8c8"
    }
  }
}
```

## Blocks

Канал `blocks`

Информация о текущем блоке

```json
{
  "result": {
    "channel": "blocks",
    "data": {
      "data": {
        "height": 3030758,
        "size": 5332,
        "transaction_count": 1,
        "block_time": 4.537886419,
        "timestamp": "2021-03-30T08:19:43Z",
        "reward": "273.000000000000000000",
        "hash": "Mh4dc6a374b07fab0f2f82c20806fe7628f2ea5cfe2932928529ad638ce51c858f",
        "validators_count": 44
      }
    }
  }
}
```

## Transactions

Канал `transactions`

Транзакции сети

```json
{
  "result": {
    "channel": "transactions",
    "data": {
      "data": {
        "txn": 1290596,
        "hash": "Mt77a733714d13d78921e3f1576b239df605c374f10a9c38aa75e335eb84a6340e",
        "nonce": 5,
        "height": 3031419,
        "timestamp": "2021-03-30T09:10:11Z",
        "gas": "10",
        "gas_price": 1,
        "fee": "0.010000000000000000",
        "type": 1,
        "payload": "",
        "from": "Mx919e7a5884df00f419c2068f8fa2b17f1d5fd70a",
        "data": {
          "coin": {
            "id": 0,
            "symbol": "BIP"
          },
          "to": "Mxe396f678a50736ec5e4d3d1f7854bb020d22fd12",
          "value": "2891.517117960000000000"
        },
        "raw_tx": "f8710501018001a1e08094e396f678a50736ec5e4d3d1f7854bb020d22fd12899cbfdc6adecf125000808001b845f8431ba0dbd5b45309a598c7118b51ef8ad826694cca0c33e6dffcfe600d3f517bbc22a6a05e066892e5211421157db9d75cb69d064d240ca27e2ce20829960cb16a953f50"
      }
    }
  }
}
```

## Commissions

Канал `commissions`

Информация об изменененных коммиссиях

```json
{
  "result": {
    "channel": "commissions",
    "data": {
      "data": {
        "add_liquidity": "20000000000",
        "create_token": "10000000000"
      }
    }
  }
}
```

## Stake

Канал `stake/Mx....`
Пример `stake/Mxe396f678a50736ec5e4d3d1f7854bb020d22fd12`

Информация об изменении стейка по адресу. В сообщении приходит значение в пипах на который изменился стейк. В случае
анбонда может быть отрицательным.

```json
{
  "result": {
    "channel": "stake/Mx....",
    "data": {
      "data": "10000000000"
    }
  }
}
```

## Balance

Канал `Mx....`

Информация об изменении баланса по адресу

```json
{
  "result": {
    "channel": "Mxe4f9bb2cb1ca13b5a6f2aa0b58b4ab0c43892100",
    "data": {
      "data": [
        {
          "coin": {
            "id": 291,
            "symbol": "TRADERS"
          },
          "amount": "120.000000000000000000",
          "bip_amount": "0.616041922247978224"
        },
        {
          "coin": {
            "id": 0,
            "symbol": "BIP"
          },
          "amount": "131.289074377930230819",
          "bip_amount": "131.289074377930230819"
        }
      ]
    }
  }
}
```

