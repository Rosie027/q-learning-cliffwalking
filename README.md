# Q-learning 悬崖迷宫

在 Gym `CliffWalking-v0` 环境中实现表格型 Q-learning，用于理解状态—动作价值、ε-greedy 探索、时序差分更新和策略评估。

## 实验设置

| 参数 | 数值 |
| --- | --- |
| 学习率 `alpha` | 0.5 |
| 折扣因子 `gamma` | 0.99 |
| 探索率 `epsilon` | 0.1 |
| 训练回合 | 500 |

核心更新公式：

```text
Q(s, a) ← Q(s, a) + α[r + γ max Q(s', a') - Q(s, a)]
```

主 Notebook：`notebooks/q-learning-cliffwalking.ipynb`。

## 实现流程

1. 创建 4×12 Cliff Walking 环境和 Q 表；
2. 使用 ε-greedy 在探索与利用之间选择动作；
3. 执行动作并使用下一状态最大 Q 值更新当前状态动作；
4. 记录每回合奖励并绘制学习曲线；
5. 使用贪心策略评估最终路线，并绘制路径与 Q 值热力图。

原始实验中最终评估总奖励达到 **-13**，对应从起点到终点的最短安全路径长度。公开 Notebook 已清除平台日志与历史输出，重新运行结果会受随机探索影响。

## 运行

```bash
python -m pip install -r requirements.txt
jupyter lab
```

Notebook 保留 `gym==0.26.2` 以匹配原实验。Gym 已停止维护，后续版本计划迁移到 Gymnasium；迁移时需要同步检查 `reset`、`step` 和环境注册接口。

## 迭代时间线

| 日期 | 阶段 |
| --- | --- |
| 2026-04-14 | 强化学习课程与实验材料准备 |
| 2026-04-28 | Q-learning Notebook 完成 |
| 2026-05-09 | 实验报告整理 |
| 2026-10-12 | 排除课程资料和个人信息，整理独立公开仓库 |

日期来自现存文件时间与实验记录，不等同于 Git 提交历史。

## 学习要点

- 马尔可夫决策过程中的状态、动作与奖励；
- on-policy 与 off-policy 方法的区别；
- ε-greedy 探索；
- Q-learning 更新与收敛直觉；
- 奖励曲线、策略路径和价值热力图的解释。
