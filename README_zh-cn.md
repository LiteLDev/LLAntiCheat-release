# LLAntiCheat-release
## Description

[English](README.md) | 简体中文   
LiteLoaderBDS 2 的免费反作弊插件  
由社区驱动，并处于持续更新中  
不会加入已有开源解决方案的功能，除非集成会带来更好的体验  
反Toolbox请前往我们团队另外的开源插件（由于Toolbox修改版泛滥，该方案拦截率较低，技术上没有可能解决）

## 功能

- 反矿物透视
- 高性能矿物混淆
- 反刷经验球与经验
- 修复漏斗刷物品BUG
- ~~防止非法修改命令方块(矿车)和结构方块~~（BDS已修复）
- 防杀戮光环（有点小问题，默认禁用）
- 防非法附魔
- 反非法give（LL内置）
- 反调试包修改数据
- 修复推箱子崩服
- ~~修复切石机修改物品~~（BDS已修复）
- 添加铁砧花费校验（反假经验）
- 反虚假名字
- ~~修复荆棘复制物品和崩服bug~~（BDS已修复）
- 修复熔炉刷物
- 修复漏斗矿车刷物
- 新熔炉刷经验
- 反连点器
- 防飞行/传送（BDS内置）
- 防止范围破坏（BDS内置）

## 支持的版本

Bedrock Dedicated Server 1.19.1.01

## 附加

> 请不要将本插件加入整合包并发布，本插件拒绝整合，更不要将LLAC反馈群放到整合包介绍帖子里，谢谢  
> 未经授权严禁转载  
遇到问题，请优先查看配置文件，所有功能配置文件均可开关（部分对正常游戏无影响的除外）
为了确保效果  
请保证LL2.0内置的反刷物功能正常开启  
如有需要可以配合[LLHelper](https://github.com/LiteLDev/LiteLoaderPlugins)隐藏种子
BDS内置了移动检测和方块操作校验功能，如有需要请在`server.properties`中将  
`correct-player-movement`和`server-authoritative-block-breaking`改为`true`  
并保证`server-authoritative-movement`的类型为`server-auth`或者`server-auth-with-rewind`

**为保护私有软件，本插件使用了其他技术保护我们发行的二进制文件，如遇杀毒软件误报，请加入（静态扫描）白名单，为保证您的安全建议不要关闭杀毒软件或禁用防火墙**

## 反馈/功能建议

WangYneos@outlook.com

## 反馈群

LLAC专用反馈QQ群: 931871701  
LL的QQ群/TG频道/discord服务器

## LiteLoader 反作弊配置文件解释

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
