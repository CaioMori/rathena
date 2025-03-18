# Diretórios de Importação

## Para que serve o diretório de importação?

O diretório `import/` oferece uma maneira de alterar suas configurações sem a necessidade de modificar os arquivos principais em `/conf/` e `/db/`.

Ao colocar suas entradas personalizadas no diretório `import/` dentro dessas duas localizações, seus arquivos principais não terão conflitos a serem resolvidos quando você atualizar seu servidor. Você mantém suas alterações, e o restante é atualizado com o rAthena.

## Como isso funciona?

Pense em "importar" como "sobrescrever". Coloque apenas as configurações que você alterou nos arquivos de importação, ou configurações que você está "sobrescrevendo".

Por exemplo, ao configurar um servidor, sempre há algumas configurações que os usuários gostariam de alterar para que o rAthena atenda às suas necessidades. O exemplo a seguir mostrará como usar corretamente o diretório `/db/import/`. (para exemplos de `/conf/import/`, veja [/conf/readme.md](/conf/readme.md))

### Conquistas
---
Queremos adicionar nossa própria conquista personalizada que pode ser dada a um jogador através de um Script NPC e outra que podemos dar aos nossos GMs.

#### /db/import/achievement_db.yml

```yml
    - Id: 280000
      Group: None
      Name: Emperio
      Reward:
        TitleId: 1035
      Score: 50
    - Id: 280001
      Group: None
      Name: Staff
      Reward:
        TitleId: 1036
      Score: 50
```


### Instâncias
---
Queremos adicionar nossa própria Instância de Moradia personalizada.

#### /db/import/instance_db.yml

```yml
    - Id: 35
      Name: Home
      IdleTimeOut: 900
      Enter:
        Map: 1@home
        X: 24
        Y: 6
      AdditionalMaps:
        - Map: 2@home
        - Map: 3@home
```


### Alias de Monstros
---
Queremos fazer com que Porings pareçam com Baphomet.

#### /db/import/mob_avail.yml

```yml
    - Mob: PORING
      Sprite: BAPHOMET
```


### Mapas Personalizados
---
Queremos adicionar nossos próprios mapas personalizados. Para isso, precisamos adicionar os nomes dos nossos mapas ao arquivo `import/map_index.txt` e depois ao arquivo `import/map_cache.dat` para que o Servidor de Mapas os carregue.

#### /db/import/map_index.txt

```
    1@home	1250
    2@home
    3@home
    ev_has
    shops
    prt_pvp
```


### Restrições de Comércio de Itens
---
Queremos garantir que itens específicos não possam ser negociados, vendidos, descartados, colocados em armazenamento, etc.

#### /db/import/item_db.yml

```yml
    - Id: 34000 # Caixa Verde Antiga
      Trade:
        NoDrop: true
        NoTrade: true
        TradePartner: true
        NoSell: true
        NoCart: true
        NoStorage: true
        NoGuildStorage: true
        NoMail: true
        NoAuction: true
    - Id: 34001 # Chaves da Casa
      Trade:
        NoDrop: true
        NoTrade: true
        TradePartner: true
        NoSell: true
        NoCart: true
        NoStorage: true
        NoGuildStorage: true
        NoMail: true
        NoAuction: true
    - Id: 34002 # Diário de Reputação
      Trade:
        NoDrop: true
        NoTrade: true
        TradePartner: true
        NoSell: true
        NoCart: true
        NoStorage: true
        NoGuildStorage: true
        NoMail: true
        NoAuction: true
```


### Missões Personalizadas
---
Queremos adicionar nossas próprias missões personalizadas ao quest_db.

#### /db/import/quest_db.yml

```yml
    - Id: 89001
      Title: "Missão de Reputação"
    - Id: 89002
      Title: "Missão de Reputação"
```



Não podemos enfatizar o suficiente o quanto esse sistema é útil para todos. A maioria dos conflitos no git simplesmente desaparecerá se os usuários fizerem uso do sistema `import/`.
