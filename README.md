<div align="center">
  
# Sei validator node on Akash Network
  
# Нода валидатора сети Sei, развертка в Akash Network.

<p align="center"><img src="https://user-images.githubusercontent.com/23629420/163564929-166f6a01-a6e2-4412-a4e9-40e54c821f05.png" width=70% </p>

| [Akash Network](https://akash.network/) | [Forum Akash Network](https://forum.akash.network/) | 
|:--:|:--:|
___
Before you start - subscribe to our news channels: 

Прежде чем начать - подпишитесь на наши новостные каналы:

| [Discord Akash](https://discord.gg/3SNdg3BS) | [Telegram Akash EN](https://t.me/AkashNW) | [Telegram Akash RU](https://t.me/akash_ru) | [TwitterAkash](https://twitter.com/akashnet_) | [TwitterAkashRU](https://twitter.com/akash_ru) |
|:--:|:--:|:--:|:--:|:--:|

</div>
<div align="center">
  
| [Discord Sei](https://discord.gg/3A3TdWfF) | [Explorer Sei](https://sei.explorers.guru/) | [Site Sei](https://www.seinetwork.io/) | [Twitter Sei](https://twitter.com/SeiNetwork) |
|:--:|:--:|:--:|:--:|
  
<div align="center">
  
[English version](https://github.com/Dimokus88/Sei/tree/main#english-version) | [Русская версия](https://github.com/Dimokus88/Sei/tree/main#%D1%80%D1%83%D1%81%D1%81%D0%BA%D0%B0%D1%8F-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D1%8F) 
 
</div>
  
</div>

___

# English version
### Deployment of the Sei node.

Deploy [deploy.yml](https://github.com/Dimokus88/Sei/blob/main/deploy.yml) **Sei** nodes with **Cloudmos (Akashlytics)** ( [use instructions here](https://github.com/Dimokus88/guides/blob/main/Akashlytics/EN-guide.md) ) by setting the values ​​in the corresponding `deploy.yml` variables:
- **my_root_password** - your password for the `root` user.
- **MONIKER**-node name.
- **LINK_KEY**-link to direct download of `priv_validator_key.json`* file.

If you don't have a `priv_validator_key.json` or want to know how to get a direct download link, refer to [this guide](https://github.com/Dimokus88/guides/blob/main/Cosmos%20SDK/valkey/README_EN.md).

> *If you want to deploy an **RPC** node without a validator key, leave `LINK_KEY` blank or remove this line altogether. The node will run on the generated `priv_validator_key.json`.

At this stage, the node is deployed. Navigating to the forwarded port **26657** in the `LEASES` tab, the `websocket` of the node will open, where its up-to-date information will be available. If you need to **create** a validator on your `priv_validator_key.json` go to the next step.

<div align="center">

<p align="center"><img src="https://user-images.githubusercontent.com/23629420/182032797-70a74454-75dd-4910-8a30-9a88a1715531.png" width=45% align="left"</p>
<p align="center"><img src="https://user-images.githubusercontent.com/23629420/182032818-069eef95-8242-459f-b503-ad8322261482.png" width=45% </p>

</div>

### Creating an Sei validator

Connect to the running node via **SSH** using forwarded port **22**, user **root** and the password you set in **deploy.yml**:
  
<p align="center"><img src="https://user-images.githubusercontent.com/23629420/182032966-3fa2ffae-5348-4a2c-a4e8-5d33c57ba320.png" width=60% </p>

Check sync status, if `false` means the node is **synced**:
  
```
curl -s localhost:26657/status | jq .result.sync_info.catching_up
```

If the node is **synchronized** - run:

```
source ~/.bashrc && wget -q -O $binary.sh https://raw.githubusercontent.com/Dimokus88/universe/main/script/create_validator.sh && chmod +x $binary.sh && sudo /bin/bash $binary.sh
```

Follow the script execution prompts.

When the validator is created, request the remaining balance:

```
$binary q bank balances $address
```

You can delegate the remaining tokens to yourself, but leave 1,000,000 usei to pay for transaction gas:

```
$binary tx staking delegate $valoper <amount>$denom --from $address --chain-id $chain --fees 555$denom -y
```

Collect rewards:

```
$binary tx distribution withdraw-rewards $valoper --from $address --fees 500$denom --commission --chain-id $chain -y
```
Other commands for managing a node [can be found here](https://github.com/Dimokus88/guides/blob/main/Cosmos%20SDK/COMMAND.MD).

[Back to top](https://github.com/Dimokus88/Sei/blob/main/README.md#Sei-validator-node-on-akash-network)

**Thank you for using Akash Network!**

___
# Русская версия
### Развертка ноды Sei.

Разверните [deploy.yml](https://github.com/Dimokus88/Sei/blob/main/deploy.yml) ноды **Sei** с помощью **Cloudmos (Akashlytics)**  ([инструкция по использованию здесь](https://github.com/Dimokus88/guides/blob/main/Akashlytics/RU-guide.md)) установив значения в соответствующих переменных  `deploy.yml`: 
- **my_root_password**-свой пароль для `root` пользователя
- **MONIKER**-имя ноды  
- **LINK_KEY**-ссылку на прямое скачивание файла `priv_validator_key.json`* 

Если у вас нет `priv_validator_key.json` или вы хотите знать, как получить ссылку на прямое скачивание - обратитесь [к этой инструкции](https://github.com/Dimokus88/guides/blob/main/Cosmos%20SDK/valkey/README_RU.md). 

> *Если вы хотите развернуть **RPC** ноду без ключа валидатора - оставьте `LINK_KEY` пустым или вовсе удалите эту строку. Нода запустится на сгенерированном `priv_validator_key.json`. 

На данном этапе нода развернута . Перейдя на переадресованный порт **26657** во вкладке `LEASES` откроется `websocket` ноды, где будет доступна ее актуальная информация. Если вам нужно **создать** валидатора на вашем `priv_validator_key.json` перейдите к следующему пункту.

<div align="center">

<p align="center"><img src="https://user-images.githubusercontent.com/23629420/182032797-70a74454-75dd-4910-8a30-9a88a1715531.png" width=45% align="left"</p>
<p align="center"><img src="https://user-images.githubusercontent.com/23629420/182032818-069eef95-8242-459f-b503-ad8322261482.png" width=45% </p>

</div>

### Создание валидатора Sei

Подключитесь к работающей ноде по протоколу **SSH**, используя переадресованный **22** порт, пользователь **root** и пароль заданный вами в **deploy.yml**:
  
<p align="center"><img src="https://user-images.githubusercontent.com/23629420/182032966-3fa2ffae-5348-4a2c-a4e8-5d33c57ba320.png" width=60% </p>
  
Проверьте статус синхронизации, если `false` значит нода **синхронизированна**:
  
```
curl -s localhost:26657/status | jq .result.sync_info.catching_up
```

Если нода **синхронизированна** - выполните:

```
source ~/.bashrc && wget -q -O $binary.sh https://raw.githubusercontent.com/Dimokus88/universe/main/script/create_validator.sh && chmod +x $binary.sh && sudo /bin/bash $binary.sh
```

Следуйте подсказкам выполнения скрипта.

Когда валидатор будет создан запросите оставшийся баланс:

```
$binary q bank balances $address
```

Можете делегировать на себя оставшиеся токены, но оставьте 1 000 000 usei для оплаты газа транзакций:

```
$binary tx staking delegate $valoper <amount>$denom --from $address --chain-id $chain --fees 555$denom -y
```

* Собрать награды:

```
$binary tx distribution withdraw-rewards $valoper --from $address --fees 500$denom --commission --chain-id $chain -y
```
Другие команды по управлению нодой [можете найти здесь](https://github.com/Dimokus88/guides/blob/main/Cosmos%20SDK/COMMAND.MD).

[К началу](https://github.com/Dimokus88/Sei/blob/main/README.md#Sei-validator-node-on-akash-network)

**Спасибо что воспользовались Akash Network!**
___


