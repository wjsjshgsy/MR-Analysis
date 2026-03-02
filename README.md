GM-Gene-NDD: Tri-Association Mapping via MR & QTL
本项目旨在利用系统遗传学方法探讨肠道微生物 (Gut Microbiota)、宿主遗传变异 (Host Genetics) 与 神经退行性疾病 (Neurodegenerative Diseases) 之间的因果关联。
📌 项目简介
通过整合多组学数据，本项目采用孟德尔随机化 (MR) 作为核心推断手段，并结合 eQTL 与 mQTL 证据，解析“微生物-肠-脑轴”在神经退行性疾病中的分子机制。
🛠 核心方法
Mendelian Randomization (MR): 使用双样本 MR、多变量 MR (MVMR) 及敏感性分析 (MR-Egger, MR-PRESSO) 评估因果性。
eQTL Integration: 整合组织特异性表达 QTL 数据，识别调节微生物效应的中介基因。
mQTL Analysis: 引入代谢/甲基化 QTL，解析微生物代谢产物与宿主遗传的交互作用。
Colocalization (coloc): 评价 GWAS 信号与 QTL 信号的共定位概率。
📊 数据来源 (Data Sources)
在此处添加您的数据来源详细信息
Gut Microbiota GWAS: [例如：MiBioGen, DMP 等]
Neurodegenerative Diseases GWAS: [例如：FinnGen, UK Biobank, ADGC 等]
QTL Data: [例如：GTEx V8, eQTLGen 等]
🚀 分析流程
Preprocessing: 汇总统计数据清洗与等位基因对齐。
IV Selection: 筛选强相关、非连锁不平衡的工具变量。
Causal Inference: 执行 IVW 及多种鲁棒性检验。
Mediation & Coloc: 结合 QTL 数据进行中介分析与共定位验证。
💻 环境要求
Language: R ≥ 4.1
Key Packages: TwoSampleMR, MendelianRandomization, MRPRESSO, coloc
📧 联系方式
Maintainer: [您的姓名]
Email: [您的邮箱]
