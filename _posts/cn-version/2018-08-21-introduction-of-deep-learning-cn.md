---
title:  "【译】深度学习前言"
categories:
  - MachineLearning
tags: 
  - machine learning
  - deep learning
entries_layout: grid
author_profile: true
toc: true
toc_label: "深度学习前言"
toc_sticky: true
hidden: false
---

开始阅读Ian Goodfellow、Yoshua Bengio、Aaron Courville三位大佬写的[`deep learning book`][deep learning]，这次不能烂尾了，决定每天花3-4个小时阅读英文原版，再用周末的时间把看过的部分理解并翻译一下，争取12月份之前完成整本书。

考虑到整本书文本量巨大。不会全文翻译。

## 前言

一直以来科学家和发明家都在寻求能够思考的机器，从古希腊一直到近现代计算机的发明。而今天artificial intelligence (AI)正在蓬勃发展，在很多应用领域和研究中都比较活跃。

### 什么是深度学习

对于人工智能来说，它适合解决那些能被正式的数学规则所描述的问题，而对于人类来说能很简单的通过直觉来解决的问题对于计算机来说却很困难，所以，这本书旨在解决这类问题；而解决这类问题的方法便是让计算机试着从经验中学习并从概念的层次理解这个世界，`每一个概念又是其与简单概念的关系所定义的`，也就意味着，它不需要人类一次性指定把所有所需的知识，概念层次结构允许它可以从简单的概念来建立和学习一套复杂的概念。如果我们把这些概念用图来表示的话，我们会发现这个图很深，有很多的图层。正式因为这样，我们会把这种方式成为`AI深度学习`

### 什么时候我们使用AI

很多成功的AI案例都发生在相对贫瘠和正规的环境下，并不需要计算机对这个世界有太多的了解；像 IBM 的 Deep Blue chess-playing system 在1997年打败了世界冠军，而对于象棋来说，他是有规可循的，而且可以通过简洁而正式的规则完全描述，所以建立起这样一个AI系统，对于程序员来讲是很容易的。

>这也就是说，对于我们来说，那些抽象的正式的任务我们很难去理解，而对于计算机来说却很容易

AI可以很容易击败世界象棋选手，却在识别物体、语音这些人类很容易完成的事情上举步维艰。人类一天的生活需要大量关于这个世界的知识，而其中很大一部分是我们我们的主观意识和直接，很难用正式的方式来表达。计算机同样需要这些知识，人工智能的一大挑战也是如何将这些非正式的知识应用到计算机。

因为如此，这时诞生了一种称之为基于知识的人工智能方法，将需要的知识硬编码，这样，计算机可以使用逻辑推理规则自动推理这些正式语言中的语句，但这样做会很死板，比如一个著名的项目`Cyc`便因为小说中`FredWhileShaving`而将小说人物Fred错认为电气而不是人。解决这个问题就需要AI系统自己通过原始数据去获取他们想要的知识，这种能力我们往往称之为`机器学习`。很多时候机器学习的算法很依赖我们给出的数据。如果我们给出的数据是有序正式的，算法速度往往能有指数级别的提升。

许多人工智能任务可以通过设计合适的模型来提取任务，然后将这些特性提供给一个简单的机器学习算法来解决，但很多时候我们其实很难知道到底使用哪一种特征值，这又回到前面了，我们主观或直觉上觉得很好去理解的事物，往往不适合作为特征值传给计算机。解决这个问题的一个方法是使用机器学习来发现从表示到输出的映射，以及表示本身。这种方法被称为`representation learning`。学习过的表示往往能够比手动设计的表示有更好的性能。它们还使人工智能系统能够快速适应新的任务，而无需人工干预。

当我们设计特征或学习特征的算法时，我们的目标常常是为了分离能够解释观察数据的`差别因子`；差别因子通常不是乘法组合的。这些因子通常不是能直接观察到的量，相反，它们可能是现实世界中观察不到的物体或者不可观测的力，但会影响可观测的量。他们还可能以概念的形式存在与人类的思考中，为观察数据提供有用的简化信息或推测原因。他们可以是被理解为让我们了解丰富多才的数据的一些概念或抽象。

### 为什么使用深度学习

现实生活中，人工智能的一大难点就是很多差别因子的同时影响我们能观察到的每一个数据。例如一张图片里红色的汽车的单点像素在黑夜里会和黑色很相近等等。许多应用需要我们清理差别因子并忽略我们所不关心的。当然，从原始的数据中提取出如此高层次、抽象的特征是非常难的，许多诸如说话口音这样的差别因子，只能通过对数据进行复杂的、接近人类水平的理解来辨识。当这几乎与获得原问题的表示一样困难是，乍一看，表示学习似乎并不能帮助我们。

这时候，**深度学习**通过其他较简单的表示来表达复杂表示，解决了表示学习的中心问题。深度学习让计算机通过简单的概念来建立复杂的概念。下图展示了一个深度学习系统如何通过组合更简单的概念来表示一个人的图像的概念，比如角和轮廓，这些概念反过来又用边来定义。深度学习模型的典型例子是前馈深度网络或多层感知机。 多层感知机仅仅是一个将一组输入值映射到输出值的数学函数。 该函数由许多较简单的函数复合而成。 我们可以认为不同数学函数的每一次应用都为输入提供了新的表示。

![1.2][1.2]上图深度学习模型的说明：计算机很难理解原始感官输入数据的含义，比如这张以像素值集合表示的图像。从一组像素到对象标识的函数映射非常复杂。如果直接处理，学习或评估这种映射几乎是不可能的。深度学习通过将所需的复杂映射分解为一系列嵌套的简单映射(每个映射由模型的不同层描述)来解决这一难题。输入显示在可见层，之所以这样命名是因为它包含我们能够观察到的变量。然后一系列隐藏的图层从图像中抽取越来越多的抽象特征。这些层被称为“隐藏”层，因为数据中没有提供它们的值;相反，模型必须确定哪些概念对解释观测数据中的关系有用。这里的图像是每个隐藏单元所代表的特征的可视化。给定像素，通过比较相邻像素的亮度，第一层可以很容易地识别边缘。给定第一个隐藏层对边缘的描述，第二个隐藏层可以很容易地搜索角和轮廓，这些都可以被识别为边缘集合。根据第二个隐藏层对图像的角和轮廓的描述，第三个隐藏层可以通过寻找特定的轮廓和角集合来检测特定对象的整个部分。最后，根据图像所包含的对象部分对图像的描述可用于识别图像中出现的对象（this description of the image in terms of the object parts it contains canbe used to recognize the objects present in the image）。转载自Zeiler和Fergus(2014)

深度大的网络可以按顺序执行更多的指令。顺序指令提供了强大的功能，因为后面的指令可以参考早期指令的结果。从这个角度看，并不是一个层的激活激活函数中的所有信息都必须编码解释输入的差别因子。表示还存储状态信息，来帮助程序理解输入。这种状态信息可以类似于传统计算机程序中的计数器或指针。它与输入的具体内容无关，但它帮助模型组织其处理过程。

## 深度学习历史趋势

通过历史背景了解深度学习是最简单的方法。与其提供详细的历史，这里仅仅提及深度学习的关键时期（长话短说）

- 深度学习有着深远而悠久的历史，不同哲学流派，他也有很过很多的名字，并且在流行程度方面也随之跌宕起伏。
- 随着训练量的不断增加，深度学习也变得更加有用
- 随着针对深度学习的计算机基础设施（软件和硬件）条件不断改善，深度学习模型的规模也在不断增大
- 深度学习解决的问题越来越多，精度也越来越高

### 神经网络的众多命名和多舛命运

![1.7][1.7]根据Google图书中短语”控制论”、”联结主义”或”神经网络”频率衡量的人工神经网络研究的历史浪潮（图中展示了三次浪潮的前两次，第三次最近才出现）

第一次浪潮开始于20世纪40年代到20世纪60年代的控制论，随着生物学习理论的发展(McCulloch and Pitts, 1943; Hebb, 1949)和第一个模型的实现，像感知机 (Rosenblatt, 1958) ，能实现单个神经元的训练。
第二次浪潮开始于1980-1995年间的联结主义方法，可以使用反向传播(Rumelhart et al., 1986a)训练具有一到两个隐藏层的神经网络。
当前第三次浪潮，也就是深度学习，大约始于2006年(Hinton et al.,2006; Bengio et al., 2007; Ranzato et al., 2007a)，并且现在在2016年以书的形式出现。

每一次浪潮带来的都可以说是一次革命，代表着科学家们对于可以思考的机器的一个不断的探索过程，每一个细节不再赘述，只需要知道它以深度学习的名义回归大众的视野，强调研究者现在有能力训练以前不可能训练的比较深的神经网络，并着力于深度的理论重要性上。此时，深度神经网络已经优于与之竞争的基于其他机器学习技术以及手工设计功能的AI系统。今天，神经网络的第三次发展浪潮仍在继续，尽管深度学习的研究重点在这一段时间内发生了巨大变化，深度学习已开始着眼于新的无监督学习技术和深度模型在小数据集的泛化能力，但目前更多的兴趣点仍是比较传统的监督学习算法和深度模型充分利用大型标注数据集的能力。**深度学习并没有突破理论而颠覆今天的人工智能世界，传统的机器学习方法仍然是主流；我们不应悲天悯人，报以读书无用论，拥抱新技术永远是主流**。

### 日益增长的数据

为什么深度学习今天才被认为是一项关键的技术，尽管人类的第一次神经网络实验早在20世纪50年代便进行了？自上世纪90年代以来，深度学习已成功应用于商业应用，但人们通常认为，深度学习更多的是一门艺术，而非技术，直到最近，只有专家才能使用。从深度学习算法中获得好的性能确实需要一些技巧。幸运的是，所需技能的数量随着训练数据的增加而减少，今天的学习算法已经能达到很好的效果，最重要的新进展是现在我们有了这些算法得以成功训练所需的资源。下图展示了基准数据集的大小如何随着时间的推移而显著增加。这种趋势是由社会日益数字化驱动的。由于我们的活动越来越多发生在计算机上，我们做什么也越来越多地被记录。由于我们的计算机越来越多地联网在一起，这些记录变得更容易集中管理，并更容易将它们整理成适于机器学习应用的数据集。因为统计估计的主要负担（观察少量数据以在新数据上泛化）已经减轻，”大数据”时代使机器学习更加容易。截至2016年，一个粗略的经验法则是，监督深度学习算法在每类给定约5000个标注样本情况下一般将达到可以接受的性能，当至少有1000万个标注样本的数据集用于训练时，它将达到或超过人类表现。此外，在更小的数据集上获得成功是一个重要的研究领域，为此我们应特别侧重于如何通过无监督或半监督学习充分利用大量的未标注样本。

![1.8][1.8]

随时间增加数据集大小。在20世纪初，统计学家们使用成百上千的手工编制的测量数据来研究数据集(Garson, 1900;Gosset, 1908; Anderson, 1935; Fisher, 1936)。在20世纪50年代到80年代，受生物启发的机器学习的先驱们经常使用小型的合成数据集，比如低分辨率的字母位图，这些数据集的设计目的是为了降低计算成本，并证明神经网络能够学习特定类型的功能(Widrowand and Hoff, 1960;Rumelhart et al ., 1986 b)。在20世纪80年代和90年代，机器学习变得更加统计化，并开始利用包含数万个示例的更大数据集，例如MNIST手写数字扫描数据集(LeCun et al., 1998b)(如下图所示)。在21世纪头十年，更复杂的同样大小的数据集，如CIFAR-10数据集(Krizhevsky and Hinton, 2009)继续生产。在那十年的末期和2010年代的前半个月，包含数十万到数千万例子的巨大数据集彻底改变了深度学习的可能性。这些数据包括公共街景房屋号数据集(Netzer et al., 2011)，ImageNet数据集的各种版本(Deng et al., 2009, 2010;Russakovsky et al.， 2014a)和Sports-1M数据集(Karpathy et al., 2014)。在图的顶部，我们可以看到翻译句子的数据集，例如IBM的数据集，它是由CanadianHansard (Brown et al.， 1990)和WMT 2014英语到法语数据集(Schwenk,2014)构建的，通常远远领先于其他数据集的大小。

![1.9][1.9]
来自MNIST数据集的示例输入。NIST代表国家标准与技术研究所，最初收集这些数据的机构。“M”代表“modified”，因为为了便于机器学习算法的使用，数据经过了预处理。MNIST数据集包括扫描手写数字和相关标签描述哪个数字0-9包含在每个图像。这个简单的分类问题是深度学习研究中最简单、应用最广泛的测试之一。尽管现代技术很容易解决，但它仍然很流行。Geoffrey Hinton将其描述为“机器学习中的果蝇”，意思是它使机器学习研究者能够在受控的实验室条件下研究他们的算法，就像生物学家经常研究果蝇一样。

### 日益增长的模型数

20世纪80年代，神经网络只能取得相对较小的成功，而现在神经网络非常成功的另一个重要原因是我们现在拥有的计算资源可以运行更大的模型。连接注意的一个主要观点是当很多神经元一起工作的时候，动物会变的更聪明。

生物的神经元并不是特别稠密的连接在一起，从下图可以看到二十年来，机器学习的模型中每个神经元的连接数量已经和哺乳动物在一个数量级上了

就神经元的总数而言，神经网络直到最近才惊人地小。随着时间的推移，增加神经网络的大小。自引入隐藏单元以来，人工神经网络的规模大约每2.4年翻一番。这种增长是由更快、内存更大的计算机和更大数据集的可用性所驱动的。更大的网络能够在更复杂的任务中获得更高的精度。这种趋势似乎将持续数十年。除非新技术能更快地扩大规模，否则人工神经网络的神经元数量至少要到2050年才能达到与人类大脑相同的水平。生物神经元可能比目前的人工神经元表现出更复杂的功能，因此生物神经网络可能比这个情节描绘的还要大。

回过头来看，拥有比水蛭更少的神经元的神经网络无法解决复杂的人工智能问题，这并不奇怪。即使是今天的网络条件下，从计算系统的角度来看，我们认为相当大的神经网络，也比相对原始的脊椎动物如青蛙要小。

同时很大一方面，更快和更通用的CPU、更快的网络链接和更好的分布式计算的软件基础设施也是深度学习历史中重要的趋势之一。这个趋势也将在未来一直持续。

### 高精度、复杂度和对现实世界的冲击

最早的深度模型被用来识别裁剪紧凑且非常小的图像中的单个对象。到现在，神经网络可以处理的图像尺寸逐渐增加。现代对象识别网络能处理丰富的高分辨率照片，并且不需要在被识别的对象附近进行裁剪。类似地，最早的网络只能识别两种对象（或在某些情况下，单类对象的存在与否），而这些现代网络通常能够识别至少1000个不同类别的对象。对象识别中最大的比赛是每年举行的ImageNet大型视觉识别挑战（ILSVRC）。 深度学习迅速崛起的激动人心的一幕是卷积网络第一次大幅赢得这一挑战，它将最高水准的前5错误率从$$26.1%$$降到$$15.3%$$，这意味着该卷积网络针对每个图像的可能类别生成一个顺序列表，除了$$15.3%$$的测试样本，其他测试样本的正确类标都出现在此列表中的前5项里。此后，深度卷积网络连续地赢得这些比赛，截至写本书时，深度学习的最新结果将这个比赛中的前5错误率降到了$$3.6%$$。深度学习在语音识别、行人检测和图像剪裁等领域取得了瞩目的成果。

在深度网络的规模和精度有所提高的同时，它们可以解决的任务也日益复杂。神经网络可以学习转录图像的整个字符序列，而不是仅仅识别单个对象。此前，人们普遍认为，这种学习需要对序列中的单个元素进行标注。循环神经网络，如之前提到的 **LSTM**序列模型，现在用于对*序列*和其他*序列*之间的关系进行建模，而不是仅仅固定输入关系。这种序列到序列的学习似乎引领着另一个应用的颠覆性发展，即机器翻译（牛逼）。

随着神经图灵机的引入，这种复杂性增加的趋势被推到了逻辑结论，神经图灵机学会从内存单元读取内容，并将任意内容写入内存单元。这样的神经网络可以从期望行为的例子中学习简单的程序。这种自编程技术尚处于起步阶段，但在未来，它原则上可以应用于几乎任何任务。

深度学习的另一个最大的成就是其在 **强化学习**领域的扩展。在强化学习的环境中，自主智体必须通过反复试验和试错来学习执行任务，而不需要人工操作者的任何指导。DeepMind 证明了基于深度学习的强化学习系统能够学习玩雅达利电子游戏，在很多任务上都能达到真正的人机水平。深度学习也显著提高了机器人强化学习的性能。

许多深度学习应用都是高利润的。现在深度学习被许多顶级的技术公司包括Google、Microsoft、Facebook、IBM、Baidu、Apple、Adobe、Netflix、NVIDIA和NEC等使用。

深度学习的进步也严重依赖于软件基础架构的进展。软件库如Theano (Bergstra et al., 2010; Bastienet al., 2012), PyLearn2 (Goodfellow et al., 2013c), Torch (Collobert et al., 2011b),DistBelief (Dean et al., 2012), Caﬀe (Jia, 2013), MXNet (Chen et al., 2015), andTensorFlow (Abadi et al., 2015)都能支持重要的研究项目或商业产品。

深度学习也为其他科学做出了贡献。用于对象识别的现代卷积网络为神经科学家们提供了可以研究的视觉处理模型。 深度学习也为处理海量数据以及在科学领域作出有效的预测提供了非常有用的工具。它已成功地用于预测分子如何相互作用从而帮助制药公司设计新的药物，搜索亚原子粒子，以及自动解析用于构建人脑三维图的显微镜图像等。我们期待深度学习未来能够出现在越来越多的科学领域中。

总之，深度学习是机器学习的一种方法。在过去几十年的发展中，它大量借鉴了我们关于人脑、统计学和应用数学的知识。近年来，得益于更强大的计算机、更大的数据集和能够训练更深网络的技术，深度学习的普及性和实用性都有了极大的发展。未来几年充满了进一步提高深度学习并将它带到新领域的挑战和机遇。

## 总结

深度学习作为一门`历史悠久又年轻`的技术，伴随第三次浪潮的来临，今天，在包括计算机、生物、社会科学等领域都有着极大的影响力；首先作为一门悠久的科学，前人为我们总结了很多理论和概念，同时也为我们提供了很多错误参照，然后作为一门年轻的科学，当当年的神经网络以`深度学习`的名义卷土重来的时候，随着设备性能的提升，数据集的增大，深度学习的发展之路似乎也越来越顺利...

[deep learning]: https://www.deeplearningbook.org/
[1.2]: /assets/images/2018-08-21-introduction-of-deep-learning/1.2.png
[1.7]: /assets/images/2018-08-21-introduction-of-deep-learning/1.7.png
[1.8]: /assets/images/2018-08-21-introduction-of-deep-learning/1.8.png
[1.9]: /assets/images/2018-08-21-introduction-of-deep-learning/1.9.png
[1.10]: /assets/images/2018-08-21-introduction-of-deep-learning/1.10.png