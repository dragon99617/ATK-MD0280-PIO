# ATK-MD0280-LCD Library for PlatformIO

本项目是为**正点原子 (ALIENTEK) STM32F407ZGT6 探索者开发板**移植的 **ATK-MD0280** (2.8寸 TFT LCD) 屏幕驱动库。

## ✨ 特性
- **完美适配 PlatformIO**: 无需手动配置复杂的包含路径。
- **FSMC 驱动**: 使用 STM32 的 FSMC 接口，显示速度极快。
- **自动识别 IC**: 继承了正点原子的 ID 读取算法，支持多种驱动 IC。
- **接口友好**: 保留了原汁原味的 `LCD_ShowString`、`LCD_DrawLine` 等常用函数。

## 🛠 安装方法

在你的 PlatformIO 项目的 `platformio.ini` 中添加：

```ini
lib_deps = 
    dragon99617/ATK-MD0280-LCD