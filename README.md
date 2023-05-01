# Paper
1. **Chain-of-Thought Prompting Elicits Reasoning in Large Language Models** [28 Jan 2022](https://doi.org/10.48550/arXiv.2201.11903)

	有关思维链的第一篇文章，在其中用了模型**PaLM 540B**，在**数学文字题**和**文字推理**的多个数据集上，通过对比使用standard few-shot prompting 和 作者人为构造chain of thought模板，发现了在数学推理方面，使用了CoT模板的模型有更好的推理能力。


2. **Self-Consistency Improves Chain of Thought Reasoning in Language Models** [21 Mar 2022]()

3. **Automatic Chain of thought Prompting in Large Language Models** [7 Oct 2022](https://doi.org/10.48550/arXiv.2210.03493)

   原理同文章1中的**Few-shot-CoT**, 区别在于文章1中使用了**人工构造**推理模板，用机器写作代替人工生成CoT模版。

   作者在构造模板中，发现如果对问题进行**Retrieval by Similarity**会导致模型对问题含义的混淆，例如“how long will it take him to cook the rest?”和“how long will it take him to cook the total?”会让模型无法准确理解**the reset**的含义，因此不能单纯的选取similarity高的问题进行回答。作者最后通过测试，得出了最终方法——将问题集划分为k个聚类，选取每个聚类中心具有代表性的问题(与人工构造的回答相似度高)，再将这k个问题通过LLM的**Zero-shot-CoT**形成k组回答问题的模板，将这k组问答输入到模型中，最后提出自己的问题，让模型think step by step。

   该方式取得的效果不仅节约人力，还能比单纯的人工设置回答模板取得更好的效果。


4. **Large Language Models are Zero-Shot Reasoners** [29 Jan 2023](https://doi.org/10.48550/arXiv.2205.11916)

   相比于文章1中提出的**Few-shot-CoT**，该文章直接使用了**Zero-shot-CoT**的方式。具体过程作者分为两个阶段：

   第一阶段直接在问题末尾拼接**let's think step by step**，让模型输出该问题的推理过程。
   第二阶段使用**Therefore,the answer is**，让模型输出答案。

   作者在测试过程中，发现模型能够有更好的解释能力，在测试集中的错误也大多是推理正确但无法从多个选择中选择最好的那一个。作者也比较了相较于Let's think step by step的其他prompt发现使用该prompt模型的准确性更高。


5. **Multimodal Chain-of-Thought Reasoning in Language Models** [17 Feb 2023](https://doi.org/10.48550/arXiv.2302.00923)

    多模态状态下cot该如何实现，本文模态仅涉及视觉和语言两个领域。
    在未加入vision feature前，作者得出了**文章1**中相似的结果，小于100B的NLP模型，在使用COT会出现混淆，进而导致正确率降低(约15%个点)
    加入vision feature的方法大致分为两种，一种是使用**Caption**另一种则是直接将**vision features**直接喂给模型，因为使用caption存在着信息丢失，所以效果自然是后者好。
    模型采取了**两步式**架构：
    1. 先将图片文本对输入模型生成Rationale

    2. 再将生成的Rationale和之前相同的图片文本对再次输入进模型，让模型生成推理过程进行回答

	这样的使得回答的正确率有显著的上升。

6. **MM-REACT: Prompting ChatGPT for Multimodal Reasoning and Action** 20 Mar 2023

6. 

 
