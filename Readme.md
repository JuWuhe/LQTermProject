[![](https://img.shields.io/badge/Author-Insyent-green)](https://insyent.today)	[![](https://img.shields.io/badge/powered%20by-Unreal-blue)](https://github.com/EpicGames/UnrealEngine)	 [![Visual Studio](https://img.shields.io/badge/--6C33AF?logo=visual%20studio)](https://visualstudio.microsoft.com/)

# 概览

- [背景](#背景)
- [实现功能](#实现功能)
- [链接](#网盘链接)
- [维护者](#维护者)

# 背景

​		本仓库是 **2班-高致远** 于2021.10.10参与腾讯游戏学院高校公开课时创建，用于存储学习第四次课程|UMG界面时作业项目工程文件。该工程文件基于Unreal4.27版本，目标平台为Android移动平台，为光子大作业项目仓库。

​		仓库工程文件`Git Clone`后需重新编译才可运行。

# 实现功能

- **存在的BUG/缺陷**
  - 移动平台的排行榜不能显示任何内容，猜测是未能成功`SaveGame`，暂未提上Debug日程
  - ~~打开排行榜 UI 并关闭后，移动平台的摇杆失效，只在排行榜UI打开时才有效~~
    - 原因：关闭排行榜UI后，将跳跃按钮存在的MyHUD控件设为`Visiable`，遮罩了触碰界面导致触摸事件无法触发，修改为`Not HIt - Testable(Self only)`解决
  - 服务器端的`PickUpScanner`在客户端不能正确显示，且客户端第一次扫描到武器时，服务器端与客户端都会出现<kbd>拾取</kbd>按钮，Log出现无访问报错
  - ~~服务器端角色持枪动作异常，枪非握持而是延伸在手臂上随手臂晃动，原因可能与上述相同，具体原因未知~~
    - 原因与上面不同，仍然不清楚为什么，解决方案是原本是在`HolsterWeapOnSelf`(组播)中调用事件`HolsterMontage`播放蒙太奇，在`HolserWeapOnServer`(在服务器上运行)中调用`HolsterWeapOnSelf`，现在删除中转节点`HolsterWeapOnSelf`，直接将`HolsterMontage`改为组播，得到解决
  - 有时在UEEditor中运行联机会出bug，原因未知，判断方式为客户端角色与服务器端角色出生在同一位置，且客户端持枪动作异常
  - 两个都`PlayAsClient`时，`PickUpScanner`一帧会出现两次，Log报出大量无访问，原因未知，并且此时看彼此的持枪方式均异常
  - 换弹动画的网络同步会丢下来两个弹夹，Log报出无访问

------

- 射线检测并拾取武器

- 滑动屏幕旋转视角

- 长按宏（但是还没有具体应用）

- 保存游戏得分，记录排行榜

  > 移动端有BUG，可能仅用于Lesson4，后续并不一定实现该功能

- 不同材质下的脚步声、脚印

- 射击抛体，命中时发生爆炸，并在不同物理材质下区别弹射

  > 粗糙实现，可能仅用于Lesson6，后续并不一定实现该功能

- 枪械

  - AR步枪
    - 半自动模式：触发一次射击一次，且有射速上限

- 局域网联机

  - 拾取武器、切换持枪、瞄准、开火等
  - 多人玩家信息、分数同步

- 动画
  - 拔枪、收枪
  - 站立状态下，角色头随着视角旋转
  - 腰射持枪状态下，左手 *IK* 使左手在任何俯仰角下握住枪械
  - 瞄准状态下，右手 *IK* 使枪械处于合适高度，不与头部穿模
  - 腰射、机瞄AimOffset（俯仰）
  - 换弹（丢下弹夹，装配弹夹）
  - 射击动画

- UMG界面
  - 拾取武器按钮
  - 角色操作界面（多人玩家信息、跳跃、射击、瞄准等）
  - 排行榜界面（上传数据、刷新、离开）

# 链接

- [Lesson4| UMG界面 | 网盘链接](https://share.weiyun.com/ARsph86I)
- [Lesson5| 骨骼动画 | 网盘链接](https://share.weiyun.com/joioQRR8)
- [Lesson6| 基本物理 | 网盘链接](https://share.weiyun.com/9BFyICQy)
- [Lesson7| 网络同步 | 网盘链接](https://share.weiyun.com/1Mi8mb9s)

# 维护者

[@JuWuhe](https://github.com/JuWuhe)