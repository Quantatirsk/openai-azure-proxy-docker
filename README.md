# openai-azure-proxy-docker

openai-azure-proxy的docker版，可以将Azure OpenAI的接口转换为标准OpenAI接口发起请求，项目来源：[https://github.com/haibbo/cf-openai-azure-proxy](https://github.com/haibbo/cf-openai-azure-proxy)

改动docker-compose.yml里环境变量 `environment` 资源名称、模型自定义名称即可。

#### docker-compose.yml

```yaml
version: '3'
services:
  azure-openai-proxy:
    image: quantatrisk/openai-azure-proxy:latest
    container_name: azure-openai-proxy
    environment:
      - RESOURCE_NAME=changeme   #  Your Azure OpenAI Resourse Name.   eg.  changeme.openai.azure.com
      - DEPLOY_NAME_GPT35=gpt-35-turbo
      - DEPLOY_NAME_GPT35_16K=gpt-35-turbo-16k
      - DEPLOY_NAME_GPT4=gpt-4
      - DEPLOY_NAME_GPT4_32K=gpt-4-32k
      - DEPLOY_NAME_GPT35_INSTRUCT_16K=gpt-35-turbo-instruct
      - API_VERSION=2023-08-01-preview
    ports:
      - "127.0.0.1:8787:8787"   # for production usage, 127.0.0.1 is recommend 
    restart: unless-stopped

```
