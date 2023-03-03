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

Babbage 能够执行简单分类等简单任务。当涉及语义搜索排名时，Babbage 也相当有能力，可以评估文档与搜索查询的匹配程度。

擅长于：**中等分类，语义搜索分类**。

### Ada

Ada 通常是最快的模型，可以执行解析文本、地址校正和某些不需要太多细节的分类任务。通过提供更多的上下文，可以提高Ada的性能。

擅长于：**解析文本、简单分类、地址校正、关键词**。

*注意：任何由更快的模型（例如Ada）执行的任务都可以由更强大的模型（例如Curie或Davinci）执行。*

## 寻找合适的模型

通过尝试使用gpt-3.5-turbo来进行实验，可以很好地了解这个API能够做些什么。在明确了自己想要实现的目标之后，可以选择继续使用gpt-3.5-turbo或其他模型，并尝试优化其功能。

您可以使用[GPT比较工具](https://gpttools.com/comparisontool)，该工具可以让您并排运行不同的模型以比较输出、设置和响应时间，然后将数据下载到Excel电子表格中。

### DALL·E
DALL·E是一个可以根据自然语言描述创建逼真图像和艺术作品的AI系统。我们目前支持在给定提示的情况下创建指定大小的新图像，编辑现有图像或创建用户提供图像的变体。

我们API中提供的当前DALL·E模型是第二代DALL·E模型，比原始模型产生的图像更加逼真、准确，分辨率也提高了4倍。您可以通过我们的[实验室界面](https://labs.openai.com/)或[API](https://platform.openai.com/docs/guides/images/introduction)进行尝试。

### Whisper
Whisper是一种通用的语音识别模型。它是在大量不同音频数据集的基础上训练的，同时还是一种多任务模型，可执行多语言语音识别、语音翻译和语言识别。目前，Whisper v2-large模型通过我们的API可用，模型名称为whisper-1。

目前，[Whisper](https://github.com/openai/whisper)的开源版本与我们的API版本之间没有区别。但是，通过我们的API，我们提供了一个经过优化的推理过程，使通过我们的API运行Whisper比其他方式更快。有关Whisper的更多技术细节，您可以阅读[相关论文](https://arxiv.org/abs/2212.04356)。
### Embeddings

嵌入是文本的数值表示，可以用来衡量两个文本之间的相关性。我们的第二代嵌入模型，text-embedding-ada-002，旨在以较小的成本取代之前的 16 个一代嵌入模型。嵌入对于搜索、聚类、推荐、异常检测和分类任务非常有用。您可以在[公告博客文章](https://openai.com/blog/new-and-improved-embedding-model)中了解有关我们最新嵌入模型的更多信息。

### Codex `Limited beta`

Codex 模型是我们 GPT-3 模型的后代，它们可以理解和生成代码。它们的训练数据包含自然语言和来自 GitHub 的数十亿行公共代码。[了解更多](https://help.openai.com/en/articles/5480054)。

他们在Python方面最有能力，并精通包括JavaScript、Go、Perl、PHP、Ruby、Swift、TypeScript、SQL甚至是Shell在内的十几种语言。

我们目前提供两种 Codex 模型：
| 最新模型 | 描述 | 最大请求 | 训练数据 |
| --- | --- | --- | --- |
| code-davinci-002 | 最有能力的Codex模型。在将自然语言转换为代码方面表现特别优秀。除了完成代码，还支持在代码 [内部插入完成代码](https://platform.openai.com/docs/guides/code/inserting-code)。 | 8,000 tokens | 截至2021年6月 |
| code-cushman-001 | 几乎与Davinci Codex同样强大，但速度稍快。这种速度优势可能使其更适合实时应用程序。 | 最多 2,048 tokens | - |

更多信息请参阅我们的 [Codex 工作指南](https://platform.openai.com/docs/guides/code)。

Codex 模型在有限的测试版期间是免费使用的，并受到降低的[速率限制](https://help.openai.com/en/articles/5955598-is-api-usage-subject-to-any-rate-limits)。随着我们对使用情况的了解，我们将考虑提供定价以支持广泛的应用程序。

在此期间，只要您的应用程序遵守我们的[使用政策](https://platform.openai.com/docs/usage-policies)，您就可以使用它。我们欢迎任何有关这些模型的反馈意见，同时期待与社区互动。

### 特定功能模型

主要的Codex模型是用于[文本补全端点](https://platform.openai.com/docs/guides/completion)的。我们还提供了一些模型，专门用于我们用于[创建嵌入](https://platform.openai.com/docs/guides/embeddings)和[编辑代码的端点](https://platform.openai.com/docs/guides/code/editing-code)。

## Moderation

Moderation 模型是为检查内容是否符合OpenAI[使用政策](https://platform.openai.com/docs/usage-policies/)而设计。该模型提供分类功能，可查找以下类别的内容：仇恨、仇恨/威胁、自我伤害、性、未成年人色情、暴力和暴力/图形。[了解更多信息](https://platform.openai.com/docs/guides/moderation/overview)。

| 模型 | 描述 |
| --- | --- |
| text-moderation-latest | 最具能力的审核模型。准确性将略高于稳定模型。 |
| text-moderation-stable | 几乎与最新模型一样有能力，但是稍微有点老旧。 |

## GPT-3
GPT-3模型能够理解和生成自然语言。这些模型被更强大的GPT-3.5一代模型取代。然而，原始的GPT-3基础模型（davinci，curie，ada和babbage）目前是唯一可以微调的模型。
| 最新模型 | 描述 | 最大请求 | 训练数据 |
| --- | --- | --- | --- |
| text-curie-001 | 该模型非常有能力，比 Davinci 更快、成本更低。 | 2,048 tokens | 截至2019年10月 |
| text-babbage-001 | 能够胜任简单的任务，速度非常快，成本较低。| 2,048 tokens | 截至2019年10月 |
| text-ada-001 | 能够完成简单任务，速度非常快，成本较低。 | 2,048 tokens | 截至2019年10月 |
| davinci | 最具能力的GPT-3模型。可以完成其他模型能完成的任何任务，并且通常具有更高的质量。 | 2,048 tokens | 截至2019年10月 |
| curie | 非常有能力，但速度比Davinci更快，成本更低。 | 2,048 tokens | 截至2019年10月 |
| babbage | 这个模型适用于简单的任务，运行非常快，成本较低。 | 2,048 tokens | 截至2019年10月 |
| ada | 能够完成非常简单的任务，通常是 GPT-3 系列中速度最快、价格最低的模型。 | 2,048 tokens | 截至2019年10月 |