<div class="Box-sc-g0xbh4-0 bJMeLZ js-snippet-clipboard-copy-unpositioned" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">minbpe</font></font></h1><a id="user-content-minbpe" class="anchor-element" aria-label="永久链接： minbpe" href="#minbpe"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">LLM 标记化中常用的（字节级）字节对编码 (BPE) 算法的最小、干净的代码。</font><font style="vertical-align: inherit;">BPE 算法是“字节级”的，因为它在 UTF-8 编码的字符串上运行。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"></font><a href="https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该算法通过GPT-2 论文</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">和 OpenAI 发布的相关 GPT-2</font></font><a href="https://github.com/openai/gpt-2"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">代码</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在法学硕士中得到推广</font><font style="vertical-align: inherit;">。</font></font><a href="https://arxiv.org/abs/1508.07909" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">森里奇等人。</font><font style="vertical-align: inherit;">2015 年</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">被引用为 BPE 在 NLP 应用中使用的原始参考文献。</font><font style="vertical-align: inherit;">如今，所有现代法学硕士（例如 GPT、Llama、Mistral）都使用此算法来训练他们的标记器。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">该存储库中有两个 Tokenizer，它们都可以执行 Tokenizer 的 3 个主要功能：1）训练 tokenizer 词汇并合并给定文本，2）从文本编码到令牌，3）从令牌解码到文本。</font><font style="vertical-align: inherit;">存储库的文件如下：</font></font></p>
<ol dir="auto">
<li><a href="/karpathy/minbpe/blob/master/minbpe/base.py"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">minbpe/base.py</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：实现该类</font></font><code>Tokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，该类是基类。</font><font style="vertical-align: inherit;">它包含</font></font><code>train</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、</font></font><code>encode</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">、 和</font></font><code>decode</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">存根、保存/加载功能，还有一些常见的实用功能。</font><font style="vertical-align: inherit;">这个类不应该直接使用，而是要继承。</font></font></li>
<li><a href="/karpathy/minbpe/blob/master/minbpe/basic.py"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">minbpe/basic.py</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：实现</font></font><code>BasicTokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">直接在文本上运行的 BPE 算法的最简单实现。</font></font></li>
<li><a href="/karpathy/minbpe/blob/master/minbpe/regex.py"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">minbpe/regex.py</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：实现</font></font><code>RegexTokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">通过正则表达式模式进一步分割输入文本，这是一个预处理阶段，在标记化之前按类别（例如：字母、数字、标点符号）分割输入文本。</font><font style="vertical-align: inherit;">这确保不会发生跨类别边界的合并。</font><font style="vertical-align: inherit;">这是在 GPT-2 论文中引入的，并从 GPT-4 开始继续使用。</font><font style="vertical-align: inherit;">此类还处理特殊标记（如果有）。</font></font></li>
<li><a href="/karpathy/minbpe/blob/master/minbpe/gpt4.py"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">minbpe/gpt4.py</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">：实现</font></font><code>GPT4Tokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">. </font><font style="vertical-align: inherit;">该类是（上面的 2）的一个轻量级包装器，它精确地再现了</font><a href="https://github.com/openai/tiktoken"><font style="vertical-align: inherit;">tiktoken</font></a></font><code>RegexTokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">库中 GPT-4 的标记化</font><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">包装处理有关恢复标记生成器中的精确合并的一些细节，以及处理一些不幸的（并且可能是历史的？）1 字节标记排列。</font></font><a href="https://github.com/openai/tiktoken"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></li>
</ol>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">最后，脚本</font></font><a href="/karpathy/minbpe/blob/master/train.py"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">train.py</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在输入文本</font></font><a href="/karpathy/minbpe/blob/master/tests/taylorswift.txt"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">tests/taylorswift.txt</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（这是她的 kek 的维基百科条目）上训练两个主要分词器，并将词汇保存到磁盘以进行可视化。</font><font style="vertical-align: inherit;">该脚本在我的 (M1) MacBook 上运行大约需要 25 秒。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">上面的所有文件都非常短且注释详尽，并且在文件底部还包含使用示例。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">快速开始</font></font></h2><a id="user-content-quick-start" class="anchor-element" aria-label="永久链接：快速启动" href="#quick-start"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">作为最简单的例子，我们可以复制</font></font><a href="https://en.wikipedia.org/wiki/Byte_pair_encoding" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">维基百科关于 BPE 的文章</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如下：</font></font></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-k">from</span> <span class="pl-s1">minbpe</span> <span class="pl-k">import</span> <span class="pl-v">BasicTokenizer</span>
<span class="pl-s1">tokenizer</span> <span class="pl-c1">=</span> <span class="pl-v">BasicTokenizer</span>()
<span class="pl-s1">text</span> <span class="pl-c1">=</span> <span class="pl-s">"aaabdaaabac"</span>
<span class="pl-s1">tokenizer</span>.<span class="pl-en">train</span>(<span class="pl-s1">text</span>, <span class="pl-c1">256</span> <span class="pl-c1">+</span> <span class="pl-c1">3</span>) <span class="pl-c"># 256 are the byte tokens, then do 3 merges</span>
<span class="pl-en">print</span>(<span class="pl-s1">tokenizer</span>.<span class="pl-en">encode</span>(<span class="pl-s1">text</span>))
<span class="pl-c"># [258, 100, 258, 97, 99]</span>
<span class="pl-en">print</span>(<span class="pl-s1">tokenizer</span>.<span class="pl-en">decode</span>([<span class="pl-c1">258</span>, <span class="pl-c1">100</span>, <span class="pl-c1">258</span>, <span class="pl-c1">97</span>, <span class="pl-c1">99</span>]))
<span class="pl-c"># aaabdaaabac</span>
<span class="pl-s1">tokenizer</span>.<span class="pl-en">save</span>(<span class="pl-s">"toy"</span>)
<span class="pl-c"># writes two files: toy.model (for loading) and toy.vocab (for viewing)</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="from minbpe import BasicTokenizer
tokenizer = BasicTokenizer()
text = &quot;aaabdaaabac&quot;
tokenizer.train(text, 256 + 3) # 256 are the byte tokens, then do 3 merges
print(tokenizer.encode(text))
# [258, 100, 258, 97, 99]
print(tokenizer.decode([258, 100, 258, 97, 99]))
# aaabdaaabac
tokenizer.save(&quot;toy&quot;)
# writes two files: toy.model (for loading) and toy.vocab (for viewing)" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">根据 Wikipedia，对输入字符串“aaabdaaabac”运行 bpe 进行 3 次合并会生成字符串：“XdXac”，其中 X=ZY、Y=ab 和 Z=aa。</font><font style="vertical-align: inherit;">需要注意的棘手之处在于，minbpe 始终将 256 个单独字节分配为令牌，然后根据需要合并字节。</font><font style="vertical-align: inherit;">所以对于我们来说 a=97、b=98、c=99、d=100（它们的</font></font><a href="https://www.asciitable.com" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">ASCII</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">值）。</font><font style="vertical-align: inherit;">然后，当 (a,a) 合并到 Z 时，Z 将变为 256。同样，Y 将变为 257，X 变为 258。因此，我们从 256 字节开始，进行 3 次合并以获得上面的结果，预期输出为[258、100、258、97、99]。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">推论：GPT-4比较</font></font></h2><a id="user-content-inference-gpt-4-comparison" class="anchor-element" aria-label="永久链接：推理：GPT-4 比较" href="#inference-gpt-4-comparison"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们可以验证它与</font><a href="https://github.com/openai/tiktoken"><font style="vertical-align: inherit;">tiktoken</font></a></font><code>RegexTokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">的 GPT-4 分词器具有相同的功能，</font><font style="vertical-align: inherit;">如下所示：</font></font><a href="https://github.com/openai/tiktoken"><font style="vertical-align: inherit;"></font></a><font style="vertical-align: inherit;"></font></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-s1">text</span> <span class="pl-c1">=</span> <span class="pl-s">"hello123!!!? (안녕하세요!) 😉"</span>

<span class="pl-c"># tiktoken</span>
<span class="pl-k">import</span> <span class="pl-s1">tiktoken</span>
<span class="pl-s1">enc</span> <span class="pl-c1">=</span> <span class="pl-s1">tiktoken</span>.<span class="pl-en">get_encoding</span>(<span class="pl-s">"cl100k_base"</span>)
<span class="pl-en">print</span>(<span class="pl-s1">enc</span>.<span class="pl-en">encode</span>(<span class="pl-s1">text</span>))
<span class="pl-c"># [15339, 4513, 12340, 30, 320, 31495, 230, 75265, 243, 92245, 16715, 57037]</span>

<span class="pl-c"># ours</span>
<span class="pl-k">from</span> <span class="pl-s1">minbpe</span> <span class="pl-k">import</span> <span class="pl-v">GPT4Tokenizer</span>
<span class="pl-s1">tokenizer</span> <span class="pl-c1">=</span> <span class="pl-v">GPT4Tokenizer</span>()
<span class="pl-en">print</span>(<span class="pl-s1">tokenizer</span>.<span class="pl-en">encode</span>(<span class="pl-s1">text</span>))
<span class="pl-c"># [15339, 4513, 12340, 30, 320, 31495, 230, 75265, 243, 92245, 16715, 57037]</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="text = &quot;hello123!!!? (안녕하세요!) 😉&quot;

# tiktoken
import tiktoken
enc = tiktoken.get_encoding(&quot;cl100k_base&quot;)
print(enc.encode(text))
# [15339, 4513, 12340, 30, 320, 31495, 230, 75265, 243, 92245, 16715, 57037]

# ours
from minbpe import GPT4Tokenizer
tokenizer = GPT4Tokenizer()
print(tokenizer.encode(text))
# [15339, 4513, 12340, 30, 320, 31495, 230, 75265, 243, 92245, 16715, 57037]" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">（你必须</font></font><code>pip install tiktoken</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">跑）。</font><font style="vertical-align: inherit;">在底层，它</font></font><code>GPT4Tokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">只是一个轻量级的包装器</font></font><code>RegexTokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，传递 GPT-4 的合并和特殊标记。</font><font style="vertical-align: inherit;">我们还可以确保特殊令牌得到正确处理：</font></font></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-s1">text</span> <span class="pl-c1">=</span> <span class="pl-s">"&lt;|endoftext|&gt;hello world"</span>

<span class="pl-c"># tiktoken</span>
<span class="pl-k">import</span> <span class="pl-s1">tiktoken</span>
<span class="pl-s1">enc</span> <span class="pl-c1">=</span> <span class="pl-s1">tiktoken</span>.<span class="pl-en">get_encoding</span>(<span class="pl-s">"cl100k_base"</span>)
<span class="pl-en">print</span>(<span class="pl-s1">enc</span>.<span class="pl-en">encode</span>(<span class="pl-s1">text</span>, <span class="pl-s1">allowed_special</span><span class="pl-c1">=</span><span class="pl-s">"all"</span>))
<span class="pl-c"># [100257, 15339, 1917]</span>

<span class="pl-c"># ours</span>
<span class="pl-k">from</span> <span class="pl-s1">minbpe</span> <span class="pl-k">import</span> <span class="pl-v">GPT4Tokenizer</span>
<span class="pl-s1">tokenizer</span> <span class="pl-c1">=</span> <span class="pl-v">GPT4Tokenizer</span>()
<span class="pl-en">print</span>(<span class="pl-s1">tokenizer</span>.<span class="pl-en">encode</span>(<span class="pl-s1">text</span>, <span class="pl-s1">allowed_special</span><span class="pl-c1">=</span><span class="pl-s">"all"</span>))
<span class="pl-c"># [100257, 15339, 1917]</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="text = &quot;<|endoftext|>hello world&quot;

# tiktoken
import tiktoken
enc = tiktoken.get_encoding(&quot;cl100k_base&quot;)
print(enc.encode(text, allowed_special=&quot;all&quot;))
# [100257, 15339, 1917]

# ours
from minbpe import GPT4Tokenizer
tokenizer = GPT4Tokenizer()
print(tokenizer.encode(text, allowed_special=&quot;all&quot;))
# [100257, 15339, 1917]" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">请注意，就像 tiktoken 一样，我们必须在编码调用中显式声明使用和解析特殊令牌的意图。</font><font style="vertical-align: inherit;">否则，这可能会成为一个主要的枪口，无意中用特殊令牌标记攻击者控制的数据（例如用户提示）。</font><font style="vertical-align: inherit;">该</font></font><code>allowed_special</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">参数可以设置为“all”、“none”或允许的特殊标记列表。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">训练</font></font></h2><a id="user-content-training" class="anchor-element" aria-label="永久链接： 培训" href="#training"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">与 tiktoken 不同，此代码允许您训练自己的标记器。</font><font style="vertical-align: inherit;">原则上，据我所知，如果您</font></font><code>RegexTokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">在词汇量为 100K 的大型数据集上进行训练，您将重现 GPT-4 分词器。</font></font></p>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您可以遵循两条路径。</font><font style="vertical-align: inherit;">首先，您可以决定不希望使用正则表达式模式分割和预处理文本的复杂性，并且您也不关心特殊标记。</font><font style="vertical-align: inherit;">在这种情况下，请访问</font></font><code>BasicTokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">. </font><font style="vertical-align: inherit;">您可以对其进行训练，然后进行编码和解码，例如如下所示：</font></font></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-k">from</span> <span class="pl-s1">minbpe</span> <span class="pl-k">import</span> <span class="pl-v">BasicTokenizer</span>
<span class="pl-s1">tokenizer</span> <span class="pl-c1">=</span> <span class="pl-v">BasicTokenizer</span>()
<span class="pl-s1">tokenizer</span>.<span class="pl-en">train</span>(<span class="pl-s1">very_long_training_string</span>, <span class="pl-s1">vocab_size</span><span class="pl-c1">=</span><span class="pl-c1">4096</span>)
<span class="pl-s1">tokenizer</span>.<span class="pl-en">encode</span>(<span class="pl-s">"hello world"</span>) <span class="pl-c"># string -&gt; tokens</span>
<span class="pl-s1">tokenizer</span>.<span class="pl-en">decode</span>([<span class="pl-c1">1000</span>, <span class="pl-c1">2000</span>, <span class="pl-c1">3000</span>]) <span class="pl-c"># tokens -&gt; string</span>
<span class="pl-s1">tokenizer</span>.<span class="pl-en">save</span>(<span class="pl-s">"mymodel"</span>) <span class="pl-c"># writes mymodel.model and mymodel.vocab</span>
<span class="pl-s1">tokenizer</span>.<span class="pl-en">load</span>(<span class="pl-s">"mymodel.model"</span>) <span class="pl-c"># loads the model back, the vocab is just for vis</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="from minbpe import BasicTokenizer
tokenizer = BasicTokenizer()
tokenizer.train(very_long_training_string, vocab_size=4096)
tokenizer.encode(&quot;hello world&quot;) # string -> tokens
tokenizer.decode([1000, 2000, 3000]) # tokens -> string
tokenizer.save(&quot;mymodel&quot;) # writes mymodel.model and mymodel.vocab
tokenizer.load(&quot;mymodel.model&quot;) # loads the model back, the vocab is just for vis" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">如果您想效仿 OpenAI 的文本标记器，最好采用他们使用正则表达式模式按类别分割文本的方法。</font><font style="vertical-align: inherit;">GPT-4 模式是 的默认模式</font></font><code>RegexTokenizer</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，因此您只需执行以下操作即可：</font></font></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-k">from</span> <span class="pl-s1">minbpe</span> <span class="pl-k">import</span> <span class="pl-v">RegexTokenizer</span>
<span class="pl-s1">tokenizer</span> <span class="pl-c1">=</span> <span class="pl-v">RegexTokenizer</span>()
<span class="pl-s1">tokenizer</span>.<span class="pl-en">train</span>(<span class="pl-s1">very_long_training_string</span>, <span class="pl-s1">vocab_size</span><span class="pl-c1">=</span><span class="pl-c1">32768</span>)
<span class="pl-s1">tokenizer</span>.<span class="pl-en">encode</span>(<span class="pl-s">"hello world"</span>) <span class="pl-c"># string -&gt; tokens</span>
<span class="pl-s1">tokenizer</span>.<span class="pl-en">decode</span>([<span class="pl-c1">1000</span>, <span class="pl-c1">2000</span>, <span class="pl-c1">3000</span>]) <span class="pl-c"># tokens -&gt; string</span>
<span class="pl-s1">tokenizer</span>.<span class="pl-en">save</span>(<span class="pl-s">"tok32k"</span>) <span class="pl-c"># writes tok32k.model and tok32k.vocab</span>
<span class="pl-s1">tokenizer</span>.<span class="pl-en">load</span>(<span class="pl-s">"tok32k.model"</span>) <span class="pl-c"># loads the model back from disk</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="from minbpe import RegexTokenizer
tokenizer = RegexTokenizer()
tokenizer.train(very_long_training_string, vocab_size=32768)
tokenizer.encode(&quot;hello world&quot;) # string -> tokens
tokenizer.decode([1000, 2000, 3000]) # tokens -> string
tokenizer.save(&quot;tok32k&quot;) # writes tok32k.model and tok32k.vocab
tokenizer.load(&quot;tok32k.model&quot;) # loads the model back from disk" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当然，您希望根据数据集的大小来更改词汇表大小。</font></font></p>
<p dir="auto"><strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">特殊令牌</font></font></strong><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">最后，您可能希望向标记生成器添加特殊标记。</font><font style="vertical-align: inherit;">使用该函数注册它们</font></font><code>register_special_tokens</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font><font style="vertical-align: inherit;">例如，如果您使用 vocab_size 32768 进行训练，则前 256 个标记是原始字节标记，接下来的 32768-256 个标记是合并标记，在这些标记之后您可以添加特殊标记。</font><font style="vertical-align: inherit;">最后一个“真实”合并令牌的 id 为 32767 (vocab_size - 1)，因此您的第一个特殊令牌应该紧随其后，其 id 恰好为 32768。所以：</font></font></p>
<div class="highlight highlight-source-python notranslate position-relative overflow-auto" dir="auto"><pre><span class="pl-k">from</span> <span class="pl-s1">minbpe</span> <span class="pl-k">import</span> <span class="pl-v">RegexTokenizer</span>
<span class="pl-s1">tokenizer</span> <span class="pl-c1">=</span> <span class="pl-v">RegexTokenizer</span>()
<span class="pl-s1">tokenizer</span>.<span class="pl-en">train</span>(<span class="pl-s1">very_long_training_string</span>, <span class="pl-s1">vocab_size</span><span class="pl-c1">=</span><span class="pl-c1">32768</span>)
<span class="pl-s1">tokenizer</span>.<span class="pl-en">register_special_tokens</span>({<span class="pl-s">"&lt;|endoftext|&gt;"</span>: <span class="pl-c1">32768</span>})
<span class="pl-s1">tokenizer</span>.<span class="pl-en">encode</span>(<span class="pl-s">"&lt;|endoftext|&gt;hello world"</span>, <span class="pl-s1">allowed_special</span><span class="pl-c1">=</span><span class="pl-s">"all"</span>)</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="from minbpe import RegexTokenizer
tokenizer = RegexTokenizer()
tokenizer.train(very_long_training_string, vocab_size=32768)
tokenizer.register_special_tokens({&quot;<|endoftext|>&quot;: 32768})
tokenizer.encode(&quot;<|endoftext|>hello world&quot;, allowed_special=&quot;all&quot;)" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">当然，您也可以根据需要添加更多令牌。</font><font style="vertical-align: inherit;">最后，我想强调，我努力保持代码本身的干净、可读和可修改。</font><font style="vertical-align: inherit;">您不应该害怕阅读代码并理解它是如何工作的。</font><font style="vertical-align: inherit;">这些测试也是寻找更多使用示例的好地方。</font><font style="vertical-align: inherit;">这让我想起：</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">测试</font></font></h2><a id="user-content-tests" class="anchor-element" aria-label="永久链接：测试" href="#tests"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我们使用 pytest 库进行测试。</font><font style="vertical-align: inherit;">它们全部位于该</font></font><code>tests/</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">目录中。</font><font style="vertical-align: inherit;">首先</font></font><code>pip install pytest</code><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">，如果您还没有，那么：</font></font></p>
<div class="highlight highlight-source-shell notranslate position-relative overflow-auto" dir="auto"><pre>$ pytest -v <span class="pl-c1">.</span></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 tooltipped-no-delay d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="$ pytest -v ." tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">运行测试。</font><font style="vertical-align: inherit;">（-v 是冗长的，稍微漂亮一些）。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">锻炼</font></font></h2><a id="user-content-exercise" class="anchor-element" aria-label="永久链接： 锻炼" href="#exercise"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">对于那些尝试学习 BPE 的人，这里是建议的进阶练习，帮助您逐步构建自己的 minbpe。</font><font style="vertical-align: inherit;">请参阅</font></font><a href="/karpathy/minbpe/blob/master/exercise.md"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">练习.md</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">演讲</font></font></h2><a id="user-content-lecture" class="anchor-element" aria-label="永久链接：讲座" href="#lecture"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"></font><a href="https://www.youtube.com/watch?v=zduSFxRajkE" rel="nofollow"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">我在这个YouTube 视频的</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">存储库中构建了代码</font><font style="vertical-align: inherit;">。</font></font><a href="/karpathy/minbpe/blob/master/lecture.md"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">您还可以在Lecture.md</font></font></a><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">中找到本讲座的文本形式</font><font style="vertical-align: inherit;">。</font></font></p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">待办事项</font></font></h2><a id="user-content-todos" class="anchor-element" aria-label="永久链接： 待办事项" href="#todos"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ul dir="auto">
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编写一个更优化的 Python 版本，可以运行大文件和大词汇</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编写一个更优化的 C 或 Rust 版本（仔细思考）</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">将 GPT4Tokenizer 重命名为 GPTTokenizer 并支持 GPT-2/GPT-3/GPT-3.5 吗？</font></font></li>
<li><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">编写一个类似于 GPT4Tokenizer 的 LlamaTokenizer （即尝试等效的句子）</font></font></li>
</ul>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">执照</font></font></h2><a id="user-content-license" class="anchor-element" aria-label="永久链接：许可证" href="#license"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">麻省理工学院</font></font></p>
</article></div>
