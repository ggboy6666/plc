# plc

AI 生成 PLC 程序示例。

## 本仓库内容

- `SCL_MachiningCell.scl`：三台机床 + 1 台库卡机器人 + 4 个托盘架（每盘 40 件）柔性单元控制示例。
- 采用“每个功能单独块 + 每块有注释”的结构，方便快速定位程序：
  - `FC_AlarmTextID`：报警码映射到 HMI 文本 ID
  - `FC_CheckSafetyAndAlarm`：安全与设备故障统一判断
  - `FB_MachineUnit`：单机床状态机（3 个实例并行）
  - `FB_RobotDispatcher`：机器人调度、托盘/手抓/工件处理
  - `FC_CalcStats`：已加工/未加工/在制统计
  - `FB_FlexibleCell`：总控状态机与人机交互

- 程序开头新增“信号总表（类型 + 起始偏移）”，列出安全/HMI/机器人/机床I/O、控制输出与统计变量地址建议，便于快速对照接线与组态。
