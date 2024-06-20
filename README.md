# setup

copy `config.json.example` to `config.json`

important attribute to change.

```
dry_run: true / false

exchange:{
   name:binance
   key
   secret
   pair_blacklist
}


telegram:{
    enabled
    token
    chat_id
}

api_server:{
    enabled. to be safe, disable them on server
}


```

to determine what pair to trade, we can use [this reference](https://github.com/iterativv/NostalgiaForInfinity/wiki/NFI-Specific-Configs)

we can either do static pair list
btw if you change the config, you don't have to run `docker-compose down` and `docker-compose up` again. you can run `docker-compose restart` to restart the container

# how to update

stop the docker `docker-compose down`

## command to update strategies

```zsh
curl https://raw.githubusercontent.com/iterativv/NostalgiaForInfinity/main/NostalgiaForInfinityX.py -o user_data/strategies/NostalgiaForInfinityX.py
curl https://raw.githubusercontent.com/iterativv/NostalgiaForInfinity/main/NostalgiaForInfinityX4.py -o user_data/strategies/NostalgiaForInfinityX4.py
```

depending on your strategy, change the file name being downloaded. change the startegy used in `docker-compose.yml`

```
    command: >
      trade
      --logfile /freqtrade/user_data/logs/freqtrade.log
      --db-url sqlite:////freqtrade/user_data/tradesv3.sqlite
      --config /freqtrade/user_data/config.json
      --strategy NostalgiaForInfinityX4
```

# how to run locally

have docker installed. run `sudo docker-compose up -d`

that's it!
your should beable to see your project at `localhost:8080`
get the **username and password** from `config.json`
