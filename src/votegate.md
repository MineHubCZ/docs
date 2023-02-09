# Dokumentace použití API VoteGate

Každý požadavek na API musí být autorizován tokenem nastaveným v `.env`
souboru. Token se předává jako GET parametr pod klíčem `token`.

## Endpointy

### Informace o serveru

[ GET ]{.badge .bg-secondary} `/api`

Vrací objekt, kde klíč je název [hlasovací služby](#services) a hodnota
je [objekt ServerInfo](#serverinfo) nebo `null` v případě selhání
načtení dat.

##### Příklad

`/api`

```json
{
    "CZECH_CRAFT": {
        "position": 19,
        "votes_count": 1490,
        "url": "https://czech-craft.eu/server/minehub"
    },
    "CRAFTLIST": {
        "position": 32,
        "votes_count": 997,
        "url": "https://craftlist.org/minehubcz"
    },
    "MINECRAFT_LIST": {
        "position": 16,
        "votes_count": 3608,
        "url": "https://www.minecraft-list.cz/server/minehubcz"
    },
    "MINECRAFTSERVERY": {
        "position": null,
        "votes_count": 1026,
        "url": "https://minecraftservery.eu/server/minehubcz"
    }
}
```

### Informace o hráči

`GET /api/{nick}`

Vrací objekt, kde klíč je název [hlasovací služby](#services) a hodnota
je [objekt PlayerInfo](#playerinfo) nebo `null` v případě selhání
načtení dat.

##### Příklad

`/api/CoolFido`

```
{
    "CZECH_CRAFT": {
        "nick": "CoolFido",
        "votes_count": 2,
        "next_vote": 1674570505,
        "vote_url": "https://czech-craft.eu/server/minehub/vote?user=CoolFido"
    },
    "CRAFTLIST": null,
    "MINECRAFT_LIST": {
        "nick": "CoolFido",
        "votes_count": 1,
        "next_vote": 1674571538,
        "vote_url": "https://www.minecraft-list.cz/server/minehubcz/vote?name=CoolFido"
    },
    "MINECRAFTSERVERY": {
        "nick": "CoolFido",
        "votes_count": 1,
        "next_vote": 1674572924,
        "vote_url": "https://minecraftservery.eu/server/minehubcz/vote/CoolFido"
    }
}
```

## Data

### Služby

|Název             |Třída                 |URL                              |
|------------------|----------------------|---------------------------------|
|CZECH_CRAFT       |CzechCraft.php        |<https://czech-craft.eu>         |
|CRAFTLIST         |CraftList.php         |<https://craftlist.org>          |
|MINECRAFT_LIST    |MinecraftList.php     |<https://www.minecraft-list.cz>  |
|MINECRAFTSERVERY  |MinecraftServery.php  |<https://minecraftservery.eu>    |

### Objekt ServerInfo

|Název vlastnosti  |Datový typ   |Význam                       |
|------------------|-------------|-----------------------------|
|position          |int \| null  |Pořadí serveru v žebříčku    |
|votes_count       |int          |Celkový počet hlasů serveru  |
|url               |string       |Odkaz na stránku serveru     |

### Objekt PlayerInfo

|Název vlastnosti  |Datový typ  |Význam                                             |
|------------------|------------|---------------------------------------------------|
|nick              |string      |Nick hráče                                         |
|votes_count       |int         |Počet hlasů daného hráče                           |
|next_vote         |int         |Timestamp času, od kdy hráč smí nejdřívě hlasovat  |
|vote_url          |string      |Hlasovací odkaz hráče                              |
