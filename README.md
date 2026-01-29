# 基于 YOLOv8 的车牌检测与识别系统 (Car Plate Detection)

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![YOLOv8](https://img.shields.io/badge/Model-YOLOv8-green)](https://github.com/ultralytics/ultralytics)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📌 项目简介 (Overview)
本项目是我本科毕业设计的一部分，实现了一个基于 **YOLOv8** 深度学习框架的车牌检测系统。系统能够从复杂背景中精准定位车牌，并为后续的字符识别提供高质量的候选区域。

**核心亮点：**
- 采用 Ultralytics 最新的 YOLOv8 架构，兼顾检测精度与实时性。
- 针对电子信息工程应用场景，打通了从图像采集到结果输出的全链路。
- 具有清晰的代码结构，方便移植到 Linux 嵌入式平台（如树莓派、Jetson Nano）。

---

## 📸 效果演示 (Demo)
> *[注：请在项目目录下创建 `docs/` 文件夹并放入一张识别成功的图片，命名为 `result.jpg`]*
![检测结果演示](./docs/result.jpg)

---

## 🛠️ 环境配置 (Installation)

推荐使用 **Anaconda** 或 **WSL2 (Ubuntu)** 搭建环境：

bash
克隆项目
git clone [https://github.com/LED-master/YOLOv8-car_plate_Detection.git](https://github.com/LED-master/YOLOv8-car_plate_Detection.git)
cd YOLOv8-car_plate_Detection
🚀 使用说明 (Usage)
1. 模型预测 (Inference)
你可以直接使用训练好的权重进行推理：

Python

from ultralytics import YOLO

# 加载模型
model = YOLO('path/to/your/best.pt')

# 执行检测
results = model.predict(source='your_image.jpg', save=True, conf=0.5)
2. 导出模型 (Export)
为了部署到嵌入式端，支持导出多种格式：

Bash

yolo export model=best.pt format=onnx  # 导出为 ONNX 格式
📊 性能评估 (Performance)
在测试集上的表现如下：

准确率 (mAP@50): ~85% (实验室标准环境)

推理延迟: ~15ms (RTX 30系列显卡) / ~150ms (CPU)

现状分析： 目前系统在光照均匀、车牌清晰的场景下表现极佳。但在极端天气（雾霾、雨天）或强逆光环境下存在漏检，这也是我接下来的优化重点。

🛠️ 待办事项 (Future Work)
[ ] 数据增强：引入混合噪声、随机光照调整，提升复杂环境下的鲁棒性。

[ ] 轻量化部署：将模型量化为 TensorRT 或 OpenVINO 格式，进一步降低端侧延迟。

[ ] 软硬件协同：通过串口（Serial）将检测结果发送至 STM32，实现道闸模拟控制。

📧 联系方式 (Contact)
Author: 赵中豪 (Zhonghao Zhao)

Email: nbzhonghao@outlook.com

GitHub: LED-master

If you find this project helpful, please give it a ⭐️!

# 安装核心依赖
pip install ultralytics opencv-python numpy
