# 期末大作业
张家祯　2025104264
　　本研究针对配电网变压器逐小时负荷预测任务，构建了基于 t→t+1 范式的严谨预测框架。通过 2022 与 2023 年跨年数据的对比实验，系统评估了线性回归（Ridge/WLS）、集成学习（HGBR）与深度学习（MLP）在不同特征组合下的表现。研究表明：特征工程是预测精度提升的核心驱动力，其中自回归项的引入使 RMSE 降低了约 23.9%；在模型层面，HGBR 凭借对非线性‘空调效应’及高阶交互特征的捕获能力，在主窗口测试中取得最优性能（MAE=7.30）；而在跨年泛化挑战中，Ridge 回归展现出更强的稳健性，揭示了在分布漂移场景下‘简单模型’的鲁棒性优势。

数据来源：
　　本次研究基于“广西大规模居民负荷数据集”，可以直接从Figshare 下载文件格式为SQLite3的数据库文件，其中包含7 张核心表
数据下载：
 　https://dataminer2.pjm.com/feed/hrl_load_metered

复现说明：
确认使用的包是否齐全
解压 Transformer_DB.7z 文件为 Transformer_DB
将 Transformer_DB.db 放到代码文件对应的文件夹下方
打开 notebook，确认数据库路径变量指向正确位置（常见写法如：DB_PATH = "Transformer_DB.db"）。
运行代码文件即可　Kernel → Restart & Run All

结果检查：
会有以下类型输出：
EDA 图：缺失率、hour×dow 热力图、温度分箱等
A/B/C 结果表：OLS / Ridge / WLS 在不同特征集下的 RMSE/MAE
调参结果：HGBR 网格、MLP 网格、WLS clip 网格的验证集最优选择
残差诊断图
dow×hour 残差均值热力图
典型样本可视化：单个 TRANSFORMER_ID 的 pred vs true 曲线
跨年验证：OutYear 指标对比柱状图 + 跨年典型样本曲线

运行环境：
| 项目           | 推荐版本                                  |
| ------------ | ------------------------------------- |
| OS           | Linux（或 Windows/macOS 亦可，但可能出现极小数值差异） |
| Python       | 3.11.2                                |
| numpy        | 1.24.0                                |
| pandas       | 2.2.3                                 |
| matplotlib   | 3.7.5                                 |
| scikit-learn | 1.4.2                                 |
| sqlite3      | Python 标准库自带（无需单独安装）                  |
