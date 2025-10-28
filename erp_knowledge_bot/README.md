# ERP Knowledge Bot（RAG 问答）

## 项目简介
将企业的 ERP 实施文档、SOP、FAQ 与实施笔记构建成可检索的知识库，结合向量检索（embeddings + vector DB）与生成模型，实现面向业务用户的自然语言问答（RAG）。适合展示你对业务理解、数据清洗、信息检索与大模型集成能力。

## 目标
- 将企业文档（300-2000 条记录）构建向量索引并提供检索接口
- 实现带来源出处的答案与引用片段，提升用户信任度
- 在内部用户测试中将首次响应时间从天级降低到秒级

## 技术栈
- Python 3.8+
- LangChain, sentence-transformers 或 OpenAI embeddings
- 向量数据库：FAISS（本地）或 Weaviate/Chroma
- LLM：OpenAI API / 本地开源模型
- Web 服务：FastAPI / Streamlit

## 最小可行代码结构

projects/erp_knowledge_bot/
├─ data/                  # 文档/手册/FAQ 源文件（txt/pdf/markdown）
├─ notebooks/
│  └─ erp_knowledge_bot_demo.ipynb
├─ src/
│  ├─ ingest.py           # 文档读取与预处理
│  ├─ embed.py            # 生成 embeddings
│  ├─ indexer.py          # 向量索引写入与加载
│  └─ app.py              # FastAPI 服务（检索 + 生成）
├─ requirements.txt
└─ README.md

## 安装与运行（示意）
1. 克隆仓库并创建虚拟环境
2. 安装依赖：
   pip install -r requirements.txt
3. 准备数据：把企业文档放到 `data/` 目录
4. 运行数据导入与索引脚本：
   python src/ingest.py --data_dir data/ --out_index index/
5. 启动服务：
   python src/app.py

## 量化指标（建议在简历/项目页填充）
- 文档量：示例 300 条
- 平均检索响应时间： ≤ 1s（含网络延迟）
- 用户首次自助命中率：30% -> 70%（POC 指标示例）

## 扩展建议
- 加入多轮会话记忆与检索上下文
- 对敏感/合规内容做过滤与审计
- 接入 Slack/Teams 工具，做内部试点

## 参考
- LangChain 文档
- sentence-transformers 使用示例
