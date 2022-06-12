# LLAntiCheat-release
## Description

English | [简体中文](README_zh-cn.md)  
Free AntiCheat plugin for LiteLoaderBDS 2
Continuously updating

## Features

- Anti Xray
- High Performance Ore Obfuscate
- Anti XpOrb
- Fix funnel bug
- ~~Anti illegal using command block and structure block~~(Mojang have fixed it)
- Anti KillAura
- Anti illegal enchant
- Fix debug packet modify game data
- Fix crash caused by push chest
- ~~Fix stonecutter change item data~~(Mojang have fixed it)
- Add Anvil cost check(Anti fake exp)
- Anti FakeName
- ~~Fix thorns's bug: copy item and crash server~~(Mojang have fixed it)
- Fix furnace copy item
- Fix funnel minecart copy item
- Fix furnace exp bug
- Anti AutoClick
- Anti fly and teleport(BDS built-in)
- Anti range destruction(BDS built-in)

## Supported Version

Bedrock Dedicated Server 1.19.1.01

## Download

[Release](https://github.com/LiteLDev/LLAntiCheat-release/releases)

## Addition

In order to ensure the effect, please ensure that the LiteLoaderBDS has not been modified
and change `correct-player-movement` and `server-authoritative-block-breaking` to `true`
and make the type of `server-authoritative-movement` is `"server-auth"` or `"server-auth-with-rewind"
in `server.properties`
![Config](https://user-images.githubusercontent.com/53301243/146678264-e122065c-dbc6-4935-8d5e-ae89aefca4ad.png)

**In order to protect proprietary software, this plugin uses other technologies to protect the binary files released by us. In case of false positives from anti-virus software, please join the (static scan) whitelist. To ensure your safety, it is recommended not to close anti-virus software or disable firewalls**

## Feedback&Feature Request

WangYneos@outlook.com

## Feedback group
LLAC dedicated QQ Group: 931871701  
QQ Groups ,telegram channel and discord server of LL

## Configuration File

Version PreRelease 22 fix 11  
Translation not 100% accurate

```jsonc

{
    //附魔相关内容
    //Enchant related information
    "Enchant": {
        //最大等级，超过该等级的附魔将被清除
        //Max Level for Enchantments, Enchantments that exceed this level will be removed
        "MaxLevel": 10
    },
    //原版漏洞相关修复
    //Fixes for bugs that existed in the original BDS
    "FixOriginalBugSwitch": {
        //箱子崩服
        //Fix Illegal Chest that cause Server Crash
        "ChestCrash": true,
        //修复熔炉复制物品
        //Fix CopyItem Bug in Furance
        "FuranceReplicate": true,
        //修复经验熔炉
        //Fix Experience Spawn Bug in Furance
        "InfiniteXpFurnace": false,
        //修复活塞推箱子复制物品
        //Fix CopyItem Bug when the Container is pushed by the piston
        "HopperReplicate": true,
        //修复异常堆叠
        //fix illegal itemStack Stacking which may be used for Copy Items
        "IllegalStack": true,
        //修复分解台复制物品
        //fix CopyItem Bug material reducer
        "ReducerReplicate": true,
        //修复递归死亡造成的异常掉落(荆棘)
        //Fix abnormal drops caused by recursive death (with thorns Armor)
        "ThornsRecursion": true
    },
    //踢出消息
    //Message When Player has been kicked from server
    "KickMessage": {
        //大多数情况下的消息
        //Kick Message in most cases
        "CommonCheat": "[AntiCheat] You have been kicked for cheating",
        //异常附魔，超出配置文件规定的附魔物品被使用/放入背包
        //Abnormal enchantments, items that exceed the enchantment level specified in Enchant.MaxLevel
        "IllegalEnchant": "[AntiCheat] You have been detected for using <Cheat:IllegalEnchant>",
        //无效的玩家名，即NameTag和XBox玩家名不一致
        //Invalid Player Name(NameTag!=XBoxPlayerName)
        "InvalidName": "[AntiChest] You have been detected for using <Cheat:InvalidName>",
        //杀戮 短时间内杀人太多
        //Killing too many people in a short period of time
        "KillAura": "[AntiCheat] You have been detected for using <Cheat:KillAura>",
        //刷经验
        //Illegal Experience or Level Request
        "XpHack": "[AntiCheat] You have been detected for using <Cheat:XpHack>"
    },
    //踢出开关
    "KickSwitch": {
        //无效的玩家名，即NameTag和XBox玩家名不一致
        //Invalid Player Name(NameTag!=XBoxPlayerName)
        "AntiInvalidName": true,
        //刷物
        //spawn Items
        "GiveItem": true,
        //杀戮 短时间内杀人太多
        //Killing too many people in a short period of time
        "KillAura": true,
        //到达最大作弊次数
        //Reach the maximum number of cheats
        "MaxCheatReach": true,
        //刷经验
        //Illegal Experience or Level Request
        "XpHack": true
    },
    //功能开关
    "Switch": {
        //刷经验
        //Illegal Experience or Level Request
        "AntiXpHack": true,
        //反矿透
        //Prevent Player from Using Xray Mods to fine Ores
        "AntiXray": true,
        //反矿透混淆模式，依赖“反矿透”功能开启，不建议关闭
        //Obfuscation mode, depending on the "AntiXray" function
        "AntiXrayObfs": true,
        //作弊次数到达CheatCountBan执行的命令
        //Command executed when the number of cheats reaches CheatCountBan
        "BanCommand": "ban {player}",
        "CheatCountBan": 8,
        "CheatCountKick": 8,
        //校验铁砧经验需求
        //Check anvil experience requirements
        "CheckAnvilCost": true,
        //检查附魔
        //Check Item's Enchantment
        "CheckEnchant": true,
        //检查杀戮
        //Check for Killaura
        "CheckKillaura": true,
        //最大每秒击杀数，依赖“检查杀戮”功能开启
        //Maximum number of kills per second, depending on the "CheckKillaura" function
        "KillPerSecond": 8,
        //检查切石机（防止客户端修改切石机输出）
        //Check StoneCutter (prevent client from modifying StoneCutter output)
        "CheckStoneCutter": true,
        //禁用命令方块矿车
        //Disable Minecart with CommandBlock
        "DisableCommandBlockMinecart": true,
        //禁用NPC
        //Disable NPC
        "DisableNPC": true,
        //阻止游戏期间更皮肤
        //Prevent Player Change Skin During the Game
        "PreventChangeSkin": true
    }
}
```
