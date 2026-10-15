# A12 智课生成系统

基于 AI 的智课生成系统，上传课件后自动提取知识点、生成讲解脚本、合成语音，并支持实时问答与进度续接。

## 在线体验

https://a12-zhike.streamlit.app

## 功能

- 上传 PPT / PDF 课件
- AI 自动提取知识点
- 生成讲授脚本
- TTS 语音合成
- 字幕点击跳转 + 自动连播
- 实时问答（基于课件内容）
- 进度续接（从提问的知识点继续讲授）
- 10 个标准 API 接口

## 技术栈

- Python
- Streamlit
- 智谱 GLM-4-Flash
- Edge TTS
- FastAPI

## 本地运行

### 1. 安装依赖

pip install streamlit python-pptx pdfplumber edge-tts openai fastapi uvicorn python-multipart -i https://pypi.tuna.tsinghua.edu.cn/simple

### 2. 配置 API Key

在项目根目录新建 `.streamlit/secrets.toml`，内容：

ZHIPU_API_KEY = "你的智谱Key"

智谱 Key 申请地址：https://bigmodel.cn

### 3. 启动

开两个终端。

终端 1（主界面）：

streamlit run app.py

终端 2（API 接口）：

uvicorn api:app --reload --port 8000

### 4. 访问

- 主界面：http://localhost:8501
- API 文档：http://127.0.0.1:8000/docs

## 使用流程

1. 上传 PPT 或 PDF
2. 点“提取知识点”
3. 点“生成讲授脚本”
4. 点“生成语音”
5. 点“开始播放”，可点字幕跳转，自动连播
6. 在问答区提问
7. 点“从这里继续讲授”

## 项目结构

A12/
├── .streamlit/
│   └── secrets.toml
├── app.py              # 主程序（Streamlit）
├── api.py              # API 接口（FastAPI）
├── requirements.txt    # 依赖清单
└── README.md
