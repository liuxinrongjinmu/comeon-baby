# 发票与订单信息抽取（OCR + NER）

## 项目简介
实现对纸质或扫描发票/订单的自动识别与关键字段抽取（发票号、金额、开票日期、供应商、税号等），并与 SAP 中的发票/订单记录做自动匹配与异常提示，减少人工录入与复核工作量。

## 目标
- 从图片/PDF 提取结构化字段并输出 JSON
- 对关键字段进行规则/模型双重校验，定位异常并生成人工复核清单
- 在小样本（500 张）上实现 ≥85% 的关键字段正确率（POC 指标示例）

## 技术栈
- OCR：PaddleOCR / Tesseract / easyocr
- NER：spaCy / Hugging Face transformers（中文模型或finetune）
- 规则与匹配：Python, regex, pandas
- 部署：FastAPI, Docker

## 最小可行代码结构
projects/invoice_ocr_ner/
├─ data/                  # 示例发票图片或 PDF
├─ notebooks/
│  └─ invoice_ocr_demo.ipynb
├─ src/
│  ├─ ocr.py              # OCR 读取图片并生成文本
│  ├─ ner.py              # NER 或基于模板的字段抽取
│  ├─ match.py            # 与 SAP 数据的匹配逻辑（示例 CSV）
│  └─ app.py              # 提供批量处理与单票查询接口
├─ requirements.txt
└─ README.md

## 安装与运行（示意）
1. pip install -r requirements.txt
2. 准备示例图片放入 data/
3. 运行 demo notebook 以查看单票抽取效果

## 量化指标（建议填写）
- 测试票数：500 张
- 字段抽取准确率：示例 ≥85%
- 自动匹配成功率：示例 70%（其余进入人工复核）

## 扩展建议
- 基于已标注数据微调 NER 模型
- 增加对不同票据模板的自适应布局解析
- 集成到 SAP 接口，实现自动记账或工单创建
