# Diret�rios de Importa��o

## Para que serve o diret�rio de importa��o?

O diret�rio `import/` oferece uma maneira de alterar suas configura��es sem a necessidade de modificar os arquivos principais em `/conf/` e `/db/`.

Ao colocar suas entradas personalizadas no diret�rio `import/` dentro dessas duas localiza��es, seus arquivos principais n�o ter�o conflitos a serem resolvidos quando voc� atualizar seu servidor. Voc� mant�m suas altera��es, e o restante � atualizado com o rAthena.

## Como isso funciona?

Pense em "importar" como "sobrescrever". Coloque apenas as configura��es que voc� alterou nos arquivos de importa��o, ou configura��es que voc� est� "sobrescrevendo".

Por exemplo, ao configurar um servidor, sempre h� algumas configura��es que os usu�rios gostariam de alterar para que o rAthena atenda �s suas necessidades. O exemplo a seguir mostrar� como usar corretamente o diret�rio `/db/import/`. (para exemplos de `/conf/import/`, veja [/conf/readme.md](/conf/readme.md))

### Conquistas
---
Queremos adicionar nossa pr�pria conquista personalizada que pode ser dada a um jogador atrav�s de um Script NPC e outra que podemos dar aos nossos GMs.

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


### Inst�ncias
---
Queremos adicionar nossa pr�pria Inst�ncia de Moradia personalizada.

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
Queremos fazer com que Porings pare�am com Baphomet.

#### /db/import/mob_avail.yml

```yml
    - Mob: PORING
      Sprite: BAPHOMET
```


### Mapas Personalizados
---
Queremos adicionar nossos pr�prios mapas personalizados. Para isso, precisamos adicionar os nomes dos nossos mapas ao arquivo `import/map_index.txt` e depois ao arquivo `import/map_cache.dat` para que o Servidor de Mapas os carregue.

#### /db/import/map_index.txt

```
    1@home	1250
    2@home
    3@home
    ev_has
    shops
    prt_pvp
```


### Restri��es de Com�rcio de Itens
---
Queremos garantir que itens espec�ficos n�o possam ser negociados, vendidos, descartados, colocados em armazenamento, etc.

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
    - Id: 34002 # Di�rio de Reputa��o
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


### Miss�es Personalizadas
---
Queremos adicionar nossas pr�prias miss�es personalizadas ao quest_db.

#### /db/import/quest_db.yml

```yml
    - Id: 89001
      Title: "Miss�o de Reputa��o"
    - Id: 89002
      Title: "Miss�o de Reputa��o"
```



N�o podemos enfatizar o suficiente o quanto esse sistema � �til para todos. A maioria dos conflitos no git simplesmente desaparecer� se os usu�rios fizerem uso do sistema `import/`.
