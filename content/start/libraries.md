---
title: 代码库
---

## Python

我们提供了一个Python库，您可以按照以下方式安装：

```shell
$ pip install openai
```

一旦安装完成，您可以使用绑定和您的密钥运行以下命令：

```python
import os
import openai

# Load your API key from an environment variable or secret management service
openai.api_key = os.getenv("OPENAI_API_KEY")

response = openai.Completion.create(model="text-davinci-003", prompt="Say this is a test", temperature=0, max_tokens=7)
```

该绑定还会安装一个命令行工具，您可以按以下方式使用：

```shell
$ openai api completions.create -m text-davinci-003 -p "Say this is a test" -t 0 -M 7 --stream
```

## Node.js

我们也有一个Node.js库，您可以在Node.js项目目录中运行以下命令进行安装：

```shell
$ npm install openai
```

一旦安装完成，您可以使用该库和您的密钥运行以下命令：

```js
const { Configuration, OpenAIApi } = require("openai");
const configuration = new Configuration({
  apiKey: process.env.OPENAI_API_KEY,
});
const openai = new OpenAIApi(configuration);
const response = await openai.createCompletion({
  model: "text-davinci-003",
  prompt: "Say this is a test",
  temperature: 0,
  max_tokens: 7,
});
```

## 社区

以下库由更广泛的开发者社区构建和维护。如果您想在此处添加新库，请按照我们的[帮助中心文章](https://help.openai.com/en/articles/6684216-adding-your-api-client-to-the-community-libraries-page)中关于添加社区库的说明进行操作。

请注意，OpenAI不会验证这些项目的正确性或安全性。

### C# / .NET

-   [Betalgo.OpenAI.GPT3](https://github.com/betalgo/openai) by [Betalgo](https://github.com/betalgo)


### Crystal

-   [openai-crystal](https://github.com/sferik/openai-crystal) by [sferik](https://github.com/sferik)


### Go

-   [go-gpt3](https://github.com/sashabaranov/go-gpt3) by [sashabaranov](https://github.com/sashabaranov)


### Java

-   [openai-java](https://github.com/TheoKanning/openai-java) by [Theo Kanning](https://github.com/TheoKanning)



### Kotlin

-   [openai-kotlin](https://github.com/Aallam/openai-kotlin) by [Mouaad Aallam](https://github.com/Aallam)



### Node.js

-   [openai-api](https://www.npmjs.com/package/openai-api) by [Njerschow](https://github.com/Njerschow)
-   [openai-api-node](https://www.npmjs.com/package/openai-api-node) by [erlapso](https://github.com/erlapso)
-   [gpt-x](https://www.npmjs.com/package/gpt-x) by [ceifa](https://github.com/ceifa)
-   [gpt3](https://www.npmjs.com/package/gpt3) by [poteat](https://github.com/poteat)
-   [gpts](https://www.npmjs.com/package/gpts) by [thencc](https://github.com/thencc)
-   [@dalenguyen/openai](https://www.npmjs.com/package/@dalenguyen/openai) by [dalenguyen](https://github.com/dalenguyen)
-   [tectalic/openai](https://github.com/tectalichq/public-openai-client-js) by [tectalic](https://tectalic.com/)


### PHP

-   [orhanerday/open-ai](https://packagist.org/packages/orhanerday/open-ai) by [orhanerday](https://github.com/orhanerday)
-   [tectalic/openai](https://github.com/tectalichq/public-openai-client-php) by [tectalic](https://tectalic.com/)


### Python

-   [chronology](https://github.com/OthersideAI/chronology) by [OthersideAI](https://www.othersideai.com/)



### R

-   [rgpt3](https://github.com/ben-aaron188/rgpt3) by [ben-aaron188](https://github.com/ben-aaron188)

### Ruby

-   [openai](https://github.com/nileshtrivedi/openai/) by [nileshtrivedi](https://github.com/nileshtrivedi)
-   [ruby-openai](https://github.com/alexrudall/ruby-openai) by [alexrudall](https://github.com/alexrudall)


### Scala

-   [openai-scala-client](https://github.com/cequence-io/openai-scala-client) by [cequence-io](https://github.com/cequence-io)

[](https://platform.openai.com/docs/libraries/swift)

### Swift

-   [OpenAIKit](https://github.com/dylanshine/openai-kit) by [dylanshine](https://github.com/dylanshine)


### Unity

-   [OpenAi-Api-Unity](https://github.com/hexthedev/OpenAi-Api-Unity) by [hexthedev](https://github.com/hexthedev)


### Unreal Engine

-   [OpenAI-Api-Unreal](https://github.com/KellanM/OpenAI-Api-Unreal) by [KellanM](https://github.com/KellanM)