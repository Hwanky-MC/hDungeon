# hDungeon

[![Java](https://img.shields.io/badge/Java-21%2B-orange.svg)](#requirements)
[![Paper API](https://img.shields.io/badge/Paper%20%2F%20Leaf%20%2F%20Purpur-1.21%2B-blue.svg)](#requirements)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.0-purple.svg)](#download)

**hDungeon** is a lightweight, performance-focused multi-room wave dungeon plugin for modern **Paper, Leaf, and Purpur 1.21+** servers.

Built with Java 21, hDungeon brings together Solo and Party dungeon runs, configurable wave progression, Dungeon Gems, an interactive GUI shop, visual administration tools, and automatic dungeon scheduling.

Designed for both Java and Bedrock players through GeyserMC compatibility.

---

## Features

### Multi-Room Dungeon System
- Run multiple dungeon rooms simultaneously.
- Supports Solo and Party gameplay.
- Add or configure rooms through `config.yml`.
- Automatically start waiting parties when a room becomes available.

### Solo & Party Wave Scaling
- Separate mob configurations for Solo and Party modes.
- Custom mob pools, boss waves, titles, sounds, and rewards.
- Configurable Dungeon Gems rewards through `waves.yml`.

### Dungeon Gems & GUI Shop
- Dedicated Dungeon Gems currency.
- Clean 4-row GUI shop with 36 available slots.
- Supports Solo Keys, Wave Skippers, and console-command rewards.
- Daily purchase limits and anti-duplicate click protection.
- Shop access is controlled by dungeon state and match phase.

### Visual Admin Shop Editor
Manage your shop directly in-game using `/dg shopadmin`.

- Add items directly from your inventory or cursor.
- Edit prices, daily limits, and action modes.
- Enable, disable, or delete shop items.
- Move and swap item slots visually.

### Automatic Dungeon Schedule
- Configure daily opening and closing times.
- Supports IANA timezones such as `Asia/Jakarta`, `UTC`, and `Europe/London`.
- Pre-open and pre-close warning notifications.
- Supports `AUTO`, `OPEN`, and `CLOSED` modes.

### Moderation & Anti-Escape
- Built-in dungeon ban and unban commands.
- Configurable command whitelist.
- Prevents dungeon escape commands such as `/tpa`, `/home`, `/warp`, `/spawn`, and `/back`.
- Custom command aliases.

---

## Requirements

| Component | Requirement |
|---|---|
| Minecraft | 1.21+ |
| Server Software | Paper / Leaf / Purpur |
| Java | Java 21 or newer |
| Economy Integration | Vault + Economy plugin (optional) |
| Placeholder Support | PlaceholderAPI (optional) |

---

## Download

Download the latest compiled plugin from the GitHub Releases page.

**[Download hDungeon](../../releases/latest)**

The release contains the ready-to-use plugin JAR. No source code or development tools are required.

---

## Installation

1. Download the latest `hDungeon-1.0.0.jar`.
2. Place the JAR inside your server's `plugins/` folder.
3. Restart your server.
4. Configure your dungeon using the generated configuration files.
5. Set up your lobby, queue, and arena spawn locations.

### Initial Setup

```text
/dg setspawn
/dg setqueue
/dg setspawn 1
/dg setmobspawn 1
```

Repeat the room spawn commands for additional rooms.

Start a test run:

```text
/dg test solo
/dg test party
```

Apply configuration changes:

```text
/dg reload
```

---

## Commands

### Player Commands

| Command | Description | Permission |
|---|---|---|
| `/dg` | Show help menu | `dungeon.use` |
| `/dg shop` | Open Dungeon Shop | `dungeon.shop` |
| `/dg gems` | Check Dungeon Gems balance | `dungeon.gems` |
| `/dg status` | View room status and queue | `dungeon.status` |
| `/dg stats` | View daily reward statistics | `dungeon.stats` |
| `/dg leave` | Leave current dungeon | `dungeon.leave` |

### Admin Commands

| Command | Description | Permission |
|---|---|---|
| `/dg setup` | Manage dungeon locations and spawns | `dungeon.admin.setup` |
| `/dg join <room>` | Join a dungeon room | `dungeon.join` |
| `/dg shopadmin` | Open visual shop editor | `dungeon.admin.shop` |
| `/dg shopadmin add <slot> <price> [limit]` | Add held item to shop | `dungeon.admin.shop` |
| `/dg shopadmin move <from> <to>` | Move or swap shop slots | `dungeon.admin.shop` |
| `/dg shopadmin setcmd <slot> <cmd>` | Set console command for a shop item | `dungeon.admin.shop` |
| `/dg gems <give\|take\|set> <player> <amount>` | Manage Dungeon Gems | `dungeon.admin.gems` |
| `/dgschedule` | Manage dungeon schedule | `dungeon.admin.schedule` |
| `/dg ban <player> [reason]` | Ban a player from dungeon features | `dungeon.admin.ban` |
| `/dg unban <player>` | Remove a dungeon ban | `dungeon.admin.ban` |
| `/dgkey <player> [amount]` | Give Solo Dungeon Keys | `dungeon.admin.givekey` |
| `/dgskipkey <player> [amount]` | Give Wave Skippers | `dungeon.admin.giveskipkey` |
| `/dg skipwave` | Skip the current wave | `dungeon.admin.skipwave` |
| `/dg test <solo\|party>` | Start an admin test run | `dungeon.admin.test` |
| `/dg stop <room\|test\|all>` | Stop dungeon sessions | `dungeon.admin.stop` |
| `/dg reload` | Reload plugin configurations | `dungeon.admin.reload` |

**Admin tip:** Grant `dungeon.admin` (default: OP) for full administrative access.

---

## PlaceholderAPI

Requires PlaceholderAPI.

| Placeholder | Description |
|---|---|
| `%dungeon_gems%` | Player's Dungeon Gems balance |
| `%dungeon_banned%` | Dungeon ban status |
| `%dungeon_queue%` | Current party queue count |
| `%dungeon_max_queue%` | Maximum party queue count |
| `%dungeon_status_<room>%` | Room status |
| `%dungeon_players_<room>%` | Players in a room |
| `%dungeon_wave_<room>%` | Current wave |
| `%dungeon_mobs_<room>%` | Active mob count |
| `%dungeon_my_room%` | Player's current room |
| `%dungeon_my_state%` | Player's current match state |
| `%dungeon_my_wave%` | Player's current wave |
| `%dungeon_my_mobs%` | Active mobs in player's match |
| `%dungeon_daily_<tier>%` | Daily tier claims |
| `%dungeon_limit_<tier>%` | Daily tier limits |
| `%dungeon_open%` | Dungeon open status |
| `%dungeon_schedule_open%` | Scheduled opening time |
| `%dungeon_schedule_close%` | Scheduled closing time |
| `%dungeon_schedule_mode%` | Current schedule mode |
| `%dungeon_schedule_next%` | Countdown to next schedule change |
| `%dungeon_reset_time%` | Daily reset time |

Supported reward tiers: `easy`, `normal`, `hard`, and `extreme`.

---

## Configuration

hDungeon automatically generates its configuration files on first startup.

| File | Purpose |
|---|---|
| `config.yml` | Main settings, rooms, storage, and scheduling |
| `waves.yml` | Solo and Party waves, mobs, bosses, and rewards |
| `shop.yml` | Dungeon Shop items and prices |
| `messages.yml` | Plugin messages |
| `sounds.yml` | Sound effects |

Use `/dg reload` to apply supported configuration changes.

## License

This project is licensed under the **MIT License**.
