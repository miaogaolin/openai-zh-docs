---
title: "快速入门"
---
OpenAI已经训练了最先进的语言模型，这些模型非常擅长理解和生成文本。我们的API提供对这些模型的访问，并可用于解决几乎涉及处理语言的任何任务。

在这个快速入门教程中，您将构建一个简单的示例应用程序。在此过程中，您将学习到对于使用API来完成任何任务都是基本的关键概念和技术，包括：

* 内容生成
* 摘要
* 分类、归类和情感分析
* 数据提取
* 翻译
* 还有很多其他的任务！
## 介绍
完成端点是我们API的核心，提供了一个简单而极其灵活和强大的接口。您将一些文本输入作为提示，API将返回一个文本完成，试图匹配您给出的任何指令或上下文。
```
提示：为一个冰淇淋店写一个标语

回应：我们每勺都送上微笑
```
您可以将其视为一个非常高级的自动完成功能 - 模型处理您的文本提示，并尝试预测最有可能出现的内容。
## 指令
想象一下，你想创建一个宠物名字生成器。从零开始想出名字是很难的！

首先，你需要一个明确表明你想要什么的提示语。让我们从一条指示开始。提交这个提示语以生成第一个完成文本。

> 官网可以直接修改提示语测试，如果想测试[前往](https://platform.openai.com/docs/quickstart/start-with-an-instruction)。

![](/start/images/1.png)

不错！现在，请尝试让您的指令更具体一些。

![](/start/images/2.png)

正如您所看到的，将一个简单的形容词添加到我们的提示中会改变生成的完成结果。设计提示本质上就是“编程”模型的方式。

## 例子
设计好的指令对于获得良好的结果非常重要，但有时这并不足够。让我们试着让您的指令更加复杂。


![](/start/images/3.png)

这个补全结果不太符合我们的要求。这些名字非常普通，而且似乎模型没有注意到我们指定的“马”的部分。让我们看看是否可以让它提供更相关的建议。

在许多情况下，展示和告诉模型你想要什么是很有帮助的。在你的提示中添加示例可以帮助传达模式或细微差别。尝试提交这个包含一些例子的提示。

" 如果该图片的实例不能够让你替换到差异，建议自己在[官网](https://platform.openai.com/docs/quickstart/add-some-examples)试试。
![](/start/images/4.png)

不错！通过添加一些输入和期望输出的例子，帮助模型提供了我们所需要的类型的名字。
## 调整设置

提示设计不是您可以使用的唯一工具。您还可以通过调整设置来控制补全。最重要的设置之一称为“温度”。

您可能已经注意到，如果您在上面的示例中多次提交相同的提示，模型将始终返回相同或非常相似的完成。这是因为您的温度设置为0。

尝试将相同的提示重新提交几次，并将温度设置为1。

![](/start/images/5.png)

看到发生了什么了吗？

> 图片中看不到效果，但可以看到有个 Temperature(温度) 参数设置

当温度高于0时，多次提交相同的提示会每次返回不同的完成结果。

请记住，模型预测哪些文本最有可能跟在前面的文本之后。温度是一个介于0和1之间的值，可以控制模型在进行这些预测时应该有多大的信心。降低温度意味着它会冒更少的风险，完成结果会更准确和确定性更强。增加温度会导致更多种类的完成结果。

> 下来进一步了解标记及其概念。

我们的模型通过将文本分解成称为标记的较小单元来处理文本。标记可以是单词、单词块或单个字符。编辑下面的文本以查看其如何被分词。

![](/start/images/6.png)

常见的单词如“cat”是一个单一的标记，而不常见的单词通常被分解成多个标记。例如，“Butterscotch”被翻译成四个标记：“But”，“ters”，“cot”和“ch”。许多标记以空格开头，例如“ hello”和“ bye”。

给定一些文本，模型会确定哪个单元最有可能出现在文本的下一个位置。例如，“Horses are my favorite”文本最可能紧随着“ animal”这个单元。

![](/start/images/7.png)

这就是温度（temperature）发挥作用的地方。如果你使用温度为0的设置，多次提交此提示，模型总会返回“animal”，因为它具有最高的概率。如果你增加温度，模型将更冒险，并考虑概率较低的标记。

![](/start/images/8.png)

通常情况下，对于输出明确定义的任务，最好设置较低的温度。如果需要多样性或创造力，则较高的温度可能会有所帮助，或者如果您想要生成几种变化以供最终用户或人类专家选择。

对于宠物名字生成器，您可能希望能够生成许多名称想法。适度的温度0.6应该可以很好地工作。
## 构建你的应用
>  以下涉及的代码使用 JS 展示，官网还有 Python，可[前往](https://platform.openai.com/docs/quickstart/build-your-application)。

现在，您已经找到了一个好的提示和设置，准备构建您的宠物名字生成器！我们已经编写了一些代码，让您开始。请按照以下说明下载代码并运行应用程序。

### 安装
如果你没有安装Node.js，请从这里[安装](https://nodejs.org/en/)。然后通过克隆此存储库下载代码。

```shell
git clone https://github.com/openai/openai-quickstart-node.git
```
如果您不想使用 git，您也可以使用此 [zip 文件](https://github.com/openai/openai-quickstart-node/archive/refs/heads/master.zip)下载代码。

### 添加 API 密钥

进入项目目录并复制示例环境变量文件。
```shell
cd openai-quickstart-node
cp .env.example .env
```
复制您的秘密API密钥并将其设置为您新创建的 .env 文件中的 OPENAI_API_KEY。如果您还没有创建秘密密钥，可以在下面进行创建。

如果没有 API 密钥，请[前往官网](https://platform.openai.com/docs/quickstart/build-your-application)创建一个，如图位置：

![](/start/images/9.png)

**重要提示：在使用Javascript时，所有API调用都应仅在服务器端进行，因为在客户端浏览器代码中进行调用将会暴露您的API密钥。有关更多详细信息，请[参见此处](https://platform.openai.com/docs/api-reference/authentication)。**

### 运行
运行以下命令在项目目录中安装依赖项并运行应用程序。
```
npm install
npm run dev
```

在浏览器中打开 [http://localhost:3000](http://localhost:3000)，您应该可以看到宠物名字生成器！

### 分析代码

打开 `openai-quickstart-node/pages/api` 文件夹中的 `generate.js` 文件。在底部，你会看到生成上述 prompt 的函数。由于用户将输入宠物的动物类型，因此它会动态替换指定动物部分的 prompt。
```js
function generatePrompt(animal) {
  const capitalizedAnimal = animal[0].toUpperCase() + animal.slice(1).toLowerCase();
  return `Suggest three names for an animal that is a superhero.

Animal: Cat
Names: Captain Sharpclaw, Agent Fluffball, The Incredible Feline
Animal: Dog
Names: Ruff the Protector, Wonder Canine, Sir Barks-a-Lot
Animal: ${capitalizedAnimal}
Names:`;
}
```
在 `generate.js` 文件的第 9 行，您会看到发送实际 API 请求的代码。如上所述，它使用了温度为 0.6 的 completions 端点。

```js
const completion = await openai.createCompletion({
  model: "text-davinci-003",
  prompt: generatePrompt(req.body.animal),
  temperature: 0.6,
});
```
完成了！你现在应该完全了解你的（超级英雄）宠物名字生成器是如何使用 OpenAI API 的了！
## 结束
这些概念和技术将有助于您构建自己的应用程序。尽管如此，这个简单的例子只展示了 OpenAI API 可能性的一小部分！完成端点足够灵活，可以解决几乎任何语言处理任务，包括内容生成、摘要、语义搜索、主题标记、情感分析等等。

需要记住的一个限制是，对于大多数模型，单个 API 请求只能在您的提示和完成之间处理最多 2,048 个令牌（大约 1,500 个单词）。

> ### 模型和价格
> 我们提供不同能力和价格点的模型。在本教程中，我们使用了text-davinci-003，这是我们最强大的自然语言模型。我们建议在进行实验时使用此模型，因为它将产生最佳结果。一旦您使事情正常运行，您可以看看其他模型是否可以以更低的延迟和成本产生相同的结果。
> 
> 单个请求中处理的令牌总数（包括提示和完成）不能超过模型的最大上下文长度。对于大多数模型，这是2048个标记或约1500个单词。作为一个粗略的经验法则，1个标记约为4个字符或0.75个英文单词。
> 
> 定价是按每1000个令牌的使用量计费，前3个月可以使用18美元的免费信用，[了解更多信息](https://openai.com/api/pricing/)。

对于更高级的任务，你可能会希望提供比单个提示中可以容纳的更多的示例或上下文。[微调API](https://platform.openai.com/docs/guides/fine-tuning)是处理这类更高级任务的绝佳选择。微调API允许你提供数百甚至数千个示例，以自定义模型以适应你的具体用例。

## 下一步

为了获取灵感并了解更多关于为不同任务设计提示的信息：

* 阅读我们的[完成指南](https://platform.openai.com/docs/guides/completion)。
* 探索我们的[示例提示库](https://platform.openai.com/examples)。
* 在 [Playground](https://platform.openai.com/playground) 中开始实验。
* 在开始构建时请记住我们的[使用政策](https://platform.openai.com/docs/usage-policies)。