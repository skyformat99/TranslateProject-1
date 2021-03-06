我的Lisp体验和GNU Emacs的开发
（Richard Stallman的演讲稿，2002年10月28日，国际Lisp会议）。

由于我的常见演讲都没有与Lisp有任何关系，因此它们都不适用于今天。所以我将不得不放弃它。由于我在与Lisp相关的职业生涯中做了足够的事情，我应该能够说些有趣的事情。

我第一次使用Lisp是在高中时阅读Lisp 1.5手册。就在那时，我的想法是因为可能有类似的计算机语言。我第一次有机会和Lisp做任何事情的时候是我在哈佛大学的新生，我为PDP-11写了一个Lisp解释器。这是一个非常小的机器 - 它有类似8k的内存 - 我设法用一千个指令编写解释器。这为我提供了一些数据空间。那是在我看到真正的软件之前，它做了真正的系统工作。

一旦我开始在麻省理工学院工作，我开始与JonL White一起开展真正的Lisp实现工作。我在人工智能实验室雇用的不是JonL，而是来自Russ Noftsker，考虑到将要发生的事情，这是最具讽刺意味的 - 他当然一定非常后悔。

在20世纪70年代，在我的生活因可怕的事件而变得政治化之前，我只是为了各种程序而一个接一个地进行扩展，其中大多数与Lisp没有任何关系。但是，在此过程中，我写了一个文本编辑器，Emacs。关于Emacs的有趣想法是它有一种编程语言，用户的编辑命令将用这种解释的编程语言编写，这样你就可以在编辑时将新命令加载到编辑器中。您可以编辑正在使用的程序，然后继续编辑它们。所以，我们有一个对编程以外的东西有用的系统，但你可以在使用它的时候对它进行编程。我不知道它是否是第一个，但它肯定是第一个这样的编辑。

这种构建巨大而复杂的程序以便在您自己编辑中使用，然后与其他人交换这种精神的精神，激发了我们在AI实验室进行的自由合作的精神。我们的想法是，您可以将任何程序的副本提供给想要其副本的人。我们与想要使用它们的人共享程序，它们是人类的知识。因此，尽管没有有组织的政治思想与我们将软件与Emacs的设计共享的方式联系起来，但我确信它们之间存在联系，也许是一种无意识的联系。我认为这是我们在AI实验室生活的方式的本质，它导致了Emacs并使它成为现实。

最初的Emacs里面没有Lisp。较低级别的语言，非解释性语言 - 是PDP-10汇编程序。我们写的解释实际上并不是为Emacs编写的，它是为TECO编写的。这是我们的文本编辑器，并且是一种非常难看的编程语言，尽可能难看。原因是它不是一种编程语言，它被设计成一种编辑器和命令语言。有一些命令，如'5l'，意思是'移动五行'，或'i'然后是一个字符串，然后是一个ESC来插入该字符串。您将键入一个字符串，该字符串是一系列命令，称为命令字符串。你会用ESC ESC结束它，它会被执行。

好吧，人们想用编程工具扩展这种语言，所以他们添加了一些。例如，第一个是循环结构，它是<>。你会把它们放在周围，它会循环。还有其他神秘的命令可用于有条件地退出循环。为了制作Emacs，我们（1）添加了具有名称的子程序的工具。在此之前，它有点像Basic，子程序只能用单个字母作为名称。这很难用大型程序编程，因此我们添加了代码以便它们可以有更长的名称。实际上，有一些相当复杂的设施; 我认为Lisp得到了TECO的放松保护设施。

我们开始使用相当复杂的设施，所有这些都是你能想到的最丑陋的语法，并且它起作用了 - 人们无论如何都能够在其中编写大型程序。显而易见的教训是，像TECO这样的语言并没有被设计成编程语言，这是错误的方法。您构建扩展的语言不应该被认为是事后的编程语言; 它应该被设计为编程语言。实际上，我们发现用于此目的的最佳编程语言是Lisp。

是伯尼格林伯格，他发现它是（2）。他在Multics MacLisp中编写了一个版本的Emacs，并且他以直截了当的方式在MacLisp中编写了他的命令。编辑器本身完全是用Lisp编写的。事实证明，Multics Emacs取得了巨大成功 - 编写新的编辑命令非常方便，甚至他办公室的秘书也开始学习如何使用它。他们使用了某人编写的手册，其中展示了如何扩展Emacs，但并没有说这是一个编程。所以那些认为自己无法编程的秘书并没有被吓跑。他们阅读了手册，发现他们可以做有用的事情并且他们学会了编程。

因此，伯尼看到了一个应用程序 - 一个对你有用的程序 - 里面有Lisp，你可以通过重写Lisp程序来扩展它，实际上是人们学习编程的一种非常好的方式。它让他们有机会编写对他们有用的小程序，这在大多数领域是你不可能做到的。他们可以鼓励他们自己的实际用途 - 在最困难的阶段 - 他们不相信他们可以编程，直到他们达到程序员的程度。

那时，人们开始想知道如何在他们没有完整服务Lisp实现的平台上得到这样的东西。Multics MacLisp有一个编译器和一个解释器 - 它是一个成熟的Lisp系统 - 但是人们希望在其他尚未编写Lisp编译器的系统上实现类似的东西。好吧，如果你没有Lisp编译器，你就无法在Lisp中编写整个编辑器 - 如果它必须运行解释的Lisp，那就太慢了，尤其是重新编译。所以我们开发了一种混合技术。我的想法是编写一个Lisp解释器和编辑器的低级部分，以便编辑器的部分内置Lisp工具。这些将是我们认为必须优化的任何部分。这是我们已经在原始Emacs中有意识地实践的一种技术，因为我们在机器语言中重新实现了某些相当高级别的特性，使它们成为TECO原语。例如，有一个TECO原语来填充段落（实际上，要完成填充段落的大部分工作，因为一些耗时较少的部分工作将由TECO程序在更高级别完成） 。您可以通过编写TECO程序来完成整个工作，但这太慢了，所以我们通过将其中的一部分放在机器语言中来优化它。我们在这里使用了相同的想法（在混合技术中），大多数编辑器都是用Lisp编写的，但是必须以特别快的速度运行的某些部分才能在较低级别编写。因为我们在机器语言中重新实现了某些相当高级别的功能，使它们成为TECO原语。例如，有一个TECO原语来填充段落（实际上，要完成填充段落的大部分工作，因为一些耗时较少的部分工作将由TECO程序在更高级别完成） 。您可以通过编写TECO程序来完成整个工作，但这太慢了，所以我们通过将其中的一部分放在机器语言中来优化它。我们在这里使用了相同的想法（在混合技术中），大多数编辑器都是用Lisp编写的，但是必须以特别快的速度运行的某些部分才能在较低级别编写。因为我们在机器语言中重新实现了某些相当高级别的功能，使它们成为TECO原语。例如，有一个TECO原语来填充段落（实际上，要完成填充段落的大部分工作，因为一些耗时较少的部分工作将由TECO程序在更高级别完成） 。您可以通过编写TECO程序来完成整个工作，但这太慢了，所以我们通过将其中的一部分放在机器语言中来优化它。我们在这里使用了相同的想法（在混合技术中），大多数编辑器都是用Lisp编写的，但是必须以特别快的速度运行的某些部分才能在较低级别编写。完成填写段落的大部分工作，因为一些耗时较少的工作部分将由TECO计划在更高层次完成。您可以通过编写TECO程序来完成整个工作，但这太慢了，所以我们通过将其中的一部分放在机器语言中来优化它。我们在这里使用了相同的想法（在混合技术中），大多数编辑器都是用Lisp编写的，但是必须以特别快的速度运行的某些部分才能在较低级别编写。完成填写段落的大部分工作，因为一些耗时较少的工作部分将由TECO计划在更高层次完成。您可以通过编写TECO程序来完成整个工作，但这太慢了，所以我们通过将其中的一部分放在机器语言中来优化它。我们在这里使用了相同的想法（在混合技术中），大多数编辑器都是用Lisp编写的，但是必须以特别快的速度运行的某些部分才能在较低级别编写。

因此，当我编写第二个Emacs实现时，我遵循了同样的设计。低级语言不再是机器语言，它是C. C是便携式程序在类Unix操作系统中运行的一种好的，高效的语言。有一个Lisp解释器，但我直接在C中实现了专用编辑工作的工具 - 操作编辑缓冲区，插入前导文本，读取和写入文件，重新显示屏幕上的缓冲区，管理编辑器窗口。

现在，这不是第一个用C编写并在Unix上运行的Emacs。第一部由James Gosling撰写，被称为GosMacs。他身上发生了一件奇怪的事。起初，他似乎受到原始Emacs的共享和合作精神的影响。我首先向麻省理工学院的人们发布了最初的Emacs。有人希望将它移植到Twenex上运行 - 它最初只运行在我们在麻省理工学院使用的不兼容的分时系统。他们将它移植到Twenex，这意味着全世界有几百个可能会使用它的安装。我们开始将它分发给他们，其规则是“您必须将所有改进发回”，这样我们才能受益。没有人试图强制执行，但据我所知，人们确实合作。

起初，戈斯林似乎参与了这种精神。他在手册中写道，他称Emacs计划希望社区中的其他人能够改进它，直到它值得这个名字。这是采用社区的正确方法 - 要求他们加入并使计划更好。但在那之后，他似乎改变了精​​神，并把它卖给了一家公司。

那时我正在研究GNU系统（一种类似Unix的自由软件操作系统，许多人错误称之为“Linux”）。没有在Unix上运行的免费软件Emacs编辑器。然而，我确实有一位朋友曾参与开发Gosling的Emacs。戈斯林通过电子邮件允许他分发自己的版本。他向我建议我使用那个版本。然后我发现Gosling的Emacs没有真正的Lisp。它有一种被称为'mocklisp'的编程语言，它在语法上看起来像Lisp，但没有Lisp的数据结构。所以程序不是数据，而且缺少Lisp的重要元素。它的数据结构是字符串，数字和一些其他专门的东西。

我总结说我无法使用它并且必须全部替换它，第一步是编写一个实际的Lisp解释器。我逐渐调整了编辑器的每个部分，基于真正的Lisp数据结构，而不是ad hoc数据结构，使得编辑器内部的数据结构可以由用户的Lisp程序公开和操作。

唯一的例外是重新显示。很长一段时间，重新显示是一个替代世界。编辑器将进入重新显示的世界，并且会继续使用非常特殊的数据结构，这些数据结构对于垃圾收集是不安全的，不会安全中断，并且在此期间您无法运行任何Lisp程序。我们已经改变了 - 因为现在可以在重新显示期间运行Lisp代码。这是一件非常方便的事情。

第二个Emacs计划是现代意义上的“自由软件” - 它是使软件免费的明确政治运动的一部分。这次活动的实质是每个人都应该自由地做我们过去在麻省理工学院做的事情，共同开发软件并与想与我们合作的任何人一起工作。这是自由软件运动的基础 - 我拥有的经验，我在麻省理工学院人工智能实验室的生活 - 致力于人类知识，而不是阻碍任何人进一步使用和进一步传播人类知识。

当时，您可以制作一台与其他不适合Lisp的计算机价格相同的计算机，除了它可以比它们更快地运行Lisp，并且在每个操作中都进行全类型检查。普通计算机通常迫使您在执行速度和良好的类型检查之间做出选择。所以，是的，你可以拥有一个Lisp编译器并快速运行你的程序，但是当他们试图获取car一个数字时，它会得到无意义的结果并最终在某些时候崩溃。

Lisp机器能够以与其他机器一样快的速度执行指令，但是每条指令 - 汽车指令都会进行数据类型检查 - 所以当你试图在编译的程序中得到一个数字的汽车时，它会立即给你一个错误。我们构建了机器，并为它配备了Lisp操作系统。它几乎完全是用Lisp编写的，唯一的例外是在微码中编写的部分。人们开始对制造它们感兴趣，这意味着他们应该创办公司。

关于这家公司应该是什么样的，有两种不同的想法。格林布莱特希望开始他所谓的“黑客”公司。这意味着它将成为一家由黑客运营的公司，并以有利于黑客的方式运营。另一个目标是维持AI Lab文化（3）。不幸的是，Greenblatt没有任何商业经验，所以Lisp机器组的其他人说他们怀疑自己能否成功。他们认为他避免外来投资的计划是行不通的。

他为什么要避免外来投资？因为当一家公司有外部投资者时，他们会接受控制，他们不会让你有任何顾忌。最后，如果你有任何顾忌，他们也会取代你作为经理。

所以Greenblatt认为他会找到一个会提前支付购买零件的顾客。他们会建造机器并交付它们; 通过这些零件的利润，他们将能够为更多的机器购买零件，销售这些零件，然后为更多的机器购买零件，等等。小组中的其他人认为这不可行。

然后Greenblatt招募了聘请我的Russell Noftsker，后来他离开了AI Lab并创建了一家成功的公司。据信拉塞尔有商业天赋。他通过对群体中的其他人说：“让我们放弃格林布拉特，忘记他的想法，我们将成为另一家公司。”他展示了这种商业天赋。在后面刺伤，显然是一个真正的商人。那些人决定他们组建一家名为Symbolics的公司。他们会得到外部投资，没有顾忌，并尽一切可能获胜。

但格林布拉特没有放弃。无论如何，他和忠于他的少数人决定启动Lisp Machines Inc.并继续他们的计划。你知道什么，他们成功了！他们得到了第一个客户，并提前付款。他们建造机器并出售它们，并建造了更多的机器和更多的机器。尽管他们没有得到团队中大多数人的帮助，但他们确实取得了成功。Symbolics也取得了成功的开始，所以你有两个竞争的Lisp机器公司。当Symbolics看到LMI不会掉在脸上时，他们开始寻找破坏它的方法。

因此，放弃我们的实验室之后在我们的实验室中进行了“战争”。除了我和少数在LMI兼职工作的人之外，当Symbolics雇佣了所有的黑客时，遗弃了。然后他们引用了一条规则并且淘汰了为麻省理工学院做兼职工作的人，所以他们不得不完全离开，只剩下我。人工智能实验室现在无能为力。麻省理工学院与这两家公司做了非常愚蠢的安排。这是一份三方合同，两家公司都许可使用Lisp机器系统源。这些公司被要求让麻省理工学院使用他们的变化。但它没有在合同中说MIT有权将它们放入两家公司获得许可的MIT Lisp机器系统中。没有人设想AI实验室的黑客组织会被彻底消灭，但确实如此。

因此，Symbolics提出了一个计划（4）。他们对实验室说：“我们将继续对可供您使用的系统进行更改，但您无法将其置于MIT Lisp机器系统中。相反，我们将允许您访问Symbolics的Lisp机器系统，您可以运行它，但这就是您所能做的一切。“

实际上，这意味着他们要求我们必须选择一个侧面，并使用MIT版本的系统或Symbolics版本。无论我们做出哪种选择，都决定了我们改进的系统。如果我们研究并改进了Symbolics版本，我们就会单独支持Symbolics。如果我们使用并改进了MIT版本的系统，我们将为两家公司提供工作，但是Symbolics认为我们将支持LMI，因为我们将帮助它们继续存在。所以我们不再被允许保持中立。

直到那时，我还没有站在任何一家公司的一边，尽管让我很难看到我们的社区和软件发生了什么。但现在，Symbolics迫使这个问题。因此，为了帮助保持Lisp Machines Inc.（5） - 我开始复制Symbolics对Lisp机器系统所做的所有改进。我自己再次写了相同的改进（即代码是我自己的）。

过了一会儿（6），我得出结论，如果我甚至不看他们的代码那将是最好的。当他们发布了发布说明的beta版时，我会看到这些功能是什么然后实现它们。当他们真正发布时，我也做了。

通过这种方式，两年来，我阻止他们消灭Lisp Machines Incorporated，两家公司继续进行。但是，我不想花费数年和数年来惩罚某人，只是挫败了一个邪恶的行为。我认为他们受到了相当彻底的惩罚，因为他们被那些没有离开或将要消失的竞争所困扰（7）。与此同时，现在是时候开始建立一个新社区来取代他们的行动和其他人已经消灭的社区。

70年代的Lisp社区不仅限于麻省理工学院人工智能实验室，而且黑客并非都在麻省理工学院。Symbolics开始的战争是麻省理工学院的战争，但当时还有其他事件正在发生。有人放弃了合作，共同消灭了社区，没有多少人离开。

一旦我停止惩罚Symbolics，我必须弄清楚下一步该做什么。我必须制作一个免费的操作系统，这很清楚 - 人们可以一起工作和共享的唯一方法是使用免费的操作系统。

起初，我想过制作一个基于Lisp的系统，但我意识到这在技术上不是一个好主意。要拥有像Lisp机器系统这样的东西，你需要特殊用途的微码。这使得以其他计算机运行程序的速度运行程序成为可能，并且仍然可以获得类型检查的好处。没有它，你将被简化为类似其他机器的Lisp编译器。程序会更快，但不稳定。如果你在分时系统上运行一个程序就好了 - 如果一个程序崩溃，那不是灾难，这是你的程序偶尔会做的事情。但这并不能很好地编写操作系统，所以我拒绝了制作像Lisp机器这样的系统的想法。

我决定改造一个类似Unix的操作系统，让Lisp实现作为用户程序运行。内核不会用Lisp编写，但我们有Lisp。因此，操作系统GNU操作系统的开发使我编写了GNU Emacs。在这样做的过程中，我的目标是实现绝对最小化的Lisp实现。节目的规模是一个巨大的问题。

那些日子里，1985年有人拥有一台没有虚拟内存的1兆字节机器。他们希望能够使用GNU Emacs。这意味着我必须保持程序尽可能小。

例如，当时唯一的循环结构是'while'，这非常简单。没有办法打破'while'语句，你只需要执行catch和throw，或者测试运行循环的变量。这表明我在努力保持小事做多远。我们没有'caar'和'cadr'等等; “挤出一切可能”是从一开始就是Emacs Lisp精神的GNU Emacs的精神。

显然，机器现在变大了，我们不再这样做了。我们放入'caar'和'cadr'等等，我们可能会在其中一天进行另一个循环构造。我们现在愿意扩展它，但我们不想将它扩展到常见的Lisp级别。我在Lisp机器上实现了一次Common Lisp，我对此并不满意。我不太喜欢的一件事是关键字参数（8）。他们对我来说似乎不太好看; 我有时候会这样做，但是当我这样做时，我会尽量减少。

这不是与Lisp有关的GNU项目的结束。后来在1995年左右，我们开始考虑启动一个图形桌面项目。很明显，对于桌面上的程序，我们希望编程语言能够编写大量内容以使其易于扩展，就像编辑器一样。问题是应该是什么。

当时，为了这个目的，TCL正在被大力推动。我对TCL的看法很低，主要是因为它不是Lisp。它看起来有点像Lisp，但在语义上它不是，而且它不那么干净。然后有人向我展示了一则广告，其中Sun试图聘请某人在TCL工作，使其成为世界“事实上的标准扩展语言”。我想，“我们必须阻止这种情况发生。”因此我们开始将Scheme作为GNU的标准可扩展性语言。不是Common Lisp，因为它太大了。我们的想法是，我们将有一个Scheme解释器，设计为以与TCL链接到应用程序相同的方式链接到应用程序中。然后我们建议将其作为所有GNU程序的首选可扩展性包。

使用像Lisp这样强大的语言作为主要的可扩展性语言，可以获得一个有趣的好处。您可以通过将其翻译成主要语言来实现其他语言。如果您的主要语言是TCL，则无法通过将其翻译成TCL来轻松实现它。但是如果你的主要语言是Lisp，那么通过翻译来实现其他东西并不困难。我们的想法是，如果每个可扩展的应用程序都支持Scheme，您可以在Scheme中编写TCL或Python或Perl的实现，将该程序转换为Scheme。然后，您可以将其加载到任何应用程序中，并使用您喜欢的语言进行自定义，它也可以与其他自定义项一起使用。

只要可扩展性语言很弱，用户就必须只使用您提供的语言。这意味着喜欢任何特定语言的人必须竞争应用程序开发人员的选择 - 说“请，应用程序开发人员，将我的语言放入您的应用程序，而不是他的语言。”然后用户根本没有选择 - 无论哪个他们正在使用的应用程序带有一种语言，并且它们被[该语言]所困扰。但是，如果你有一种强大的语言可以通过翻译来实现其他语言，那么你就可以让用户选择语言了，我们不再需要语言大战了。这就是我们希望'Guile'，我们的计划翻译，会做的。我们去年夏天有一个人在完成从Python到Scheme的翻译工作。我不知道是不是' 已完全完成，但对于对此项目感兴趣的任何人，请与我们联系。这就是我们未来的计划。

我没有谈过自由软件，但让我简要地告诉你一些关于这意味着什么的信息。自由软件不涉及价格; 这并不意味着你是免费获得的。（您可能已经支付了一份副本，或者免费获得了一份副本。）这意味着您拥有作为用户的自由。关键是你可以自由运行程序，自由学习它的功能，可以随意改变它以满足你的需求，可以自由地重新发布其他人的副本并免费发布改进的扩展版本。这就是自由软件的含义。如果你使用非免费程序，你就失去了至关重要的自由，所以不要这样做。

GNU项目的目的是通过提供免费软件来取代它，使人们更容易拒绝自由践踏，用户主导，非自由软件。对于那些没有道德勇气拒绝非自由软件的人来说，当这意味着一些实际的不便时，我们试图做的是提供一个免费的替代方案，这样你就可以在没有混乱的情况下转向自由。实际上的牺牲。牺牲越少越好。我们希望让您更轻松地生活在自由，合作中。

这是合作自由的问题。我们习惯于思考自由和与社会的合作，好像他们是对立的。但在这里他们是在同一边。使用免费软件，您可以自由地与其他人合作，也可以自由地帮助自己。使用非自由软件，有人会主宰你并让人们分裂。你不能与他们分享，你不能自由地合作或帮助社会，而不是你可以自由地帮助自己。分裂和无助的是使用非自由软件的用户状态。

我们已经制作了大量的免费软件。我们做过人们说我们永远做不到的事情; 我们有两个免费软件操作系统。我们有很多应用程序，显然我们还有很长的路要走。所以我们需要你的帮助。我想请你自愿参加GNU项目; 帮助我们开发更多工作的免费软件。看看 http://www.gnu.org/help 找到如何提供帮助的建议。如果您想订购商品，可以在主页上找到相关链接。如果你想阅读哲学问题，请查看/哲学。如果您正在寻找可以使用的免费软件，请查看/directory，其中列出了大约1900个软件包（这是所有免费软件的一小部分）。请写更多信息并为我们做出贡献。我的论文“自由软件和自由社会”正在出售，可以在www.gnu.org上购买。快乐的黑客！

--------------------------------------------------------------------------------

via: https://www.gnu.org/gnu/rms-lisp.html

作者：[Richard Stallman][a]
选题：[lujun9972](https://github.com/lujun9972)
译者：[geekmar](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]:https://www.gnu.org
[1]:https://www.gnu.org/help/
[2]:http://www.gnu.org/
