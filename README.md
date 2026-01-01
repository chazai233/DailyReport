# DailyReport - Word Document Generation Service

FastAPI 服务，用于生成格式化的施工日报 Word 文档（中英文双语）。

## 功能特性

- 🔄 自动获取天气数据 (Pakbeng, Laos)
- 📄 基于模板生成 Word 文档
- 🌐 支持中英文双语输出
- 📊 自动表格格式化与单元格合并

## 快速部署

### Zeabur 部署

1. Fork 此仓库
2. 登录 [Zeabur](https://zeabur.com)
3. 新建项目 → Deploy from GitHub → 选择此仓库
4. 配置环境变量（见下方）

### 环境变量

| 变量名 | 说明 | 必需 |
|--------|------|------|
| `TEMPLATE_CN_BASE64` | 中文模板 Base64 编码 | 推荐 |
| `TEMPLATE_EN_BASE64` | 英文模板 Base64 编码 | 推荐 |

## API 端点

| 端点 | 方法 | 说明 |
|------|------|------|
| `/` | GET | 服务状态 |
| `/health` | GET | 健康检查 |
| `/generate-from-template` | POST | 生成 Word 文档 |
| `/docs` | GET | Swagger API 文档 |

## 本地开发

```bash
# 安装依赖
pip install -r requirements.txt

# 启动服务
uvicorn main:app --host 0.0.0.0 --port 8000

# 访问 API 文档
open http://localhost:8000/docs
```

## 请求示例

```json
POST /generate-from-template
{
  "chinese_data": "[{\"seq\":1,\"location\":\"右岸道路\",\"content\":\"道路路面整平\",\"quantity\":\"100m\",\"shift\":\"\"}]",
  "english_data": "{\"translated_data\":[{\"seq\":1,\"location_en\":\"Right Bank Road\",\"content_en\":\"Road surface grading\",\"quantity_en\":\"100m\",\"remarks_en\":\"\"}]}"
}
```

## 许可证

MIT License
