# ATK-MD0280-PIO Library for PlatformIO

本项目是为正点原子 (ALIENTEK) STM32F407ZGT6 探索者开发板移植的 ATK-MD0280 (2.8寸 TFT LCD) 屏幕驱动库，主要用于在 PlatformIO 环境下快速进行开发。

## ✨ 特性

* **完美适配 PlatformIO**: 无需手动配置复杂的包含路径，通过库管理器直接引入。
* **FSMC 驱动**: 默认使用 STM32 的 FSMC 接口，屏幕刷新速度快。
* **自动识别 IC**: 继承了正点原子的 ID 读取算法，支持多种底层驱动 IC。
* **接口友好**: 保留了原汁原味的 `LCD_ShowString`、`LCD_DrawLine`、`LCD_Clear` 等常用函数，方便老代码直接迁移。

## 🛠 安装方法

在你的 PlatformIO 项目的 `platformio.ini` 配置文件中添加：

```ini
lib_deps = 
    dragon99617/ATK-MD0280-PIO
```

## 🔌 硬件连接（基于正点原子探索者F407）

本库默认使用正点原子探索者开发板的标准 LCD 接口引脚配置（FSMC总线）：
* **数据线**: D0-D15 -> 对应 FSMC_D0 - FSMC_D15
* **控制线**: 
    * CS (片选) -> FSMC_NE4
    * RS (数据/命令) -> FSMC_A18
    * WR (写使能) -> FSMC_NWE
    * RD (读使能) -> FSMC_NOE
    * BL (背光控制) -> PB15

## 🚀 基础调用说明

在你的主程序（如基于 HAL 库的工程）中，按以下步骤调用即可点亮屏幕：

1.  **引入头文件**：`#include "lcd.h"`
2.  **初始化**：在系统时钟和延时函数初始化完成后，调用 `LCD_Init();`
3.  **显示控制**：
    * 清屏：`LCD_Clear(WHITE);`
    * 设置画笔颜色：`POINT_COLOR = RED;`
    * 显示字符串：`LCD_ShowString(30, 40, 200, 24, 24, (uint8_t*)"ATK-MD0280 Ready!");`

## ⚠️ 版权声明与免责条款

* **核心驱动版权**：本库中涉及的核心驱动源码（包括但不限于 `atk_md0280.c`、`atk_md0280.h` 及字库文件）的著作权归属于**广州市星翼电子科技有限公司（正点原子 ALIENTEK）**所有。
* **开源目的**：本项目仅出于个人学习、技术交流目的，对原厂驱动进行了 PlatformIO 平台的编译环境适配与目录结构封装。
* **使用限制**：请勿将原厂代码用于未经原作者授权的商业盈利项目。针对本仓库中个人补充的配置文件（如 `library.json` 等），采用 MIT 协议开源。
