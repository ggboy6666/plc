# plc

AI 生成 PLC 程序示例。

## 本仓库内容

- `SCL_MachiningCell.scl`：三台机床 + 1 台库卡机器人 + 4 个托盘架（每盘 40 件）柔性单元控制示例。
- 采用“每个功能单独块 + 每块有注释”的结构，方便快速定位程序：
  - `FC_AlarmTextID`：报警码映射到 HMI 文本 ID
  - `FC_CheckSafetyAndAlarm`：安全与设备故障统一判断
  - `FB_MachineUnit`：单机床状态机（3 个实例并行）+ 加工时长统计
  - `FB_RobotDispatcher`：机器人调度、托盘/手抓/工件处理、优先级优化
  - `FC_CalcStats`：已加工/未加工/在制统计
  - `FB_FlexibleCell`：总控状态机与人机交互

## 已实现的关键需求

- 开头提供完整信号总表（信号类型 + 起始偏移建议）。
- 可判断：
  - 机床夹紧是否到位（MachineClampIn）
  - 机器人夹紧是否到位（RobotGripOK）
  - 托盘是否放置到位（TrayRawPlaceOK / TrayDonePlaceOK）
- 托盘40工位逐位追踪：可以区分哪些工件已加工、哪些未加工。
- 若 2 台及以上机床同时完工请求下料，按机床平均加工时长自动优化服务顺序（长节拍优先）。
