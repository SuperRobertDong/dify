# Dify 项目分析

## 1. 项目的前后台架构
- 前端：位于`/web`目录，使用Next.js框架
- 后端：位于`/api`目录，基于Python构建的API服务
- SDK：位于`/sdks`目录，提供多语言客户端库

## 2. 开发语言
- 前端：TypeScript (56.9%)和JavaScript (8.0%)
- 后端：Python (30.4%)
- 其他：CSS/SCSS等样式语言

## 3. 数据库和插件
根据项目结构和docker配置推断:
- PostgreSQL：主数据库
- Redis：缓存和会话管理
- Weaviate/Milvus：向量数据库(用于RAG功能)

## 4. Docker安装测试环境
是的，可以通过Docker安装：
```
cd dify
cd docker
cp .env.example .env
docker compose up -d
```
安装后访问 http://localhost/install 进行初始化。

## 5. MacBook本地开发环境搭建
1. 克隆代码仓库：`git clone https://github.com/langgenius/dify.git`
2. 后端设置：
   ```
   cd api
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```
3. 前端设置：
   ```
   cd web
   npm install
   ```

## 6. 本地开发和调试
- 后端：
  ```
  cd api
  flask run --debug
  ```
- 前端：
  ```
  cd web
  npm run dev
  ```
调试信息会显示在终端，也可在代码中添加日志语句。

## 7. 项目功能
Dify是开源LLM应用开发平台，提供：
- 可视化AI工作流设计
- 支持多种LLM模型(GPT、Mistral、Llama3等)
- 提示词IDE界面
- RAG功能管道(检索增强生成)
- Agent功能和50多种预建工具
- LLMOps应用监控和分析
- 完整API服务

## 8. License限制
使用Dify Open Source License(基于Apache 2.0但有额外限制)。主要限制可能包括：
- 不得删除或修改Dify的版权信息
- 如进行商业化，需要注明使用了Dify
- 二次开发允许，但可能对直接竞争产品有限制

建议在商业化前详细查看LICENSE文件中的完整条款。

## 9. 项目版本信息
### 前端版本
- Next.js: v14.2.10
- Node.js: >=18.17.0 (引擎要求)
- React: ~18.2.0
- TypeScript: 4.9.5

### 后端版本
- Python: 3.11-3.12 (根据pyproject.toml中的requires-python字段)
- Dockerfile基于: Python 3.12-slim-bookworm
- Flask: ~3.1.0
- SQLAlchemy: ~2.0.29
- Celery: ~5.4.0 