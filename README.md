# GameEngineArchitectureNote

## Chapter 1

### 1.1 典型游戏团队的结构

- engineer
runtime programmer(gameplay) & tool programmer(SDK)

- artist
"content is king"

concept artist、3D modeler、foreground modeler、background modeler、texture artist、lighting artist
、animator、motion capture actor、sound designer、voice actor、composer

- game designer
gameplay engineer、writer

- producer

- etc

### 1.2 游戏是什么

soft real-time interactive agent-based computer simulation[基于代理的计算机模拟的软实时互动]

### 1.3 游戏引擎是什么

### 1.4 不同游戏类型的引擎差异

#### FPS

- 高效地渲染
- 实时性
- 拟真
- 各种武器
- 规则不是很严密的碰撞
- 强力的AI
- 多人模式

#### 第三人称&平台游戏

- 移动模式（跑酷）
- 解谜的环境元素
- 第三人称的“俯视摄像机”
- 复杂的碰撞系统

#### 格斗游戏

- 丰富的动作
- 精准的判定
- 针对复杂操作的相应系统
- 背景
- 动画
- 人物仿真

#### 竞速游戏

- 远处背景的渲染
- 赛道，路径等
- 视角
- 碰撞

#### RTS(real-time strategy)

- 大量可操作单位
- 高度场地形(height field terrain)
- 建造
- 交互

#### MMO(massively multiplayer online game)

- 庞大的服务器

#### mod

#### 其他

体育游戏、rpg、模拟游戏、解密游戏、非电子游戏的移植(如麻将)、网页游戏等

### 1.5 游戏引擎概览

#### 雷神之锤

#### 虚幻

#### Source(DOTA2!)

#### DICE的寒霜引擎(战地)

#### CryEngine(孤岛危机)

#### 索尼的PhyreEngine(黑魂)

#### 微软的XNA Game Studio

#### Unity

#### 供非程序员使用的二维游戏引擎

#### 其他商业引擎

#### 专有内部引擎(神秘海域!)

#### 开源引擎

### 1.6 运行时引擎架构

#### 硬件

电脑、游戏主机、手机等

#### 设备驱动

管理硬件资源，用以隔离操作系统和上层引擎，使上层软件无需理解不同硬件版本的通信细节差异

#### 操作系统

#### SDK和中间件

- 数据结构和算法

STL、Boost

- 图形

OpenGL、DriectX

- 碰撞和物理

ODE(open dynamic engine)

- 角色动画

Edge(顽皮狗+索尼联合制作)

- AI

Kynapse(包括路径搜寻、物体回避、辨别等接口)

- 生物力学角色模型

Endorphin & Euphoria(利用真实人类运动的高阶生物力学模型去产生角色动作)

#### 平台独立层

隔离引擎和底层平台(API)

#### 核心系统

- 断言(assertion)

检查代码错误

- 内存分配

高效的内存分配与释放系统

- 数学库

各种数学计算

- 自定义的数据结构以及算法

#### 资源管理器

各种游戏资源和数据

#### 渲染引擎

游戏引擎中最为复杂的部分，通常采用分层架构

- 低阶渲染器

高速渲染丰富的几何图元集合不考虑部分场景是否可见

使用图形设备接口(如OpenGL)和其他渲染组件

- 场景图/剔除优化

基于可视性判别算法去限制提交的图元数量


- 视觉效果

粒子(烟、火、水花)、贴花(弹孔、脚印)、光照贴图、环境贴图、动态阴影、后期处理效果、
高动态范围(HDR)、全屏抗锯齿(FSAA)、颜色矫正等

- 前端

HUD、菜单、GUI等

#### 剖析和调试工具

内置调试、测试

#### 碰撞和物理

- 碰撞检测(collision detection)
- 动力学模拟(dynamic simulation)
- 刚体动力学模拟(rigid body dynamic)
- 运动学(kinematics)和动力学(dynamics)

第三方SDK：PhysX(NVIDIA) & Havok

#### 动画

- 精灵/纹理动画(sprite/texture animation)
- 刚体层次结构动画(rigid body hierarchy animation)
- 骨骼动画(skeletal animation)
- 顶点动画(vertex animation)
- 变形目标动画(morph target animation)

#### 人体学接口设备

- 键鼠
- 手柄(joypad)
- 专用控制器等

#### 音频

#### 多人在线/网络游戏

- 单屏多人(魂斗罗双人)
- 切割屏多人(马里奥赛车多人)
- 网络多人(UFC)
- MMO

#### Gameplay

- 游戏世界和游戏对象模型，包括：
1. 静态物体、动态刚体
2. 玩家角色、NPC
3. 武器、载具、光源等

参考*软件对象模型*的概念：
1. 是否OOD？
2. 使用什么语言？
3. 如何组织静态阶层？
4. 使用模板/基于原则设计/多态(polymorphism)？
5. 参考对象用一般指针/智能指针/句柄？
6. 如何标识独一无二的对象？
7. 如何管理对象的生命周期
8. 如何随时间模拟对象的状态?

- 事件系统

游戏对象与其他对象之间的通信

- 脚本

便于修改游戏逻辑和结构

- AI基础

- 专用子系统

比如载具、武器系统等

### 1.7 工具及资产管道

引擎需要读取大量数据

#### 数字内容创作工具(digital content creation, DCC)

#### 资产调节管道

DCC制作的数据，要导出为容易读取的标准/自定义格式

- 三维模型/网格数据
- 骨骼动画数据
- 音频数据
- 粒子系统数据

#### 世界编辑器

#### 资源数据库

使用关系型数据库

#### 一些构建工具的方法

基于网页的用户界面(PUBG主界面)