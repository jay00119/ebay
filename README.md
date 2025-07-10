# eBay市场分析工具

这是一个集成了eBay商品标题抓取和爆款分析功能的工具。它由两个后端服务和一个前端界面组成。

## 项目结构

- `ebayTest_backend/`: 关键词分析（原eBay商品标题抓取工具）的后端服务。
- `ebay2_backend/`: 爆款分析（原eBay爆款分析器）的后端服务。
- `frontend/`: 合并后的前端界面。

## 部署说明

### 1. 克隆仓库

```bash
git clone https://github.com/jay00119/ebay.git
cd ebay
```

### 2. 后端服务设置

#### 2.1 关键词分析后端 (`ebayTest_backend`)

1.  进入目录：
    ```bash
    cd ebayTest_backend
    ```
2.  创建并激活虚拟环境：
    ```bash
    python3.11 -m venv venv
    source venv/bin/activate
    ```
3.  安装依赖：
    ```bash
    pip install -r requirements.txt
    ```
4.  启动服务（监听在5002端口）：
    ```bash
    python3.11 src/main.py
    ```

#### 2.2 爆款分析后端 (`ebay2_backend`)

1.  进入目录：
    ```bash
    cd ../ebay2_backend
    ```
2.  创建并激活虚拟环境：
    ```bash
    python3.11 -m venv venv
    source venv/bin/activate
    ```
3.  安装依赖：
    ```bash
    pip install -r requirements.txt
    ```
4.  启动服务（监听在5000端口）：
    ```bash
    python3.11 src/main.py
    ```

### 3. 前端界面设置 (`frontend`)

1.  进入目录：
    ```bash
    cd ../frontend
    ```
2.  启动HTTP服务器（监听在8080端口）：
    ```bash
    python3.11 -m http.server 8080 --bind 0.0.0.0
    ```

### 4. DeepL API密钥

关键词分析功能使用了DeepL API进行翻译。您需要在 `ebayTest_backend/src/routes/deepl_api.py` 文件中配置您的DeepL API密钥。找到以下行：

```python
deepl_client = deepl.Translator("YOUR_DEEPL_API_KEY")
```

将 `YOUR_DEEPL_API_KEY` 替换为您的实际DeepL API密钥。

### 5. 访问工具

在所有服务都成功启动后，您可以通过访问前端HTTP服务器的地址来使用该工具。如果部署在本地，通常是 `http://localhost:8080/static/index.html`。如果部署在云端，请使用相应的公共URL。

## 注意事项

- 确保您的Python环境为3.11或更高版本。
- 后端服务需要保持运行状态，前端才能正常工作。
- 如果您更改了后端服务的端口，请务必更新前端 `frontend/static/index.html` 中对应的API地址。


