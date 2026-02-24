# plc

AI 生成 PLC 程序示例。

## 本仓库内容

- `SCL_MachiningCell.scl`：三台机床 + 1 台库卡机器人 + 4 个托盘架（每盘 40 件）柔性单元控制示例。
- 本版本按“每个功能单独块”拆分：
  - `FC_CheckSafetyAndAlarm`：安全与故障统一判断
  - `FB_MachineUnit`：单机床状态机（可实例化 3 次并行运行）
  - `FB_RobotDispatcher`：机器人上/下料、手抓与托盘分配
  - `FC_CalcStats`：加工统计汇总
  - `FB_FlexibleCell`：单元总控与 HMI 交互
