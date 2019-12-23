# The Chat Game
The Chat Game (TCG) is chat game for Telegram messenger.

The game (@thechatgamebot or t.me/thechatgamebot) is based on various RPG mechanics, including collectible items. Users can utilize various items for gameplay mechanics like fighting and trading. Most games with similar concept force players to manually exchange their items or inventories (sometimes offline), because platforms do not allow them to do so in the way they want. The most striking example is a huge market of EVE Online in-game items (starships, resources, etc). Main obstacles for effective free market operation are centralization and regulations. Usually, unofficial exchanges require shady schemes involving guarantors. Official in-game exchanges usually have strict trading rules and high fees. Both of these problems can be effectively solved by TON.

We decided to move all item-related operations to the TON Blockchain. Users can transfer their items to their TON address and have complete control over them. TON Blockchain ensures transparency and guarantees that game owners cannot interfere with players' inventories. Other games and service can interact with our smart contract to read inventories and perform actions related to items.

As Telegram-based game we also solve one of the most complicated issues for text games in Telegram - low adoption rate and low organic growth rate. Our game is using @combot with more than 60000 active groups to issue items to users. About 1/3 of groups using @combot utilize "levels & XP" system. In these groups, users have a chance to receive in-game item. This allows us to organically integrate the part of the gameplay associated with getting the very first items into a huge number of group chats.

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
