---
---
# Deuplicate guide

Everything you can do with the mod, from your first heart to running duplicates on a
multiplayer server.

## Hearts

Hearts are the currency of the mod. Your max hearts go up and down as you craft, kill,
and duplicate.

- **Craft a Heart.** Surround a golden apple with diamonds and redstone:

  ```
  R D R
  D G D
  R D R
  ```

  R is redstone, D is a diamond, G is a golden apple. Using the Heart raises your max
  hearts by one, up to a cap of 20 by default.

- **Take hearts from players.** Killing another player moves one of their max hearts
  to you (lifesteal). They lose it, you gain it.

- **Spend hearts on duplicates.** Creating a duplicate permanently costs two max
  hearts by default. You always keep at least one. When you clear that duplicate, the
  hearts come back to you.

The exact numbers (cost, cap, lifesteal amount) are server settings, listed at the
bottom of this page.

## Creating and clearing duplicates

Press **V** to create a duplicate. It spawns as a copy of you and starts in Follow
mode. If you do not have enough hearts to pay the cost, nothing happens and you get a
message.

- **C** calls every duplicate you own straight back to you, wherever they are.
- **X** clears your newest duplicate.
- **Z** clears all of them at once.

Clearing a duplicate refunds the hearts you paid for it.

## Tasks

Right-click a duplicate to open its menu and choose a job.

| Task | What the duplicate does |
|------|--------------------------|
| Follow Me (Bodyguard) | Sticks with you and fights what you fight. This is the starting mode. |
| Guard Area | Holds a fixed spot and fends off anything that comes near it. |
| Defender | Defends its anchor and the people it is friendly with. |
| Raider | Pushes outward and attacks enemies instead of holding ground. |
| Chop Trees | Finds and chops nearby trees for wood. |
| Mine Ore | Mines a chosen ore. Pick coal, copper, iron, gold, redstone, or lapis in the menu. Give it a pickaxe. |
| Harvest Crops | Harvests grown crops and replants. |
| Hunt Animals | Hunts nearby animals for their drops. |

Follow and Raider stay near you or the action. The other jobs are autonomous: the
duplicate works around the spot where you assigned the task and keeps going even when
you walk away.

### Where the loot goes

The four gathering jobs (chop, mine, harvest, hunt) carry what they collect and drop
it off for you. In the task menu you choose the deposit target:

- **To Me** sends the loot to you.
- **To Chest** sends it to a chest you bind. Pick Bind Deposit Chest, then right-click
  the chest you want it to use.

## Job blocks

**Duplicate Job Bench.** Right-click it to open a panel that lists the duplicates near
you and lets you assign jobs from one place instead of clicking each one.

```
I B I
P P P
P   P
```

I is an iron ingot, B is a book, P is any planks.

**Duplicate Job Board.** Right-click it to manage a defense board for your duplicates.

```
I P I
P H P
I P I
```

H is a Heart, I is an iron ingot, P is any planks.

## Teams (multiplayer)

Teams keep your duplicates from turning on your friends. Use these in chat:

| Command | What it does |
|---------|--------------|
| `/deuplicate team create <name>` | Start a team |
| `/deuplicate team invite <player>` | Invite a player to your team |
| `/deuplicate team join <name>` | Join a team you were invited to |
| `/deuplicate team leave` | Leave your team |
| `/deuplicate team info` | Show your team and its members |
| `/deuplicate team disband` | Disband a team you own |

## Admin commands

These need operator permission.

| Command | What it does |
|---------|--------------|
| `/deuplicate reload` | Reload the server config from disk |
| `/deuplicate hearts get <player>` | Show a player's max hearts |
| `/deuplicate hearts set <player> <n>` | Set a player's max hearts (1 to 100) |
| `/deuplicate hearts add <player> <n>` | Add or remove max hearts (-100 to 100) |

## Server settings

On a server or in singleplayer, the file `config/deuplicate-server.properties` is
created with defaults the first time the mod runs. The chunk-loading group is the main
lever for keeping a busy server smooth while duplicates work away from any player.

| Setting | Default | What it does |
|---------|---------|--------------|
| `keepDuplicatesLoadedWhileOffline` | true | Keep duplicates ticking when no player is nearby, even while the owner is offline |
| `forceLoadChunkRadius` | 1 | Chunk radius kept loaded around each working duplicate (0 to 4) |
| `chunkUpdateIntervalTicks` | 40 | How often the loader re-checks which chunks to keep (1 to 1200) |
| `nearbyPlayerRadius` | 80 | If a player is this close, the area is already loaded so no extra loading is used (16 to 512) |
| `maxForceLoadedDuplicates` | 128 | Hard cap on how many duplicates may force-load chunks at once |
| `duplicateHeartCost` | 2 | Max hearts paid to create a duplicate (0 to 20) |
| `minimumHeartsAfterDuplicate` | 1 | Lowest max hearts you can be left with after paying |
| `maxPlayerHearts` | 20 | Highest max hearts a player can reach |
| `playerKillHeartReward` | 1 | Max hearts taken from a player you kill |
| `craftedHeartValue` | 1 | Max hearts granted by using one crafted Heart |

After editing the file, run `/deuplicate reload` to apply it without a restart.
