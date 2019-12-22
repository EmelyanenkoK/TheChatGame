# The Chat Game
The Chat Game is chat game for Telegram messenger.

The game (@thechatgamebot or t.me/thechatgamebot) based on RPG + collectibles mechanincs. It allows users to collect different items and use them for fights, trade and other gameplay mechanincs. For most games with similar concepts players often discuss conditions and execute item exchange outside of the game, especially when the game doesn't build it's inventory related mechaninc around player/account binded items. The most striking example is a huge market of EvE-online items (starships, resources etc). However, the main obstacle for effective market operation is conjuction of "out-of-game agreement" and "in-game exchange". Usually such exchanges require complex schemes involving guarantors. This is the problem which can be effectively solved by TON smart-contract.

We move all operations with items inside the game on-chain. This way users may transfer their items on their own TON addresses; exchange, trade, and subject items to be governed by complex smart-contracts. It is even possible to transfer items to the other games (if owners of those games provide gates). More details and discussion are placed in section [On-chain advances](#onchain).

We also solve one of the most complicated issues for Telegram-based text games - their low adoption and low organic growth rate. We use @combot with more than 60000 active groups as a playground for items issuing. More than 30% of chats which uses Combot also uses it's XP system. We simply add game items as a random rewards for users activity in group chats. This mechanics allows us to organically integrate the part of the gameplay associated with getting the first items into a huge number of group chats.

## Smart contract details
Smart contract allows item manipulation both for game admins and external users.

Game admins may create new items, place them into inner user inventories, put specifications of the items on-chain (thus it is possible to create independent inventory explorers and other services) and also transfer and burn items on behalf on inner users.

At the same time game admins have no power to change inventories of outer users. That way once item is transferred outside of the game, all operations became fully independent of admins will. "No power, no abuse of power".

At the same time, inner and outer users are equal with only differense that inner users has first 196 bits of their 'addresses' zeroed. Respectively admins only may change inventories of users with first first 196 bits of their 'addresses' equal to zero.

### Replay protection
Since it is expected that there may be period of high rate of item operations, and since game engine may be runned independently in many processes (on many servers) we chose to implement replay protection using 'remember recent queries mechanism'. That way using of blockchain is not only 'not obstructive', but otherwise allows to guarantee atomicity.

### Garbage collections
To prevent clutter of the contract storage, the administration reserves the right to delete data of inactive users (no actions more than a year).

### Outer users abilities
Outer users may transfer items and touch inventories (to prevent their deleting after year of inactivity) by sending inner messages. Also, any smart-contract may request information about any user inventory and get response as TON inner message.

### Spam-prevention
Spam prevention is reached by two mechanisms. In-game spam prevention is implemented as non-zero cost of on-chain operations in terms of game resources. Out-of-game spam prevention is implemented as fee collection for operations which require storing of additional information.

### Smart-contract address
Smart-contract deployed on `kQChp8oK-nB-Avs1rCL8Q9IieH8oAwnntwIHmYvDzD07wqUf`.


## <a name="onchain"></a>On-chain advances

+ decentralized and transparent core gameplay base
+ decentralized and self-regulated ingame econimics
+ the ability to use GRAMs as ingame currency
