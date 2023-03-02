# 模型
## 概述

OpenAI API由不同功能和价格点的各种模型驱动。您还可以通过[微调](https://platform.openai.com/docs/guides/fine-tuning)对我们原始的基础模型进行有限的自定义，以适应您的特定用例。


| 模型 | 描述 |
| --- | --- |
| [GPT-3.5](https://platform.openai.com/docs/models/gpt-3-5) | 一整套模型，它们在 GPT-3 的基础上进行了改进，能够理解和生成自然语言或代码。 |
| [DALL·E](https://platform.openai.com/docs/models/dall-e) | 一个可以根据自然语言提示生成和编辑图像的模型。 |
| [Whisper](https://platform.openai.com/docs/models/whisper) | 一个可以将音频转换为文本的模型 |
| [Embeddings](https://platform.openai.com/docs/models/embeddings) | 一个能够将文本转换为数字形式的模型集合 |
| [Codex](https://platform.openai.com/docs/models/codex) Limited beta |一整套可以理解和生成代码的模型，包括将自然语言翻译成代码的模型。 |
| [Moderation](https://platform.openai.com/docs/models/moderation) | 一种经过微调的模型，可以检测文本是否可能包含敏感或不安全内容。 |
| [GPT-3](https://platform.openai.com/docs/models/gpt-3) | 一整套能够理解和生成自然语言的模型 |

我们还发布了一些开源模型，包括[Point-E](https://github.com/openai/point-e)、[whisper](https://github.com/openai/whisper)、[Jukebox](https://github.com/openai/jukebox)和[CLIP](https://github.com/openai/CLIP)。

请访问我们的[模型索引页面](https://platform.openai.com/docs/model-index-for-researchers)，以了解哪些模型被用于我们的研究论文以及类似InstructGPT和GPT-3.5等模型系列之间的差异。

## GPT-3.5

GPT-3.5模型可以理解和生成自然语言或代码。我们最强大且成本效益最高的模型是 `gpt-3.5-turbo`，它经过优化，适用于聊天，但在传统的完成任务中也表现良好。

| 最新模型 | 描述 | 最大请求 | 训练数据 |
| --- | --- | --- | --- |
| gpt-3.5-turbo | 最强大的GPT-3.5模型，针对聊天进行了优化，成本是 `text-davinci-003` 的 1/10。将随着我们的最新模型迭代进行更新。 | 4,096 tokens | 截至2021年9月 |
| gpt-3.5-turbo-0301 |2023年3月1日的 `gpt-3.5-turbo` 快照。与 `gpt-3.5-turbo` 不同，该模型将不会接收更新，并且只支持为期三个月，截至2023年6月1日。 | 4,096 tokens | 截至2021年9月 |
| text-davinci-003 | 该模型可处理各种语言任务，其输出质量更好、长度更长，指令遵循更一致，比Curie、Babbage或Ada模型更为出色。同时，该模型还支持在文本中[插入](https://platform.openai.com/docs/guides/completion/inserting-text)自动完成。| 4,000 tokens | 截至2021年6月 |
| text-davinci-002 | 使用有监督的微调训练，具有与 `text-davinci-003` 相似的能力，而不是使用强化学习。 | 4,000 tokens | 截至2021年6月 |
| code-davinci-002 | 优化用于代码自动完成任务 | 4,000 tokens | 截至2021年6月 |

我们建议在尝试实验时使用 `gpt-3.5-turbo`，因为它将产生最好的结果。一旦您的实验得到了很好的运行，我们鼓励您尝试其他模型，以查看是否可以以更低的延迟或成本获得相同的结果。

> OpenAI模型是非确定性的，这意味着相同的输入可能会产生不同的输出。将[温度(temperature)](https://platform.openai.com/docs/api-reference/completions/create#completions/create-temperature)设置为0会使输出基本上是确定性的，但仍可能存在一些小的可变性。

### 特定功能模型

虽然新的 `gpt-3.5-turbo` 模型是为聊天优化的，但它也非常适合传统的自动完成任务。原始的 `GPT-3.5` 模型是为[文本自动完成](https://platform.openai.com/docs/guides/completion)而优化的。

我们为[创建嵌入](https://platform.openai.com/docs/guides/embeddings)和[编辑文本](https://platform.openai.com/docs/guides/completion/editing-text)的端点使用自己的一组专门的模型。

### Turbo

Turbo模型是ChatGPT所使用的同一模型家族。它针对对话式聊天输入和输出进行了优化，但与Davinci模型系列相比，在完成任务时表现同样出色。在API中使用ChatGPT表现良好的任何用例，使用Turbo模型系列都应该表现良好。

Turbo模型系列也是首个定期接收模型更新的模型系列，类似于ChatGPT。

擅长：**对话和文本生成**。

### Davinci

Davinci 是最具能力的模型系列，可以执行其他模型（ada、curie 和 babbage）可以执行的任何任务，而且通常需要更少的指令。对于需要对内容有很深入理解的应用，例如特定受众的摘要和创意内容生成，Davinci 将产生最佳结果。这些增加的功能需要更多的计算资源，因此每个 API 调用的成本更高，而且速度不如其他模型快。

Davinci 另一个擅长的领域是理解文本意图。Davinci 在解决许多逻辑问题和解释字符动机方面非常出色。Davinci 能够解决一些涉及因果关系的最具挑战性的人工智能问题。

擅长的领域：**复杂的意图、因果关系、受众摘要**。

### Babbage