[![](https://img.shields.io/badge/Author-Insyent-green)](https://insyent.today)	[![](https://img.shields.io/badge/powered%20by-Unreal-blue)](https://github.com/EpicGames/UnrealEngine)	 [![Visual Studio](https://img.shields.io/badge/--6C33AF?logo=visual%20studio)](https://visualstudio.microsoft.com/)

# 概览

- [背景](#背景)
- [实现功能](#实现功能)
- [链接](#网盘链接)
- [维护者](#维护者)

# 背景

​		本仓库是**2班-高致远**于2021.10.10参与腾讯游戏学院高校公开课时创建，用于存储学习第四次课程|UMG界面时作业项目工程文件。该工程文件基于Unreal4.27版本，目标平台为Android移动平台，为光子大作业项目仓库。

​		仓库工程文件`Git Clone`后需重新编译才可运行。

# 实现功能

- **存在的BUG/缺陷**
  - 移动平台的排行榜不能显示任何内容，猜测是未能成功`SaveGame`，暂未提上Debug日程
  - ~~打开排行榜 UI 并关闭后，移动平台的摇杆失效，只在排行榜UI打开时才有效~~
    - 原因：关闭排行榜UI后，将跳跃按钮存在的MyHUD控件设为`Visiable`，遮罩了触碰界面导致触摸事件无法触发，修改为`Not HIt - Testable(Self only)`解决
  - 跳跃Button在跳跃没停止时仍然可以点击，不过并不会干扰该次跳跃，只是绑定了一个加分事件在跳跃上，但此时不能移动时跳跃，预计需重写`Jump`事件
  - 持枪时，手部悬空未触碰到枪把，需做手部 *IK (Inverse Kinematics)* 强化细节
  - 机瞄时，枪械高度过高与头部骨骼穿模，需调整持枪高度

------



- 射线检测并拾取武器
- 滑动屏幕旋转视角
- 动画
  - 拔枪、收枪
  - 腰射、机瞄AimOffset（俯仰）
  
- UMG界面
  - 拾取武器按钮
  - 角色操作界面（玩家信息、跳跃、待做：射击、瞄准等）
  - 排行榜界面（上传数据、刷新、离开）

# 链接

- [Lesson4| UMG界面 | 网盘链接](https://share.weiyun.com/ARsph86I)

# 维护者

[@JuWuhe](https://github.com/JuWuhe)