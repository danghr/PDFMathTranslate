[**Documentation**](https://github.com/Byaidu/PDFMathTranslate) > **Advanced Usage** _(current)_

---

<h3 id="toc">Table of Contents</h3>

- [Full / partial translation](#partial)
- [Specify source and target languages](#language)
- [Translate with different services](#services)
- [Translate wih exceptions](#exceptions)
- [Multi-threads](#threads)
- [Custom prompt](#prompt)

---

<h3 id="partial">Full / partial translation</h3>

- Entire document

  ```bash
  pdf2zh example.pdf
  ```

- Part of the document

  ```bash
  pdf2zh example.pdf -p 1-3,5
  ```

[⬆️ Back to top](#toc)

---

<h3 id="language">Specify source and target languages</h3>

See [Google Languages Codes](https://developers.google.com/admin-sdk/directory/v1/languages), [DeepL Languages Codes](https://developers.deepl.com/docs/resources/supported-languages)

```bash
pdf2zh example.pdf -li en -lo ja
```

[⬆️ Back to top](#toc)

---

<h3 id="services">Translate with different services</h3>

We've provided a detailed table on the required [environment variables](https://chatgpt.com/share/6734a83d-9d48-800e-8a46-f57ca6e8bcb4) for each translation service. Make sure to set them before using the respective service.

|**Translator**|**Service**|**Environment Variables**|**Default Values**|**Notes**|
|-|-|-|-|-|
|**Google (Default)**|`google`|None|N/A|None|
|**Bing**|`bing`|None|N/A|None|
|**DeepSeek Chat**|`deepseek-chat`| `DEEPSEEKCHAT_BASE_URL`, `DEEPSEEKCHAT_API_KEY`, `DEEPSEEKCHAT_MODEL` | `https://api.deepseek.com/v1`, `[Your DEEPSEEK_API_KEY]`, `deepseek-chat` |See [DeepSeek](https://www.deepseek.com/)|
|**DeepSeek Reasoner**|`deepseek-reasoner`| `DEEPSEEKREASONER_BASE_URL`, `DEEPSEEKREASONER_API_KEY`, `DEEPSEEKREASONER_MODEL` | `https://api.deepseek.com/v1`, `[Your DEEPSEEK_API_KEY]`, `deepseek-reasoner` |See [DeepSeek](https://www.deepseek.com/)|
|**DeepSeek Reasoner (Distill)**|`deepseek-reasoner-distill`| `DEEPSEEKREASONERDISTILL_BASE_URL`, `DEEPSEEKREASONERDISTILL_API_KEY`, `DEEPSEEKREASONERDISTILL_MODEL` | `https://dashscope.aliyuncs.com/compatible-mode/v1`, `[Your API Key]`, `deepseek-r1-distill-qwen-32b` |See [Aliyun Bailian](https://bailian.console.aliyun.com/)|
|**QWen MT Turbo**|`qwen-mt-turbo`| `QWENMTTURBO_MODEL`, `QWENMTTURBO_API_KEY` | `[Your API Key]`, `qwen-mt-turbo` |See [Aliyun Bailian](https://bailian.console.aliyun.com/)|
|**QWen MT Max**|`qwen-mt-plus`| `QWENMTTURBO_MODEL`, `QWENMTTURBO_API_KEY` | `[Your API Key]`, `qwen-mt-plus` |See [Aliyun Bailian](https://bailian.console.aliyun.com/)|
<!-- |**OpenAI-Liked**|`openailiked`| `OPENAILIKED_BASE_URL`, `OPENAILIKED_API_KEY`, `OPENAILIKED_MODEL` | `url`, `[Your Key]`, `model name` | None | -->
<!-- |**DeepL**|`deepl`|`DEEPL_AUTH_KEY`|`[Your Key]`|See [DeepL](https://support.deepl.com/hc/en-us/articles/360020695820-API-Key-for-DeepL-s-API)| -->
<!-- |**DeepLX**|`deeplx`|`DEEPLX_ENDPOINT`|`https://api.deepl.com/translate`|See [DeepLX](https://github.com/OwO-Network/DeepLX)| -->
<!-- |**Ollama**|`ollama`|`OLLAMA_HOST`, `OLLAMA_MODEL`|`http://127.0.0.1:11434`, `gemma2`|See [Ollama](https://github.com/ollama/ollama)| -->
<!-- |**OpenAI**|`openai`|`OPENAI_BASE_URL`, `OPENAI_API_KEY`, `OPENAI_MODEL`|`https://api.openai.com/v1`, `[Your Key]`, `gpt-4o-mini`|See [OpenAI](https://platform.openai.com/docs/overview)| -->
<!-- |**AzureOpenAI**|`azure-openai`|`AZURE_OPENAI_BASE_URL`, `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_MODEL`|`[Your Endpoint]`, `[Your Key]`, `gpt-4o-mini`|See [Azure OpenAI](https://learn.microsoft.com/zh-cn/azure/ai-services/openai/chatgpt-quickstart?tabs=command-line%2Cjavascript-keyless%2Ctypescript-keyless%2Cpython&pivots=programming-language-python)| -->
<!-- |**Zhipu**|`zhipu`|`ZHIPU_API_KEY`, `ZHIPU_MODEL`|`[Your Key]`, `glm-4-flash`|See [Zhipu](https://open.bigmodel.cn/dev/api/thirdparty-frame/openai-sdk)| -->
<!-- | **ModelScope**       | `modelscope`   |`MODELSCOPE_API_KEY`, `MODELSCOPE_MODEL`|`[Your Key]`, `Qwen/Qwen2.5-Coder-32B-Instruct`| See [ModelScope](https://www.modelscope.cn/docs/model-service/API-Inference/intro)| -->
<!-- |**Silicon**|`silicon`|`SILICON_API_KEY`, `SILICON_MODEL`|`[Your Key]`, `Qwen/Qwen2.5-7B-Instruct`|See [SiliconCloud](https://docs.siliconflow.cn/quickstart)| -->
<!-- |**Gemini**|`gemini`|`GEMINI_API_KEY`, `GEMINI_MODEL`|`[Your Key]`, `gemini-1.5-flash`|See [Gemini](https://ai.google.dev/gemini-api/docs/openai)| -->
<!-- |**Azure**|`azure`|`AZURE_ENDPOINT`, `AZURE_API_KEY`|`https://api.translator.azure.cn`, `[Your Key]`|See [Azure](https://docs.azure.cn/en-us/ai-services/translator/text-translation-overview)| -->
<!-- |**Tencent**|`tencent`|`TENCENTCLOUD_SECRET_ID`, `TENCENTCLOUD_SECRET_KEY`|`[Your ID]`, `[Your Key]`|See [Tencent](https://www.tencentcloud.com/products/tmt?from_qcintl=122110104)| -->
<!-- |**Dify**|`dify`|`DIFY_API_URL`, `DIFY_API_KEY`|`[Your DIFY URL]`, `[Your Key]`|See [Dify](https://github.com/langgenius/dify),Three variables, lang_out, lang_in, and text, need to be defined in Dify's workflow input.| -->
<!-- |**AnythingLLM**|`anythingllm`|`AnythingLLM_URL`, `AnythingLLM_APIKEY`|`[Your AnythingLLM URL]`, `[Your Key]`|See [anything-llm](https://github.com/Mintplex-Labs/anything-llm)| -->
<!-- |**Argos Translate**|`argos`| | |See [argos-translate](https://github.com/argosopentech/argos-translate)| -->
<!-- |**Grok**|`grok`| `GORK_API_KEY`, `GORK_MODEL` | `[Your GORK_API_KEY]`, `grok-2-1212` |See [Grok](https://docs.x.ai/docs/overview)| -->

<!-- For large language models that are compatible with the OpenAI API but not listed in the table above, you can set environment variables using the same method outlined for OpenAI in the table. -->

Use `-s service` or `-s service:model` to specify service:

```bash
pdf2zh example.pdf -s openai:gpt-4o-mini
```

Or specify model with environment variables:

```bash
set OPENAI_MODEL=gpt-4o-mini
pdf2zh example.pdf -s openai
```

For PowerShell user:
```shell
$env:OPENAI_MODEL = gpt-4o-mini
pdf2zh example.pdf -s openai
```

[⬆️ Back to top](#toc)

---

<h3 id="exceptions">Translate wih exceptions</h3>

Use regex to specify formula fonts and characters that need to be preserved:

```bash
pdf2zh example.pdf -f "(CM[^RT].*|MS.*|.*Ital)" -c "(\(|\||\)|\+|=|\d|[\u0080-\ufaff])"
```

Preserve `Latex`, `Mono`, `Code`, `Italic`, `Symbol` and `Math` fonts by default:

```bash
pdf2zh example.pdf -f "(CM[^R]|MS.M|XY|MT|BL|RM|EU|LA|RS|LINE|LCIRCLE|TeX-|rsfs|txsy|wasy|stmary|.*Mono|.*Code|.*Ital|.*Sym|.*Math)"
```

[⬆️ Back to top](#toc)

---

<h3 id="threads">Multi-threads</h3>

Use `-t` to specify how many threads to use in translation:

```bash
pdf2zh example.pdf -t 1
```

[⬆️ Back to top](#toc)

---

<h3 id="prompt">Custom prompt</h3>

Use `--prompt` to specify which prompt to use in llm:

```bash
pdf2zh example.pdf --prompt prompt.txt
```

example prompt.txt

```
[
    {
        "role": "system",
        "content": "You are a professional,authentic machine translation engine.",
    },
    {
        "role": "user",
        "content": "Translate the following markdown source text to ${lang_out}. Keep the formula notation {{v*}} unchanged. Output translation directly without any additional text.\nSource Text: ${text}\nTranslated Text:",
    },
]
```

In custom prompt file, there are three variables can be used.
|**variables**|**comment**|
|-|-|
|`lang_in`|input language|
|`lang_out`|output language|
|`text`|text need to be translated|

[⬆️ Back to top](#toc)

---

<h3 id="auth">Authorization</h3>

Use `--authorized` to specify which user to use Web UI and custom the login page:

```bash
pdf2zh example.pdf --authorized users.txt auth.html
```

example users.txt
Each line contains two elements, username, and password, separated by a comma.

```
admin,123456
user1,password1
user2,abc123
guest,guest123
test,test123
```

example auth.html

```html
<!DOCTYPE html>
<html>
<head>
    <title>Simple HTML</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>Welcome to my simple HTML page.</p>
</body>
</html>
```

[⬆️ Back to top](#toc)

---

<h3 id="cofig">Custom configuration file</h3>

Use `--config` to specify which file to configure the PDFMathTranslate:

```bash
pdf2zh example.pdf --config config.json
```

```bash
pdf2zh -i --config config.json
```

example config.json
```json
{
    "USE_MODELSCOPE": "0",
    "PDF2ZH_LANG_FROM": "English",
    "PDF2ZH_LANG_TO": "Simplified Chinese",
    "NOTO_FONT_PATH": "/app/SourceHanSerifCN-Regular.ttf",
    "translators": [
        {
            "name": "deeplx",
            "envs": {
                "DEEPLX_ENDPOINT": "http://localhost:1188/translate/",
                "DEEPLX_ACCESS_TOKEN": null
            }
        },
        {
            "name": "ollama",
            "envs": {
                "OLLAMA_HOST": "http://127.0.0.1:11434",
                "OLLAMA_MODEL": "gemma2"
            }
        }
    ]
}
```
By default, the config file is saved in the `~/.config/PDFMathTranslate/config.json`. The program will start by reading the contents of config.json, and after that it will read the contents of the environment variables. When an environment variable is available, the contents of the environment variable are used first and the file is updated.

[⬆️ Back to top](#toc)

---