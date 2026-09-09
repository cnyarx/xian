# 大模型学习教程交接

## 任务目标

在独立目录 `大模型学习教程/` 中完成一套 Obsidian Markdown 格式的大模型学习教程，要求：

- 先有完整学习路线；
- 每个理论主题都有独立教程；
- 正文真实出现的重要概念和公式都有独立解释页；
- 前置依赖可递归追溯到基础原语；
- 内容通俗、准确，包含例子、练习和答案；
- 专业概念尽量有中英文对照；
- 事实、论文和公式有可靠来源，不编造结论；
- 标题和正文不得出现“小白版”“高中生版”等读者能力标签。

当前 Goal 已恢复并处于 active；大模型教程的全量验收已完成并保留可复核证据。本轮沿弦理论路线图完成了"紫外发散与红外发散""正规化与重整化""重整化群""beta 函数""有效场论""Yang-Mills 理论""规范协变导数""Wilson 线与 Wilson 圈""规范固定""Faddeev-Popov 行列式""Faddeev-Popov 鬼场""BRST 对称性""BRST 上同调""量子反常""手征反常""Weyl 反常""反常消除""二维 Euclidean 场论""复坐标与全纯分解""二维自由玻色子""二维自由费米子"和"算符乘积展开"二十二个节点，并将两套学习路径之间的第二批跨学科关系、重整化群受限关系、有效场论—模型量化的受控近似关系，以及规范理论、Wilson 线、规范固定、FP 行列式、FP 鬼场、BRST、BRST 上同调、量子反常、手征反常、Weyl 反常、反常消除、二维 Euclidean 场论、复坐标与全纯分解、二维自由玻色子、二维自由费米子、算符乘积展开与群作用/等变性、概率结构、分次符号方法或局部展开方法之间的严格边界写入知识图谱。后续接手时应先读取当前 Goal 状态，再从"算符乘积展开"或路线图实际后继节点继续，同时把概念内容正确性、关联关系和跨学科图谱显式化作为首要验收目标。

## 目录与环境

- 项目目录：`/home/admin/github/cnyarx/xian`
- 教程目录：`/home/admin/github/cnyarx/xian/大模型学习教程`
- 本交接文档：`/home/admin/github/cnyarx/xian/handoffs/HANDOFF_ONTOLOGY_LEARNING.md`
- 教程子目录 `大模型学习教程/` 自身不含 `.git`，但其父项目 `/home/admin/github/cnyarx/xian` 已在较早步骤初始化为 Git 仓库（remote `git@github.com:cnyarx/xian.git`），可以使用 `git status`、`git diff` 等命令。
- 所有已执行修改均已直接写入本地文件，没有只存在于会话内存、尚未落盘的代码改动。

## 当前规模

最近一次成功统计：

- Markdown 文件：188 个；
- 理论教程：73 篇；
- 概念原子页：61 篇；
- 公式页：26 篇；
- 动手项目：7 个；
- 73/73 篇理论教程均有“概念与公式导航”；
- 7 个项目共 9 个 Python 代码块已通过 `py_compile` 静态语法检查。

注意：这些数字只能证明结构存在，不能证明内容已经全部正确或 Goal 已完成。

## 本轮已经落盘的修改

### 1. 理论教程事实与公式修正

已修改：

- `01-数学基础/04-概率分布.md`
  - 区分离散均匀分布与连续均匀分布；
  - 明确连续分布单点概率为 0，等长区间概率相等。
- `01-数学基础/07-指数与对数.md`
  - 不再把一般实数指数定义成重复相乘；
  - 增加 $a^x=\exp(x\ln a)$；
  - 区分幂律在双对数坐标上线性化与指数关系在半对数坐标上线性化。
- `01-数学基础/08-高维空间直觉.md`
  - 删除“每个词固定为 4096 维”“注意力一定在几千维计算”等错误概括；
  - 改为 token、隐藏维度和每头维度由具体架构决定；
  - 修正 Transformer 来源说明，明确原论文使用缩放点积而非默认余弦相似度。
- `03-机器学习基础/03-损失函数.md`
  - 区分 $\partial L/\partial p_y=-1/p_y$ 与 softmax 交叉熵对 logits 的梯度 $p_i-y_i$；
  - 删除“损失大所以训练梯度一定很大”的错误说法。
- `06-注意力与Transformer/05-残差连接与层归一化.md`
  - 增加 `[1,2,3]` 的 LayerNorm 可复算数值例子。
- `07-预训练/05-训练稳定性.md`
  - 增加 loss spike 的完整排查示例与证据链。
- `08-后训练与对齐/06-合成数据与蒸馏.md`
  - 扩充合成数据定义，不再限定为“由模型生成”；
  - 明确蒸馏教师更大或更强不是定义的必要条件。

### 2. 概念原子页修正

已修改：

- `15-概念词典/31-分类回归与学习范式.md`
  - 增加策略、奖励、优势与基线的前置依赖。
- `15-概念词典/32-数据划分与预处理.md`
  - 给“测试集无偏评估”补充独立性、代表性和未参与模型选择的条件。
- `15-概念词典/33-梯度消失与梯度爆炸.md`
  - 参数梯度公式补上 $\partial h_1/\partial\theta_1$；
  - 增加雅可比乘积的适用边界。
- `15-概念词典/34-因果掩码与注意力掩码.md`
  - 修正“因果掩码只适用于 decoder-only”的错误；
  - 区分 encoder、decoder 自注意力和交叉注意力。
- `15-概念词典/37-维度灾难与高维直觉.md`
  - 对 $[0,1]^D$ 均匀点，修正典型距离量级为 $\sqrt{D/3}$。
- `15-概念词典/38-指数对数与数值范围.md`
  - 修正一般实数指数定义与底数、对数定义域条件。
- `15-概念词典/39-上下文学习.md`
  - 删除“模型越大 ICL 必然越强”的无条件概括。
- `15-概念词典/40-旋转矩阵与位置编码数学.md`
  - 增加 RoPE 相对位置点积性质；
  - 明确列向量约定下依赖 $n-m$。
- `15-概念词典/41-通用近似定理.md`
  - 增加激活函数公式前置依赖；
  - 修正“任意非线性激活都可以”的过宽表述；
  - 明确定理只保证存在性。
- `15-概念词典/42-权重绑定.md`
  - 删除“输入嵌入和输出投影互逆”的错误；
  - 若 $U\in\mathbb R^{V\times d}$，修正为 $z=Uh$；
  - 解释另一种 $d\times V$ 约定何时写成转置。
- `15-概念词典/43-数据预处理流水线.md`
  - 增加 Token 前置依赖；
  - 删除“代码占比 10–20% 一定改善推理”“清洗后通常几 TB”等无条件数字。
- `15-概念词典/44-后训练与指令微调.md`
  - 增加负对数似然和优化器前置依赖；
  - 删除“使模型学会思考”的过度承诺。
- `15-概念词典/45-偏好数据与RLHF.md`
  - 修正 RLAIF 定义，强调仍需人工目标、准则、校准和审计；
  - 增加 Constitutional AI 来源。
- `15-概念词典/46-DPO与GRPO.md`
  - 区分奖励模型、奖励信号和价值模型；
  - 明确 GRPO 省去的是单独价值函数，不是奖励来源。
- `15-概念词典/47-合成数据与知识蒸馏.md`
  - 增加熵与 KL 前置依赖；
  - 扩充合成数据定义并修正学生与教师能力边界。
- `15-概念词典/48-推理训练与推理时扩展.md`
  - 删除成本必然“线性或更快增长”的无条件结论；
  - 增加过程奖励来源。
- `15-概念词典/50-推理阶段与延迟指标.md`
  - TPOT 分母修正为输出 token 数减 1；
  - 增加单 token 输出和 ITL 口径边界。
- `15-概念词典/51-KV-Cache基础.md`
  - 使用 $H_{kv}$ 而非笼统的注意力头数；
  - 修正算例：MHA 为 1 GiB，8 个 KV 头的 GQA 为 256 MiB。
- `15-概念词典/53-检查点与容错.md`
  - 补充随机状态、确定性算子、拓扑、通信顺序、软件和硬件版本条件；
  - 修正检查点资源开销描述。
- `15-概念词典/54-模型量化方法.md`
  - 增加量化公式前置依赖；
  - 删除“QAT 精度最高”的绝对说法。
- `15-概念词典/55-模型服务与部署.md`
  - 增加 HTTP、零信任架构和 OpenTelemetry 来源。
- `15-概念词典/56-向量检索与ANN.md`
  - 删除缺少实验条件的“1 秒、5ms、95%”数字；
  - 改为要求在目标数据上测延迟—召回率曲线。
- `15-概念词典/57-工具调用与执行权限.md`
  - 增加 JSON、JSON Schema、NIST 和 OWASP 来源。
- `15-概念词典/58-模型幻觉.md`
  - 按 Maynez taxonomy 统一内在/外在幻觉定义；
  - 区分对来源忠实与对世界事实正确；
  - 删除“概率模型必然无法消除幻觉”的伪定理式表述。

### 3. 公式页修正与答案

已修改：

- `16-公式手册/08-激活函数公式.md`
  - 明确 ReLU 在 0 处不可导，框架按约定选次梯度。
- `16-公式手册/11-位置编码与RoPE公式.md`
  - 列向量约定下修正为 $R((n-m)\theta)$；
  - 说明不同约定可能写成相反符号。
- `16-公式手册/08` 至 `22`
  - 已为此前缺失的 46 道最小自测补答案。
- `16-公式手册/22-MoE路由与组合公式.md`
  - 已是 softmax 权重时，Top-2 重归一化直接除以保留权重之和，不再次 softmax。

### 4. 动手项目修正

#### 项目 02：手写数字识别

文件：`14-动手项目/02-手写数字识别.md`

已完成：

- 新增 `IndexedDataset`；
- DataLoader 返回原始数据集索引；
- 错误样本 JSON 保存 `dataset_index`、真实标签和预测标签；
- 验收说明明确可用 `test_set[dataset_index]` 重新读取原图。

#### 项目 05：微调一个开源模型

文件：`14-动手项目/05-微调一个开源模型.md`

已完成：

- `--revision` 改为必填，拒绝浮动 `main` 和 `None`；
- `MODEL_LICENSE_CHECK` 改为必填；
- 增加随机种子；
- 增加固定 `test_instructions.txt` 示例；
- 增加训练前后使用相同贪心解码的推理；
- 保存 `test_outputs.json`；
- 元数据记录 revision、seed、测试指令文件和依赖版本；
- 运行说明通过 Hugging Face API 实时读取真实 commit SHA，失败时停止，不猜 hash。

重要边界：当前机器两次访问 Hugging Face 均连接超时，因此没有把未经真实 API 核验的 SHA 写进文档，也没有端到端运行 LoRA 项目。

#### 项目 07：部署一个本地模型

文件：`14-动手项目/07-部署一个本地模型.md`

已完成：

- 增加 Python 3.10+、Gradio 版本范围和 `pip freeze`；
- 增加硬件与内存粗估边界；
- Ollama 模型改为先用 `ollama list/show` 核验，再设置 `$OLLAMA_MODEL`；
- 客户端和界面命令使用 `$OLLAMA_MODEL`，不再保留 `<已核验的本地模型名>` 占位符；
- 要求保存模型 digest、许可证和服务版本。

重要边界：当前机器没有模型服务和权重，未做真实模型端到端验证。

### 5. README

文件：`大模型学习教程/README.md`

已修正：

- 05 目录不再错误写入“嵌入”；
- 11 目录不再错误写入“蒸馏”；
- 12 目录不再错误写入“思维链”；
- 更新 08、11、12 的实际内容描述。

## 已完成验证

### 数值复算

已独立复算：

- MHA KV Cache 算例：1 GiB；
- 8 个 KV 头的 GQA 算例：256 MiB；
- 10 维单位超立方体内切球体积占比约 0.249%。

### Python 代码静态检查

已从 7 个项目动态抽取 9 个 Python fenced code block，并使用 Python `compile(..., "exec")` 做与 `py_compile` 等价的语法检查。逐项结果：

- `14-动手项目/01-从零实现一个感知机.md`：2/2 通过；
- `14-动手项目/02-手写数字识别.md`：1/1 通过；
- `14-动手项目/03-实现一个Transformer块.md`：1/1 通过；
- `14-动手项目/04-训练一个微型语言模型.md`：1/1 通过；
- `14-动手项目/05-微调一个开源模型.md`：1/1 通过；
- `14-动手项目/06-搭建一个RAG系统.md`：1/1 通过；
- `14-动手项目/07-部署一个本地模型.md`：2/2 通过。

汇总：`py_compile_passed: 9`，`py_compile_failed: 0`。该结果仅证明语法成立，不代表项目端到端通过。

### prerequisites 依赖图

旧检查器曾错误输出 `prereq_edges: 0`；后续一次解析又因未自动补 `.md` 而误报 143 个缺失目标。这两次结果均无效。

现已使用 `yaml.safe_load` 读取 frontmatter，并按以下规则解析目标：去除 alias 和锚点、自动补 `.md`、路径链接相对来源文件目录解析、裸文件名优先来源目录并在全库按唯一 stem 回退。真实结果：

- Markdown 节点：188；
- `prereq_edges: 399`；
- `missing_targets: 0`；
- `ambiguous_targets: 0`；
- `dependency_cycles: 0`；
- `inverse_concept_level_edges: 0`；
- `cross_directory_formula_edges: 83`（公式页指向其他目录 76 条，其他目录指向公式页 7 条，二者无重叠）；
- `text_prerequisite_requirements: 4`。

四条文字基础要求是：

1. `01-数学基础/01-向量与矩阵.md`：基本算术与坐标表示；
2. `01-数学基础/03-概率基础.md`：分数与基本算术；
3. `01-数学基础/06-导数与梯度.md`：简单方程与函数图像；
4. `01-数学基础/07-指数与对数.md`：指数的基本运算。

### 项目实际运行与环境边界

- 项目 01（感知机）：已使用本机 NumPy 1.26.4 执行完整训练流程，4 轮收敛，预测为 `[0, 0, 0, 1]`，`all_checks_passed: True`，端到端通过。
- 项目 02（MNIST）：当前缺少 `torch`、`torchvision`，未下载数据，未端到端运行。
- 项目 03（Transformer 块）：当前缺少 `torch`，仅通过语法检查，未端到端运行。
- 项目 04（微型语言模型）：当前缺少 `torch`，仅通过语法检查，未端到端运行。
- 项目 05（LoRA 微调）：当前缺少 `torch`、`peft`、`datasets`；Hugging Face API 返回 `URLError <urlopen error [Errno 97] Address family not supported by protocol>`，无法核验真实 revision，未端到端运行。
- 项目 06（RAG）：当前缺少 `faiss` 等运行依赖，仅通过语法检查，未端到端运行。
- 项目 07（本地部署）：当前缺少 `gradio`，且没有 `ollama`、`llama-cli`、`llama-server` 命令、模型服务和已核验权重，未端到端运行。

当前可导入：`numpy`、`transformers`、`requests`。不可导入：`torch`、`torchvision`、`peft`、`datasets`、`faiss`、`gradio`。上述阻塞均按真实环境记录，不能写成端到端通过。

### 全库结构检查

对 188 篇 Markdown 的最近一次完整扫描结果：

- Obsidian 链接：1054；
- `broken_links: 0`；
- `ambiguous_links: 0`；
- `theory_navigation_missing: 0`；
- `formula_answer_missing: 0`；
- `control_characters: 0`；
- `placeholders: 0`。

这些指标与 prerequisites 图是两类独立检查，不能用结构扫描替代语义终审。

## 独立内容终审结果

所有终审均由只读 Agent 执行；发现的问题由主线程串行修改，再由独立 Agent 复验。

### 理论页、项目与后段概念页

- 本轮修改的理论页：前一轮记录问题均已消除；另发现 `01-数学基础/07-指数与对数.md` 将零次幂概括为“任何数”的新 Critical，已限定为非零底数并说明 $0^0$ 不能由该规则直接定义，独立复验通过；
- 概念词典 48–58：前一轮记录问题均已消除，未发现新 Critical；
- 项目 02、05、07 与 README：前一轮记录问题均已消除，未发现新 Critical。

### 概念词典 31–47

逐篇原问题和最终证据：

- `31-分类回归与学习范式.md`：原缺少策略、奖励、优势与基线前置，已加入对应依赖；终审新发现“强化学习必须大量交互”的无条件概括，现已区分在线模型无关、离线和模型式方法；**已消除**。
- `32-数据划分与预处理.md`：原测试集评估缺少独立性、代表性和未参与调参条件；现已明确测试样本应独立且来自目标分布，并规定依赖数据的预处理仅用训练集拟合；**已消除**。
- `33-梯度消失与梯度爆炸.md`：原参数梯度遗漏局部导数并以单层雅可比判断全路径；公式已修正；终审新发现“等价于浅层模型”，现明确冻结前层仍执行非线性变换；**已消除**。
- `34-因果掩码与注意力掩码.md`：原误称因果掩码只适用于 decoder-only；已区分三类注意力；终审新发现预测索引与允许 $i=j$ 冲突，现明确位置 $i$ 的状态使用 $0\ldots i$ 并预测 $i+1$；**已消除**。
- `37-维度灾难与高维直觉.md`：原距离量级错误，已由 $E\|X\|^2=D/3$ 修正为 $\sqrt{D/3}$；**已消除**。
- `38-指数对数与数值范围.md`：原一般实数指数与定义域错误；终审发现零次幂仍缺少 $a\ne0$，现明确不定义 $0^0$ 且零不能取负指数；**已消除**。
- `39-上下文学习.md`：原“模型越大 ICL 必然越强”已限定；终审发现 zero-shot 与“必须有示例”的定义冲突，现明确采用示例可选的广义 ICL 口径；**已消除**。
- `40-旋转矩阵与位置编码数学.md`：原缺少 RoPE 相对位置性质；已补 $n-m$；终审发现把整个点积说成只依赖位置差，现明确只有 RoPE 引入的位置依赖通过 $n-m$ 出现，数值仍依赖 $q,k$；**已消除**。
- `41-通用近似定理.md`：原激活条件和存在性边界缺失；已补；终审发现自测答案又无条件声称深层参数效率，现限定到特定函数族、网络类别、激活与误差标准；**已消除**。
- `42-权重绑定.md`：原互逆和矩阵转置错误已修正；终审发现按模型大小概括收益，现区分固定参数节省、占总参数比例和任务性能；**已消除**。
- `43-数据预处理流水线.md`：原 Token 依赖和无条件定量结论已修正；**已消除**。
- `44-后训练与指令微调.md`：原负对数似然、优化器依赖和“学会思考”承诺已修正；**已消除**。
- `45-偏好数据与RLHF.md`：原 RLAIF 取消人工和缺少 Constitutional AI 来源已修正；**已消除**。
- `46-DPO与GRPO.md`：原奖励、奖励模型与价值模型混淆已修正；终审发现“参考策略是效果上限”，现明确参考策略只是正则化锚点；**已消除**。
- `47-合成数据与知识蒸馏.md`：原熵与 KL 依赖、合成数据范围和师生能力边界已修正；**已消除**。

独立复验：上述原残留 2 项和新 Critical 10 项全部消除，**必须修正 0，新 Critical 0**。

### 公式手册 08–22

前一轮原 Critical 均已消除：ReLU 在 0 点已区分数学不可导与软件次梯度约定；RoPE 在当前列向量约定下使用 $n-m$；Top-2 对保留 softmax 权重直接除以权重和；46/46 道练习均已有答案。

终审新发现并修正：

- `10-缩放点积与多头注意力公式.md`：区分投影前 $X_Q,X_K,X_V$ 与投影后 $Q_i,K_i,V_i$，形状链闭合；
- `12-FFN与SwiGLU公式.md`：统一使用列向量和 $W x$ 约定；
- `15-梯度裁剪与全局批量公式.md`：改为分段形式，$g=0$ 不再计算除法，并补不同 micro-batch 大小时按样本或 token 加权；
- `18-均匀仿射量化公式.md`：全零张量使用正的安全尺度并令量化值等于零点，反量化仍为零；
- `20-DPO与ORPO损失公式.md`：定义长度归一化 SFT 项、序列概率和 odds；
- `14-缩放定律与训练计算量公式.md`：自测答案只保留 $9^{-0.5}=1/3$，并区分经验损失拟合、算法 FLOPs 与墙钟效率；
- `17-KV-Cache容量公式.md`：自测答案区分逻辑 KV 元素、前缀块共享和块内浪费。

独立复验：5 个新 Critical 和 3 道答案限定全部修好，**必须修正 0，新 Critical 0**。

## 参考资料总索引复验

文件：`18-参考资料/参考资料总索引.md`

已分类更新：

- 论文与技术报告：补入 Maynez、Lightman；Constitutional AI 原本已存在；
- 教材与正式标准：单列 IEEE 754、RFC 8259、JSON Schema Draft 2020-12、RFC 9110、NIST SP 800-207、NIST AI RMF；
- 官方软件与 API 文档：补入 OpenTelemetry 和 OWASP 提示注入防护指南；
- 删除跨栏目重复的 IEEE 754 和 NIST AI RMF 条目；
- 未纳入 localhost、本地示例 URL 或代码动态生成 URL。

## 跨学科关系图谱进展

本轮新增项目级索引：

- `弦理论与大模型跨学科关系图谱.md`

索引按以下层级维护关系：

1. 数学对象直接相同；
2. 共享结构但不等价；
3. 同名异义术语辨析；
4. 禁止误连。

已建立并双向写回页面的第一批连接：

- Gaussian 积分 ↔ 概率分布、正态分布；
- 梯度 ↔ 梯度下降；
- 矩阵 ↔ 点积与矩阵乘法；
- 指数函数、对数函数 ↔ softmax、交叉熵和缩放定律所在的“指数与对数”；
- QFT 紫外/红外发散与正规化术语 ↔ ML 过拟合与正则化、正则化与泛化。

第二批连接（7 组，18 个目标页面定向验证通过）：

- Fourier 级数 ↔ 位置编码、旋转矩阵与位置编码数学；
- 概率（含 Born 规则） ↔ 概率基础；
- 向量空间 ↔ 高维空间直觉；
- 群作用 ↔ 旋转矩阵与位置编码数学；
- Feynman 图 ↔ 计算图、自动微分与梯度累加；
- 路径积分 ↔ 梯度下降；
- 正规化与重整化 ↔ 过拟合与正则化、正则化与泛化。

规范解析器对本轮 18 个目标页面复验：

- 本批次新增链接断链：0；
- 歧义链接：0；
- 跨两套教程的可解析链接：40；
- 7 组关系全部双向可解析；
- YAML 解析失败：0；
- 控制字符：0；
- `git diff --check`：通过。

目标页中另有 12 个弦理论路线图预告链接尚未创建，包括“弦的模展开”“轨道”“稳定子群”“商空间”“世界面路径积分”等；它们是本轮修改前已存在的未来节点，不属于第二批新增关系，也未据此创建空白占位页。

必须保留的边界：

- Feynman 图不等于计算图；
- 传播子不等于反向传播；
- 路径积分不等于 SGD；
- ML regularization 不等于 QFT regularization 或 renormalization；
- 数学泛函不等于软件库中的 `functional` 命名；
- 大模型高维参数空间不等于弦理论临界时空维数。

## 弦理论路线图新增节点

新增：`弦理论/物理学/紫外发散与红外发散.md`。

该页已覆盖：

- UV 高动量/短距离与 IR 软、共线、特殊运动学、零模区域；
- 一般表面发散度 $\omega=dL-2I+\sum_v r_v$，其中 $r_v$ 严格定义为圈动量缩放下的顶点多项式最高次数；
- 四维无导数纯 $\phi^4$ 连通图的 $\omega=4-E$ 及适用条件；
- 硬截止蝌蚪积分的 $1/(16\pi^2)$ 系数、二次 UV 发散；
- 四点泡图的对数 UV 发散；
- 无尺度积分在维数正规化中为零不代表普通收敛；
- soft 与 collinear 的区别，以及质量和外部运动学的真实边界；
- 子发散、UV/IR 重叠、包容可观测量与实虚辐射相消；
- ML 正则化、QFT 正规化和 QFT 重整化的术语辨析；
- 弦世界面模空间对 UV/IR 区域的重新组织及有限性边界。

同步修改：

- `圈展开.md` 的 `used_by` 已指向“紫外发散与红外发散”；
- 移除了“紫外发散与红外发散文件尚不存在”的过时说明；
- 后继“正规化与重整化”已建立，`used_by`、正文导航和关系区均已形成真实双链。

独立物理终审先发现并修复两项：

1. $r_v$ 不能笼统等于顶点总导数数，必须按圈动量缩放次数定义；
2. 外部带电粒子质量不能一般性消除无质量光子的 soft 发散，质量对 soft/collinear 的作用需区分。

最终独立复验：**必须修正 0，新 Critical 0**。

新增：`弦理论/物理学/正规化与重整化.md`。

该页已覆盖：

- 裸场、裸质量、裸耦合与组合重整化常数 $Z_\phi,Z_m,Z_\lambda$ 的一致定义；
- 维数正规化 $d=4-2\varepsilon$、$\mu^{4-d}$ 积分测度和 $1/\bar\varepsilon$；
- 一圈蝌蚪自能、泡图、三个散射道和对称因子；
- MS-bar 乘法反项 $\delta_m=-\lambda/(32\pi^2\bar\varepsilon)$、$\delta_\lambda=3\lambda/(32\pi^2\bar\varepsilon)$；
- 四维一圈 $\beta(\lambda)=3\lambda^2/(16\pi^2)$ 及 $d$ 维推导；
- MS、MS-bar 与 on-shell 方案的区别；
- 可重整化理论与 EFT 的边界；
- ML regularization、QFT regularization 和 QFT renormalization 的术语辨析。

独立公式终审先发现并已修复：

1. 泡图振幅遗漏 $i$，有限项多出无来源常数 $2$；
2. 乘法质量与耦合反项的符号、系数及耦合次数错误；
3. 基本维数正规化积分左侧遗漏 $\mu^{4-d}$，导致等式量纲不一致；
4. 裸参数 $Z$ 因子定义与代入 Lagrangian 不一致；
5. $\ln(4\pi)$ 错算成 $\ln4$，使数值例子错误；
6. 练习积分测度遗漏 $(2\pi)^{-d}$；
7. $\beta$ 函数推导过度跳步，现已显式给出 $\beta_d=-2\varepsilon\lambda+3\lambda^2/(16\pi^2)$。

2026-09-08 最终独立复验结果：

- 公式终审：**Critical 0**；$\mu^{4-d}$ 量纲、组合 $Z$ 定义、反项符号与系数、泡图 $i$ 因子、数值例、练习测度和 $\beta_d$ 推导全部 Pass；
- 教学结构终审：**Critical 0**；正文、适用条件、常见误区和 12 道练习答案一致；
- 已进一步限定固定阶残余方案依赖、单耦合质量无关方案下 $\beta$ 函数前两项的普适范围，以及无质量粒子 $p^2=0$ 质量壳附近的 IR/无尺度积分边界；
- 弦世界面模空间退化只表述为长管传播、低能因子化和 IR 区域，不再与普通参数重整化混同。

新增：`弦理论/物理学/重整化群.md`。

该页已覆盖：

- beta 函数 $\beta_i(g)=\mu dg_i/d\mu$，质量反常维数 $\gamma_{m^2}$ 和场反常维数 $\gamma_\phi$ 的一致定义；
- Callan–Symanzik 方程 $[\mu\partial_\mu+\beta\partial_g+\gamma_{m^2}m_R^2\partial_{m_R^2}+n\gamma_\phi]G_R^{(n)}=0$，并警告改 1PI 顶点或 $Z_\phi$ 方向时符号可能反转；
- 四维 $\lambda\phi^4$ 一圈 $\beta=3\lambda^2/(16\pi^2)$、运行耦合 $\lambda(\mu)=\lambda_0/[1-3\lambda_0\ln(\mu/\mu_0)/(16\pi^2)]$ 和 Landau 极点 $\mu_L=\mu_0\exp(16\pi^2/(3\lambda_0))$；
- RG 改善与大对数重求和 leading-log 几何展开及收敛条件；
- 固定点 $\beta_i(g_*)=0$ 和线性化 $M_{ij}=\partial\beta_i/\partial g_j|_{g_*}$，在 $\mu$ 增大向 UV 约定下 $\theta<0$ 为 UV 吸引、$\theta>0$ 为 UV 排斥/IR 吸引；
- $d=4-2\varepsilon$ 下 Wilson–Fisher 固定点 $\lambda_*=32\pi^2\varepsilon/3+O(\varepsilon^2)$ 和 $\beta_d'(\lambda_*)=2\varepsilon$；
- Wilsonian 动量壳层、粗粒化、重标度和无量纲化耦合分类；
- 微扰 RG 与 Wilsonian RG 的异同；
- EFT 与 RG 的边界：运行不能替代阈值匹配，高维算符按 $(E/\Lambda)^{\Delta_i-d}$ 抑制；
- 弦理论：区分时空 EFT 的 RG、世界面 Weyl 反常系数、非线性 sigma 模型的世界面 beta 函数和模空间退化；
- 机器学习：限于特定变分 RG 与受限 Boltzmann 机的已知映射，明确指出 Transformer 层数不是 RG 步数，严格映射需要 trace condition 等条件。

独立终审结果：

- 公式终审：**Critical 0**；A–H 八项全部 Pass：$\beta$ 函数、运行耦合积分、Landau 极点、$d=4-2\varepsilon$ 固定点、Callan–Symanzik 符号、UV/IR 方向、leading-log 展开、数值 526.4；
- 教学结构终审：**Critical 0**；练习答案一致，符号边界清晰，ML 类比限定严格，conformal/Weyl 反常系数已精确化，EFT 幂次抑制已补指数，Wilsonian 分类已补无量纲化耦合和固定点邻域条件，trace condition 已纳入 ML 严格映射条件。

重整化群节点同步修改：

- `正规化与重整化.md` 的 `used_by` 和关系区已指向本节点；
- `微扰论.md` 删除陈旧 `[[重整化]]` 断链，改回 `正规化与重整化` 并新增 `重整化群` 链接；
- `对数函数.md` 删除两处“对应独立文件尚未建立”的旧说明，替换为真实 `[[重整化群]]` 链接；
- `生成泛函.md` 的 `used_by` 和关系区已指向本节点；
- `常微分方程.md` 的 `used_by` 和关系区新增本节点链接；
- `弦理论与大模型跨学科关系图谱.md` 新增重整化群受限关系，并补禁止误连条目。

新增：`弦理论/物理学/beta 函数.md`。

该页已覆盖：

- 在裸参数固定时定义 $\beta^i(g)=\mu\,dg^i/d\mu$，并区分 $\mu d/d\mu$ 与 $d/d\ln\mu^2$ 的因子 $2$；
- 在 $d=4-2\varepsilon$ 中区分经典项 $-\kappa\varepsilon g$ 与四维量子 beta；
- 从 MS/$\overline{\mathrm{MS}}$ 完整极点塔推导 $\beta_d=-\kappa\varepsilon F/(\partial_gF)$ 和 $\beta(g)=\kappa[g a_1'(g)-a_1(g)]$；
- $\lambda\phi^4/4!$ 的一圈、两圈系数，QED 一圈 $a_1(e)=e^3/(24\pi^2)$ 与 $\beta_e=e^3/(12\pi^2)$，QCD 一圈 $\beta_0=11N_c/3-2n_f/3$ 与渐近自由；
- 单耦合前两个系数的方案普适条件、多耦合 beta 向量的坐标变换和固定点稳定矩阵边界；
- 世界面非线性 sigma 模型 $\beta^G_{\mu\nu}=\alpha'R_{\mu\nu}+O(\alpha'^2)$ 的适用条件、尺度方向及其与 Weyl 反常系数的区别；
- beta 只控制耦合跑动，完整 RG 演化还需场与复合算符的反常维数和算符混合矩阵；
- 12 道练习覆盖简单极点、QED、QCD、方案变换、多耦合、世界面 beta 和重夸克阈值 EFT 匹配。

独立终审结果：

- 公式终审：**Critical 0**；MS 极点通式、$\lambda\phi^4$ 一二圈、QED、QCD、方案变换、多耦合向量、sigma 模型和练习算术均通过；
- QED 练习答案曾把 $a_1(e)$ 误写为 $e^3/(12\pi^2)$，已修正为 $e^3/(24\pi^2)$，与正文和简单极点公式一致；
- 教学终审最初发现 1 个 Critical：错误声称 beta 单独控制所有算符；已改为 beta 控制耦合，完整 RG 需反常维数和算符混合；
- 聚焦复验又发现练习 2 未处理 $\beta a_1'/\varepsilon$ 的阶数边界；已将题目限定到最低非平凡微扰阶，显式说明该项为更高耦合阶，并指出全阶推导必须恢复完整极点塔；
- 最终独立教学复验：**Critical 0**；原 Critical、练习 2、QED $a_1(e)$、练习 5/12 和方案边界全部 Pass。

beta 函数节点同步修改：

- `正规化与重整化.md`、`重整化群.md`、`曲率.md`、`群表示.md` 和 `Lie 代数.md` 均已在 `used_by` 与关系区建立回链；
- beta 页对以上 5 个前驱建立正向链接，定向复验为双向导航 5/5；
- 后继“有效场论”现已创建，beta 页的 `used_by` 和关系区已建立真实链接。

新增：`弦理论/物理学/有效场论.md`。

该页已覆盖：

- EFT 的四个组成：低能自由度、对称性、幂次计数和截断阶数；
- 一般 Lagrangian $\mathcal L_{\mathrm{EFT}}=\mathcal L_{\mathrm{light}}^{(\Delta\le d)}+\sum_i C_i\mathcal O_i/\Lambda^{\Delta_i-d}$；
- $d$ 维场的 canonical dimension、弱耦合 Gaussian power counting 与完整 scaling dimension 的边界；
- 算符基、分部积分、低阶运动方程、局域场重定义及 on-shell/off-shell 基的区别；
- 路径积分意义下积分掉重场，并以重标量模型推导 $g^2J^2/(2M^2)-g^2J\Box J/(2M^4)+\cdots$；
- matching、RG running、算符混合、阈值 matching、MS-bar 中不自动退耦和 non-decoupling 边界；
- EFT cutoff、regulator 与重整化尺度 $\mu$ 的区别；
- “不可重整化算符”在固定 $E/\Lambda$ 阶数下仍可逐阶预测；
- 截断误差、振幅与截面干涉阶数、Fermi 四费米理论；
- 弦低能展开中的 $\alpha'E^2$、$g_s$、KK/绕弦阈值，及质量零极点与局域高导数项的区别；
- 13 道练习覆盖自由度/对称性、power counting/截断、matching/running、阈值/non-decoupling、冗余算符和弦低能展开。

独立终审结果：

- 公式与物理事实终审：**Critical 0**；A–K 全部 Pass，重标量符号与 $1/2$ 因子、matching 余项、Wilson 系数运行、阈值退耦、Fermi 归一化和弦低能展开均正确；
- 教学结构终审：**Critical 0**；正文顺序、概念边界和相关页面分工全部 Pass；
- 教学终审曾建议练习增加自由度/对称性、power counting/截断、冗余算符和 non-decoupling 覆盖，现已由 12 道扩展为 13 道；
- 聚焦复验：**Critical 0**；$\mathbb Z_2$ 单标量 $\Delta\le6$ 的 on-shell/EOM-reduced 算符基、$\phi^3\Box\phi$、$\phi^2(\partial\phi)^2$、$(\Box\phi)^2$ 的冗余边界和 off-shell 限定均通过。

有效场论节点同步修改：

- `经典场论.md`、`路径积分.md`、`微扰论.md`、`S 矩阵.md`、`Feynman 图.md`、`正规化与重整化.md`、`重整化群.md` 和 `beta 函数.md` 均建立真实回链；
- 有效场论页对以上 8 个前驱或关联页面建立正向链接，定向复验为双向导航 8/8；
- `弦理论与大模型跨学科关系图谱.md` 新增“有效场论与模型量化中的受控近似”；
- `大模型学习教程/11-部署与优化/01-模型量化.md` 与有效场论页互相回链，并都指向跨学科图谱；
- 该关系只比较“指定适用域、压缩不可分辨细节、用误差验收近似”的方法结构，明确禁止 EFT=模型量化/知识蒸馏/LoRA，以及 Wilson 系数/matching=量化 scale/zero-point/校准；
- 后继“Yang-Mills 理论”已经创建并通过终审；有效场论页的 `used_by`、正文导航和关系区已改为真实链接。

新增：`弦理论/物理学/Yang-Mills 理论.md`。

该页已覆盖：

- Hermitian 生成元、结构常数与表示依赖的迹归一化；
- 物质表示、规范协变导数、有限规范变换和规范势的非齐次变换；
- $F_{\mu\nu}=\frac{i}{g}[D_\mu,D_\nu]$、Yang-Mills 作用量、运动方程与 Bianchi 恒等式；
- 三、四规范玻色子自相互作用及 Abelian 群与 $g\to0$ 的不同极限；
- $d-2$ 个物理偏振、规范固定、Faddeev-Popov 鬼场和 BRST 的分工预告；
- Chan-Paton 标签、分离/重合 D-brane、$U(1)^N\to U(N)$ 增强和 DBI 小场强展开；
- bosonic open string 与超弦首批 $\alpha'$ 修正阶数的边界；
- 15 道练习及答案。

Yang-Mills 节点同步修改：

- `有效场论.md`、`beta 函数.md`、`经典场论.md`、`Maxwell 方程.md`、`群表示.md` 和 `曲率.md` 新增真实回链；
- `规范对称性.md`、`Maxwell 场量子化.md`、`Lie 群.md` 和 `Lie 代数.md` 已有回链，定向验证合计 10/10；
- 上一页 `有效场论` 和总路线均可点击；下一页“规范协变导数”尚未创建，保留普通文本而不制造断链；
- `弦理论与大模型跨学科关系图谱.md` 将该节点纳入群作用/表示/等变性的“共享数学语言但不等价”关系，并明确局域规范变换、规范轨道、规范固定、鬼场、BRST 和自相互作用不得与大模型概念强行等同。

独立终审与结构验收：

- 独立终审：**Critical 0**；协变导数、场强、规范变换、作用量、三/四点系数、源流定义、DBI 边界和 15 道答案全部 Pass；
- YAML：通过；tags 4/4；prerequisites 7/7；
- 页面 Obsidian 链接 23 个，缺失 0；未来链接 0；
- 学习导航 3/3；练习 15/15，答案 15/15；控制字符 0；
- `git diff --check`：通过。

新增：`弦理论/物理学/规范协变导数.md`。

该页已覆盖：

- 表示 $R$ 中 $D_\mu=\partial_\mu-igA_\mu^aT_R^a$ 的定义；
- 基本表示、伴随表示、规范单态和对偶表示的具体公式；
- 伴随表示中结构常数和符号的完整传递；
- $U(1)$ 电磁约定 $D_\mu=\partial_\mu+iqA_\mu$ 与 Yang-Mills 约定的对应；
- 张量积表示上的 Leibniz 法则；
- $D_\mu'(U\psi)=U(D_\mu\psi)$ 的显式验证；
- 协变导数对易子、规范场强和表示依赖；
- 与时空联络、切丛协变导数和内部对称向量丛的分工边界；
- 8 道练习及答案。

规范协变导数节点同步修改：

- `Yang-Mills 理论.md` 的下一页、`used_by` 和正文预告已改为真实链接；
- `规范对称性.md`、`联络.md`、`协变导数.md`、`联络如何定义协变导数.md` 和 `Dirac 场.md` 建立真实回链，定向复验合计 6/6；
- `电势.md` 原有 `used_by` 链接在新页创建后已成为可解析链接；
- 上一页 Yang-Mills 和总路线均可点击；下一页“Wilson 线与 Wilson 圈”尚未创建，保留普通文本而不制造断链；
- `弦理论与大模型跨学科关系图谱.md` 将该节点显式纳入群作用、表示和协变/等变语言的共享结构，并新增 $D_\mu\ne$ 自动微分算子、$A_\mu\ne$ 可学习位置编码的禁止误连。

独立终审与结构验收：

- 独立终审：**Critical 0**；伴随表示、对偶表示、规范变换、张量积 Leibniz、$U(1)$ 符号和 8 道答案全部 Pass；
- YAML：通过；tags 4/4；prerequisites 6/6；
- 页面 Obsidian 链接 27 个，缺失 0；未来链接 0；
- 学习导航 3/3；练习 8/8，答案 8/8；控制字符 0；
- 定向回链 6/6，`git diff --check` 通过。

新增：`弦理论/物理学/Wilson 线与 Wilson 圈.md`。

该页已覆盖：

- 从 $\dot z^\mu D_\mu\psi=0$ 推导开放 Wilson 线的初值微分方程和路径排序指数；
- Dyson 展开、开放 Wilson 线的双端规范协变变换、端点物质场组合；
- 路径拼接、反向路径、幺正表示下的逆与 Hermitian 共轭；
- 闭合 holonomy 的共轭变换与取迹 Wilson 圈的规范不变性；
- 表示依赖、归一化、Abelian 极限和 Aharonov-Bohm 全局相位；
- 以线性尺度 $\ell$ 和有向面积双向量定义的小回路展开，余项从 $O(\ell^3)$ 开始；
- full holonomy 与 restricted holonomy 的区别、曲率和全局拓扑的分工；
- 非 Abelian Stokes 公式不能简化为普通面积指数；
- Euclidean 大矩形圈、归一化 $w_R=\mathcal W_R/\dim R$、静态势和面积律；
- Chan-Paton、D-brane 世界体、紧致维 Wilson 线、T 对偶和杂化弦背景；
- 10 道练习及答案。

Wilson 线与 Wilson 圈节点同步修改：

- `规范协变导数.md` 的下一页、`used_by` 和正文关系已改为真实链接；
- `Yang-Mills 理论.md`、`联络.md`、`曲率.md`、`群表示.md`、`Lie 群与 Lie 代数的对应.md` 和 `Maxwell 场量子化.md` 建立真实回链；
- 加上跨学科图谱，定向回链复验合计 8/8；
- `弦理论与大模型跨学科关系图谱.md` 新增 Wilson 线、路径排序和 holonomy 的禁止误连：Wilson 线不等于 token/attention/计算图路径，路径排序不等于位置编码或自回归顺序，holonomy 不等于参数更新或隐藏状态，面积律不等于模型规模定律，闭合路径取迹不等于 attention 权重归一化；
- 上一页“规范协变导数”和总路线可点击；下一页“规范固定”尚未创建，继续保留普通文本预告，不制造未来断链。

独立终审与结构验收：

- 独立终审：**Critical 0**；初值方程、Dyson 展开、规范变换、路径拼接、反向路径、幺正性、闭合 holonomy、小回路展开、full/restricted holonomy、非 Abelian Stokes、静态势、面积律、弦理论关系和 10 道答案全部 Pass；
- YAML：通过；tags 4/4；prerequisites 6/6；
- 页面 Obsidian 链接实例 22 个、唯一目标 10 个，缺失 0；未来链接 0；
- 学习导航：上一页、普通文本后继预告和总路线均通过；练习 10/10，答案 10/10；控制字符 0；
- 定向回链 8/8，`git diff --check` 通过。

新增：`弦理论/物理学/规范固定.md`。

该页已覆盖：

- 规范轨道、物理配置空间 $\mathcal A/\mathcal G$ 和规范切片；
- 二次算符 $K^{\mu\nu}=\eta^{\mu\nu}\Box-\partial^\mu\partial^\nu$ 的零方向与不可逆原因；
- Lorenz 规范、线性协变规范族（Feynman/Landau 极限）、Coulomb 规范和 axial 规范的定义与残余条件；
- Minkowski 作用量中的负号规范固定项与 Euclidean 作用量正号；
- 一般协变规范传播子，与 `传播子.md` 的 $i\varepsilon$ 处方一致；
- FP 插入恒等式的思想、Abelian $\Box$ 与非 Abelian $D_\mu^{\mathrm{adj}}$ 的差别；
- 残余规范、边界条件、Gribov copies 的适用边界；
- 目标时空 Yang-Mills 规范固定、世界面 Diff×Weyl、$bc$ 鬼和 $\beta\gamma$ 超鬼的严格区分；
- 10 道练习及答案。

规范固定节点同步修改：

- `Wilson 线与 Wilson 圈.md` 的下一页从普通文本改为真实链接；
- `Yang-Mills 理论.md` 的“规范固定（待创建）”和量子化预告改为真实链接，仍保留未创建 FP/BRST 为普通文本；
- `路径积分.md`、`传播子.md`、`Feynman 图.md`、`圈展开.md` 新增真实回链；
- `规范对称性.md` 和 `Maxwell 场量子化.md` 原有断链在创建后自动解析；
- `弦理论与大模型跨学科关系图谱.md` 在禁止误连区将规范固定改为真实链接；
- 上一页 Wilson 和总路线均可点击；下一页 Faddeev-Popov 行列式尚未创建，保留普通文本预告。

独立终审与结构验收：

- 独立终审：**Critical 0**；公式、规范定义、传播子、FP/Gribov 边界、10 道答案全部 Pass；
- YAML：通过；tags 4/4；prerequisites 5/5；
- 页面 Obsidian 链接实例 30 个、唯一目标 13 个，缺失 0；未来链接 0；
- 学习导航：上一页、普通文本后继预告和总路线均通过；练习 10/10，答案 10/10；控制字符 0；
- 定向回链 9/9，`git diff --check` 通过。

新增：`弦理论/物理学/Faddeev-Popov 行列式.md`。

该页已覆盖：

- FP 算符的功能 kernel 定义；
- 本路线 $D_\mu=\partial_\mu-igA_\mu$、$U=e^{ig\alpha}$ 约定下的伴随协变导数分量符号；
- Abelian Lorenz 规范 $M=\Box$ 与 non-Abelian $M^{ab}=\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}$ 的完整推导；
- 有限维 delta 变量变换、行列式为何在分子；
- $|\det M|$ 与局部有向 $\det M$ 的适用边界；
- 规范群体积 $\operatorname{Vol}(\mathcal G)$ 的形式分离及其前提；
- determinant 的局部轨道性质、零模、残余规范和多重交点；
- Gribov copies，以及仅在适当 Euclidean Hermitian 设定中用最低特征值描述第一 Gribov horizon 的边界；
- Abelian 行列式场无关但仍可有零模，non-Abelian 行列式依赖规范场；
- Minkowski/Euclidean 算符约定和后续鬼作用量符号的分工；
- 目标时空 Yang-Mills FP 行列式与世界面 Diff×Weyl FP 行列式的共同结构和严格区别；
- 10 道练习及答案。

Faddeev-Popov 行列式节点同步修改：

- `规范固定.md` 的下一页从普通文本改为真实链接；
- `Yang-Mills 理论.md` 的量子化预告把 FP 行列式改为真实链接，并仅保留鬼场和 BRST 为未创建普通文本；
- `路径积分.md`、`圈展开.md`、`群作用.md`、`Maxwell 场量子化.md` 和 `Grassmann 变量.md` 建立真实回链；
- `弦理论与大模型跨学科关系图谱.md` 新增 FP 行列式不等于神经网络 Jacobian、规范群体积不等于参数空间体积、Gribov horizon 不等于损失景观鞍点的禁止误连；
- 上一页“规范固定”和总路线可点击；下一页“Faddeev-Popov 鬼场”尚未创建，保留普通文本预告。

独立终审与结构验收：

- 独立终审：**Critical 0**；11 项检查全部 Pass；
- YAML：通过；tags 4/4；prerequisites 4/4；
- 页面 Obsidian 链接实例 17 个、唯一目标 7 个，缺失 0；未来链接 0；
- 学习导航：上一页、普通文本后继预告和总路线均通过；练习 10/10，答案 10/10；控制字符 0；
- 定向回链 8/8，`git diff --check` 通过。

正规化与重整化节点同步修改：

- `紫外发散与红外发散.md` 的 `used_by` 和关系区已指向本节点；
- `圈展开.md` 删除“正规化与重整化尚未建立”的过时说明并建立真实链接；
- ML 正则化两页和跨学科总图谱均已补充本节点的同名异义导航。

新增：`弦理论/物理学/Faddeev-Popov 鬼场.md`。

该页已覆盖：

- 行列式 $\det M$ 的 Grassmann 指数化，引入 $c^a,\bar c^a$ 作为 Grassmann 奇 Lorentz 标量；
- 鬼场性质：伴随表示、不作为物理外态、ghost number $\operatorname{gh}(c)=+1,\operatorname{gh}(\bar c)=-1$、不构成自旋—统计定理违反；
- Minkowski 作用量 $S_{\mathrm{gh}}=\int \bar c\,\partial D c$ 与 Euclidean $S_{E,\mathrm{gh}}=-\int \bar c\,\partial D c$；
- 自由二次核 $M_0(k)=-\delta^{ab}k^2$，传播子 $\Delta^{ab}(k)=-i\delta^{ab}/(k^2+i0)$，并说明 $M=-\partial D$ 约定常见 $+i$ 符号的来源；
- ghost–gauge 顶点，$e^{-ip\cdot x}$ 约定、全流入动量下 $V_\mu^{abc}=-g f^{abc}q_\mu$，并明确整体符号依赖 Fourier/动量流向约定；
- Abelian 鬼自由解耦、non-Abelian 鬼依赖 $A_\mu$ 产生 ghost–gauge 顶点；
- 鬼圈图作用：组织在 Slavnov–Taylor 恒等式和完整图之和层面，不是逐图一一抵消；
- 世界面对比表：$bc$ 为 anticommuting 一阶系统，$\beta\gamma$ 为 commuting/bosonic 一阶系统，Berezinian 因子，统计和来源不同，不可机械等同；
- BRST 预告：$c^a$ 替代规范参数成为动态场，BRST 微分 $s$ 由全局 Grassmann 奇参数生成，$s^2=0$，不把 $c^a$ 称为 BRST 变换参数；
- 大模型禁止误连：鬼场 ≠ 隐变量/辅助 token/负样本权重/辅助损失，鬼圈负号 ≠ 损失惩罚项，BRST 微分 ≠ 反向传播；
- 10 道练习及答案。

Faddeev-Popov 鬼场节点同步修改：

- `Faddeev-Popov 行列式.md` 的下一页从普通文本改为真实链接，正文中鬼场引用同步升级；
- `Yang-Mills 理论.md` 的量子化预告把鬼场改为真实链接，仅保留 BRST 为未创建普通文本；
- `Grassmann 变量.md` 的 `used_by` 和关系区中 `[[鬼场]]` 旧链接改为正式路径；
- `路径积分.md`、`圈展开.md`、`Feynman 图.md` 的鬼场普通文本改为真实链接；
- `弦理论与大模型跨学科关系图谱.md` 禁止误连区将鬼场改为真实链接，并细化禁止项；
- `Maxwell 场量子化.md` 和 `模空间.md` 已有真实链接，自动解析。

独立终审与结构验收：

- 独立终审：**Critical 0**；11 项检查全部 Pass；
- YAML：通过；tags 4/4；prerequisites 5/5；used_by 5/5；
- 页面 Obsidian 链接实例 23 个、唯一目标 10 个，缺失 0；未来链接 0；
- 学习导航：上一页真实链接、普通文本 BRST 后继预告和总路线均通过；练习 10/10，答案 10/10；控制字符 0；
- `git diff --check` 通过。

新增：`弦理论/物理学/BRST 对称性.md`。

该页已覆盖：

- 与仓库 $D_\mu=\partial_\mu-igA_\mu$、$(D_\mu^{\mathrm{adj}})^{ab}=\delta^{ab}\partial_\mu+g f^{acb}A_\mu^c$ 一致的 off-shell BRST 变换；
- $sA_\mu^a=(D_\mu^{\mathrm{adj}}c)^a$、$sc^a=-\frac g2f^{abc}c^bc^c$、$s\bar c^a=B^a$、$sB^a=0$；
- 利用 Grassmann 反对易性和 Jacobi 恒等式验证 $s^2A=s^2c=s^2\bar c=s^2B=0$；
- 场强变换 $sF_{\mu\nu}^a=+g f^{abc}F_{\mu\nu}^bc^c$ 与 Yang-Mills 作用量不变性；
- gauge-fixing fermion $\Psi=\bar c^a(G^a-\xi B^a/2)$，并采用 $\mathcal L_{\mathrm{gf+gh}}=-s\Psi$ 精确复现既有的 $-G^2/(2\xi)+\bar cMc$；
- Nakanishi-Lautrup 辅助场的消去，以及 off-shell/on-shell 幂零性的边界；
- BRST-exact 规范固定变化不改变物理量所需的测度、正规化、无反常、边界和全局规范条件；
- Noether BRST 流与荷 $Q$、$Q^2=0$、物理态条件 $Q|\mathrm{phys}\rangle=0$ 和 $\ker Q/\operatorname{im}Q$ 入口；
- Abelian/non-Abelian BRST、Hamilton/BFV-BRST 边界、Yang-Mills 与世界面 BRST 的共同结构和区别；
- 世界面量子 $Q^2=0$ 还要求总中心荷反常消失，RNS $\beta\gamma$ 明确为 commuting/bosonic 超鬼；
- 大模型禁止误连：$s$ ≠ 反向传播、$s^2=0$ ≠ 梯度消失、$Q$ ≠ 优化器、上同调 ≠ 降维、$\Psi$ ≠ 损失函数、$B^a$ ≠ bias/隐变量；
- 10 道练习及答案。

BRST 对称性节点同步修改：

- `Faddeev-Popov 鬼场.md` 的下一页和正文预告改为真实 BRST 链接；
- `Yang-Mills 理论.md` 的量子化预告把 BRST 改为真实链接，并删除“尚未创建”说明；
- `规范固定.md` 的 BRST 物理态条件改为真实链接；
- `规范对称性.md` 的世界面 BRST 普通文本改为真实链接；
- `弦理论与大模型跨学科关系图谱.md` 新增 BRST 专属禁止误连；
- `Poisson 括号.md`、`Maxwell 场量子化.md`、`Grassmann 变量.md`、`Lie 代数.md`、`群作用.md`、`模空间.md` 和路线图的既有链接在页面创建后自动解析。

独立终审与结构验收：

- 独立终审：**Critical 0**；11 项检查全部 Pass；
- YAML：通过；tags 4/4；prerequisites 6/6；used_by 7/7；
- 页面 Obsidian 链接实例 31 个、唯一目标 12 个，缺失 0；未来链接 0；
- 学习导航：上一页真实链接、普通文本 BRST 上同调后继预告和总路线均通过；练习 10/10，答案 10/10；控制字符 0；
- 定向复核确认场强符号为正、$\mathcal L_{\mathrm{gf+gh}}=-s\Psi$、$c^a$ 不是全局参数、$\beta\gamma$ 为 bosonic；
- `git diff --check` 通过。

新增：`弦理论/物理学/BRST 上同调.md`。

该页已覆盖：

- ghost number 分次空间 $\mathcal H=\bigoplus_n\mathcal H^n$ 与 $Q:\mathcal H^n\to\mathcal H^{n+1}$；
- 闭态 $Z^n(Q)$、恰当态 $B^n(Q)$、$\operatorname{im}Q\subseteq\ker Q$ 和 $H^n(Q)=Z^n/B^n$；
- 三维有限基例子中 $H^0(Q)=0$、$H^1(Q)=\operatorname{span}\{[c]\}$；
- Yang-Mills 常用 $\mathcal H_{\mathrm{phys}}\simeq H^0(Q)$ 的限定，以及弦世界面 ghost-number 扇区依鬼真空、开闭弦、相对/绝对上同调和 picture number 而变；
- 不定内积候选空间、$Q^\ddagger=Q$ 假设下恰当态与闭态正交、恰当态零范数，以及正定 Hilbert 空间中处处定义自伴幂零 $Q$ 必为零的边界；
- BRST doublet、收缩同伦 $\{Q,K\}=N$ 和正本征值闭态为恰当态的最小证明；
- quartet mechanism 的适用条件，不把局部/微扰结论夸大为任意相互作用非微扰理论的无条件定理；
- 状态空间 $H^n(Q)$、局域算符 $H^g(s)$ 与模全微分 $H^{g,d}(s\mid d)$ 的严格区分；
- 局域可观测量与 $H^0(s)$ 的条件性关系；
- Wess-Zumino 下降方程、$H^{1,d}(s\mid d)$ 的一致反常候选分类，以及非平凡类不等于具体反常系数必然非零；
- Yang-Mills 与世界面 BRST 上同调的共同骨架和 ghost 系统、中心荷、picture number 等差异；
- 大模型禁止误连：上同调 ≠ 降维，核模像 ≠ quotient embedding，closed/exact ≠ 样本分类，quartet ≠ 剪枝/蒸馏/MoE 路由；
- 10 道练习及答案。

BRST 上同调节点同步修改：

- `BRST 对称性.md` 的下一页、导言和物理态段落改为真实上同调链接；
- `Fock 空间.md`、`场的正则量子化.md`、`Hilbert 空间.md` 的实质性普通文本改为真实链接；
- `Yang-Mills 理论.md` 和 `Faddeev-Popov 鬼场.md` 补真实上同调链接；
- 路线图原有断链在页面创建后自动解析；
- `弦理论与大模型跨学科关系图谱.md` 将 BRST 上同调拆为独立真实链接，并补齐禁止误连边界。

独立终审与结构验收：

- 独立终审：**Critical 0**；11 项检查全部 Pass；
- YAML：通过；tags 4/4；prerequisites 4/4；used_by 7/7；
- 页面 Obsidian 链接实例 26 个、唯一目标 10 个，缺失 0；未来链接 0；
- 学习导航：上一页真实链接、普通文本“量子反常”后继预告和总路线均通过；练习 10/10，答案 10/10；控制字符 0；
- 精确复核有限维例子、正定/不定内积边界和跨学科图谱镜像；
- `git diff --check` 通过。

新增：`弦理论/物理学/量子反常.md`。

该页已覆盖：

- 经典对称、量子有效作用量和不可由允许局域反项消除的反常定义；
- 路径积分测度 Jacobian、Fujikawa 正规化视角，以及测度、三角形图和指标定理之间的关系；
- Ward 恒等式中的接触项与反常项，以及量子 Slavnov-Taylor 恒等式破缺；
- Wess-Zumino 一致性条件、BRST 下降方程和 $H^{1,d}(s\mid d)$ 的局域一致反常分类；
- consistent anomaly、covariant anomaly 与 Bardeen-Zumino 局域多项式的关系；
- 规范反常、全局轴流反常与手征规范反常的严格区分；
- trace/Weyl anomaly、diffeomorphism anomaly 和 local Lorentz anomaly 的边界；
- 局域微扰反常、非微扰全局规范反常与全局对称性 ’t Hooft 反常的区分；
- anomaly polynomial 与 descent 的约定无关结构；
- 标准玻色弦 $c_{\mathrm{tot}}=D-26=0$ 和 RNS 超弦 $c_{\mathrm{tot}}=3D/2-15=0$ 的中心荷账本及适用条件；
- 世界面中心荷消除与目标时空 Green-Schwarz 型机制的层次边界；
- 大模型禁止误连：量子反常不等于模型幻觉、训练异常或数据漂移，Wess-Zumino 条件不等于 KKT 条件，anomaly matching 不等于数据分布匹配，中心荷不等于模型容量；
- 10 道练习及答案。

量子反常节点同步修改：

- `BRST 上同调.md` 的下一页和正文预告改为真实量子反常链接，并在 `used_by` 和“与其他概念的关系”补双向回链；
- `BRST 对称性.md` 的反常边界改为真实量子反常链接，并在 `used_by` 和“与其他概念的关系”补双向回链；
- 路线图原有断链在页面创建后自动解析；
- `弦理论与大模型跨学科关系图谱.md` 新增量子反常专属禁止误连条目；
- 下一节点“手征反常”尚未创建，导航继续使用普通文本预告，未预造 Wiki 断链。

独立终审与结构验收：

- 独立终审：**Critical 0**；物理事实 11 项全部 Pass，双向回链问题修复后独立复核 7/7 Pass；
- YAML：通过；tags 4/4；prerequisites 5/5；used_by 4/4；
- 页面 657 行；Obsidian 链接实例 28 个、唯一目标 13 个，缺失 0；未来“手征反常”Wiki 链接 0；
- 学习导航：上一页真实链接、普通文本“手征反常”后继预告和总路线均通过；练习 10/10，答案 10/10；控制字符 0；
- 精确复核 Wess-Zumino 公式与 Obsidian 双方括号词法冲突，已改为不会产生伪 Wiki 链接的数学写法；
- `BRST 上同调.md`、`BRST 对称性.md`、跨学科图谱和路线图均存在真实量子反常引用；
- `git diff --check` 通过。

新增：`弦理论/物理学/手征反常.md`。

该页已覆盖：

- “手征反常”在全局轴流反常与手征规范反常之间的术语歧义；
- 四维 mostly-minus Minkowski、$\gamma^5=i\gamma^0\gamma^1\gamma^2\gamma^3$、$\epsilon^{0123}=+1$、$D_\mu=\partial_\mu+iqA_\mu$ 和 $\widetilde F^{\mu\nu}=\epsilon^{\mu\nu\rho\sigma}F_{\rho\sigma}/2$ 的完整约定；
- 质量显式破缺 $2im\bar\psi\gamma^5\psi$ 与 Abelian ABJ 量子项的严格区分；
- $F\widetilde F$ 与 $\epsilon FF$ 两种公式之间的因子 2；
- AVV 三角形图、线性发散圈积分、动量路由有限表面项和矢量 Ward 恒等式优先保持；
- Fujikawa Euclidean 热核正规化、费米测度 Jacobian 与 Minkowski Ward 恒等式的联系；
- non-Abelian 轴流反常的结构式，以及二阶指标 $T(R)$ 与手征规范反常三阶对称迹 $d_R^{abc}$ 的区分；
- Adler-Bardeen one-loop exact 的适用边界；
- $F\widetilde F$ 的全微分、边界和非平凡拓扑扇区；
- Dirac 零模、Atiyah-Singer 指标定理、瞬子与 $U(1)_A$ 问题；
- 显式质量破缺、自发手征对称性破缺和量子反常三种机制；
- $\pi^0\to\gamma\gamma$ 的领先低能反常结构，不夸大为完整实验宽度无修正；
- 四维局域手征规范反常、Abelian 立方条件和混合 $U(1)$-引力条件；
- 世界面 Weyl 反常不等于 ABJ 反常，世界面中心荷条件不等于目标时空 Green-Schwarz 机制；
- 大模型禁止误连：手征反常不等于异常检测，轴流不等于 token/梯度流，instanton 不等于优化跳跃，Dirac 零模不等于零梯度或死亡神经元；
- 10 道练习及答案。

手征反常节点同步修改：

- `量子反常.md` 的下一页改为真实手征反常链接，并在 `used_by` 和“与其他概念的关系”补双向回链；
- `Dirac 场.md` 的 `used_by` 补手征反常；该页原有正文关系链接在文件创建后自动解析；
- 路线图原有手征反常断链在页面创建后自动解析；
- `弦理论与大模型跨学科关系图谱.md` 新增手征反常专属禁止误连；
- 下一节点“Weyl 反常”在路线命名空间下尚未创建，导航保持普通文本，不链接旧的 `物理学/Weyl 反常.md` 概览页，也不预造新断链。

独立终审与结构验收：

- 初次独立终审发现 1 个 Critical：Fujikawa 小节误称局域 $\alpha(x)$ 轴变换使无质量经典作用量不变；
- 已修正为 $\delta S=-\int d^4x\,(\partial_\mu\alpha)J_5^\mu$，明确只有常数 $\alpha$ 是经典轴对称，并说明作用量变分与测度 Jacobian 共同进入 Ward 恒等式；
- 独立复核：**Critical 0**，原 Critical 完全关闭，未引入新 Critical；
- YAML：通过；tags 4/4；prerequisites 6/6；used_by 4/4；
- 页面 687 行；Obsidian 链接实例 28 个、唯一目标 10 个，缺失 0；未来“Weyl 反常”Wiki 链接 0；
- 学习导航：上一页真实链接、普通文本“Weyl 反常”后继预告和总路线均通过；练习 10/10，答案 10/10；控制字符 0；
- ABJ 的 $q^2/(8\pi^2)F\widetilde F$ 与 $q^2/(16\pi^2)\epsilon FF$ 因子 2 自洽；局域作用量变分和 Ward 合并逻辑通过；
- `量子反常.md`、`Dirac 场.md`、跨学科图谱和路线图均存在真实手征反常引用；
- `git diff --check` 通过。

新增：`弦理论/物理学/Weyl 反常.md`。

该页已覆盖：

- 二维 Euclidean $Z_E$、$W_E=-\log Z_E$、能动张量、曲率和 Laplacian 的完整约定；
- $\langle T^a{}_a\rangle_E=-(c_L+c_R)R^{(2)}/(48\pi)$ 及非手征情形 $-cR^{(2)}/(24\pi)$；
- 有限 Weyl 变换、Wess-Zumino 泛函和 Polyakov 非局域有效作用量，并明确紧致曲面的常数零模投影；
- 能动张量 OPE、Virasoro 中心扩张与曲背景迹反常由同一中心荷联系；
- $c_L+c_R$ 控制 Weyl 反常、$c_L-c_R$ 控制二维引力反常；
- 反对易 $bc$ 和对易 $\beta\gamma$ 一阶系统中心荷；
- 标准玻色弦 $c_{\mathrm{tot}}=D-26$ 与 RNS $c_{\mathrm{tot}}=3D/2-15$ 的临界维数账本；
- 玻色弦 BRST 幂零还需正规序截距 $a=1$，并收紧 RNS 物质扇区截距与 superghost picture 的边界；
- 一般 $G_{\mu\nu}$、$B_{\mu\nu}$、dilaton 背景中的最低阶 Weyl anomaly coefficients；
- 普通 RG beta 与 Weyl anomaly coefficient 可能相差微分同胚、$B$ 场规范变换、dilaton 改进、冗余算符、场重定义和 scheme；
- 非临界弦、Liouville $c_L=1+6Q^2$、$Q^2=(25-c_m)/6$、linear dilaton 和内部 CFT；
- heterotic 左右扇区逐侧计数，以及中心荷条件不能单独推出完整规范群；
- 世界面 Weyl/引力反常与目标时空迹、规范、引力及 ABJ 反常的层次边界；
- 大模型禁止误连：Weyl scaling 不等于归一化，中心荷不等于模型容量，临界维数不等于 embedding dimension，ghost 不等于辅助 token，sigma-model beta 不等于优化器 beta，Liouville 场不等于网络层；
- 14 道练习及答案。

Weyl 反常节点同步修改：

- `手征反常.md` 的下一页改为真实 Weyl 反常链接，并补 `used_by` 与正文双向关系；
- `量子反常.md`、`能动张量.md`、`度量.md`、`beta 函数.md`、`重整化群.md`、`BRST 对称性.md` 补真实回链；
- `能动张量.md` 和 `度量.md` 原 `[[共形反常]]` 断链改为正式 Weyl 页的别名链接；
- 保留旧 `物理学/Weyl 反常.md`，修正过强说法并明确导向正式路线页；
- `弦理论与大模型跨学科关系图谱.md` 新增 Weyl 反常专属禁止误连；
- 路线图中尚未创建的“反常消除”由 Wiki 断链改为普通文本预告；正式页导航同样不预造后继链接。

独立终审与结构验收：

- 初次独立终审：**Critical 0**；发现 3 个缺失专题页链接、路线图后继断链和 RNS 截距表述精度建议；
- 修复后最终独立复核：**Critical 0，7/7 Pass**，覆盖公式约定、中心荷账本、BRST/RNS 边界、sigma beta 边界、Liouville、链接导航和练习答案；
- YAML：通过；tags 4/4；prerequisites 6/6；used_by 6/6；
- 页面 709 行；Obsidian 链接实例 33 个、唯一目标 11 个，缺失 0；
- 学习导航：上一页真实链接、普通文本“反常消除”后继预告和总路线均通过；页面和路线图未来后继 Wiki 链接均为 0；
- 练习 14/14，答案 14/14；控制字符 0；9 个相关页面均有正式 Weyl 回链；
- `git diff --check` 通过。

新增：`弦理论/物理学/反常消除.md`。

该页已覆盖：

- 将所有右手费米子统一改写为左手 Weyl 场并正确共轭表示与取反 Abelian 电荷的记账方法；
- 四维局域规范反常检查表：简单群三次、$G^2-U(1)$、多 $U(1)$、引力-$U(1)$，含旁观群简并度；
- 标准模型一代的完整算例：$SU(3)^3$、$SU(3)^2Y$、$SU(2)^2Y$、$Y^3$、引力-$Y$ 及 Witten $SU(2)$ 全局反常；
- 超荷归一化边界，区分 $Q=T_3+Y$ 与 $Q=T_3+Y'/2$ 两套表不能混用；
- 局域条件不足以保证完整一致性的论述，以及 Witten $SU(2)$ 一般直积群判据含旁观群简并度；
- anomaly polynomial、两步下降关系，并声明整体符号与倍数依约定；
- Green–Schwarz 机制：反常因子化、$B$ 场补偿、规范不变三形式场强和适用边界；
- anomaly inflow：体加边界总系统规范不变，不表示边界单独无反常；
- 世界面中心荷消除与目标时空反常消除的严格区分；
- RR tadpole、K-theory 挠率荷与 Freed–Witten 条件作为独立层次的一致性约束；
- 六类一致性条件对照表；
- 大模型禁止误连：反常消除不等于模型修复，规范反常相消不等于损失抵消，Green–Schwarz 补偿不等于梯度补偿，anomaly inflow 不等于跨层信息流；
- 16 道练习及答案。

反常消除节点同步修改：

- `Weyl 反常.md` 的下一页改为真实链接，补 `used_by` 和正文关系；
- `手征反常.md`、`量子反常.md` 补真实回链和正文关系；
- `弦理论与大模型跨学科关系图谱.md` 新增反常消除专属禁止误连；
- `物理学/Weyl 反常.md` 旧概览补反常消除导流；
- 路线图第 247 行由普通文本预告改为真实链接，第 370 行旧 Green–Schwarz 断链改为指向正式页的显示名别名链接；
- 后继 `[[二维 Euclidean 场论]]` 已创建，反常消除页导航、`used_by` 和正文边界均已改为真实双向链接。

独立终审与结构验收：

- 初次独立终审：2 Critical；CS H3 控制字符、一般 SU(2) Witten 判据漏旁观群简并度；
- 修复后独立复核：**Critical 0**，三项全部关闭，其余 9 项检查 Pass；
- YAML：通过；tags 4/4；prerequisites 6/6；used_by 5/5；
- 页面 873 行；Obsidian 链接实例 31 个、唯一目标 11 个，缺失 0；
- 学习导航：真实 Weyl 页上一页、普通文本二维 Euclidean 场论预告和总路线均通过；未来后继 Wiki 链接 0；
- 练习 16/16，答案 16/16；控制字符 0；6 个相关页面均有正式反常消除回链；
- `git diff --check` 通过。

### 节点十八：二维 Euclidean 场论（2026-09-09）

创建正式路线页 `弦理论/物理学/二维 Euclidean 场论.md`（971 行），在反常消除之后建立从 Lorentz 量子场论到二维 CFT 计算语言的桥梁。核心约定一次固定：$d^2z=dx\,dy$、$\Delta=4\partial\bar\partial$、$g_{z\bar z}=1/2$、$\Delta\ln|z|^2=4\pi\delta^{(2)}(z)$、$G_0=-(4\pi)^{-1}\ln(\mu^2|z|^2)$、$\langle XX\rangle=-(\alpha'/2)\ln(\mu^2|z-w|^2)$，以及紧致曲面协变 delta 投影方程 $-\Delta_{h,x}G=\delta_h-1/V$。

涵盖：Lorentz→Euclidean Wick 旋转（含 $i\varepsilon$ 和边界条件）、复坐标与 Wirtinger 导数、面积元与度量约定（区分 $dz\,d\bar z$ 与 $dz\wedge d\bar z$）、普通标量与弦坐标两种作用量规范化、Euclidean 生成泛函与关联函数、有质量 Green 函数 $K_0$ 与无质量极限、紧致曲面零模与投影 Green 函数（协变 delta 版本）、OS 反射正性及其应用边界、Euclidean 能动张量变分定义与二维迹 $T^a{}_a=m^2\phi^2$、经典无质量 Weyl 不变、二维共形局部平坦性与全纯结构入口、圆柱平面 $z=e^w$ 映射与径向量子化几何入口、统计物理联系与适用边界、三层分离（局部场论/共形几何/全局世界面）、timelike $X^0$ 的 OS/幺正性边界隔离。

未创建的后继 Wiki 链接保持普通文本，不制造断链；仅做径向量子化入口，不提前展开 OPE、态—算符对应、Witt/Virasoro 代数。

直积协同（主线程串行写，子 Agent 只读）：

- 反常消除页导航改为真实 `[[二维 Euclidean 场论]]`，补 `used_by`，边界文本同步；
- Wick 旋转页修复 `[[Euclidean 场论]]`→`[[二维 Euclidean 场论]]` 断链，补正文关系；
- 跨学科图谱新增二维 Euclidean 场论专属禁止误连 13 条（$S_E$≠损失、$e^{-S_E}$≠softmax、场构型积分≠SGD、Wick 旋转≠复值训练、Euclidean 时间≠训练步数、圆柱—平面映射≠位置编码、径向量子化半径≠网络深度、Green/二点函数≠attention/kernel/embedding、反射正性≠损失非负/安全对齐、红外零模≠零梯度/死亡神经元、质量调节器≠weight decay、共形不变性≠scaling law、共形映射≠LayerNorm）；
- 路径积分、能动张量、Weyl 反常、Green 函数、复分析、共形映射、黎曼曲面、度量八个页面的 `used_by` 和正文关系段全部补上正式二维 Euclidean 场论回链，形成双向导航。

Critical 修复：

1. 紧致曲面 Green 函数由平直 $\delta^{(2)}$ 修正为协变 $\delta_h$，配套投影方程、练习 8/9、答案 8/9 同步修改；
2. 弦 $X^\mu$ 二点函数补充 timelike 分量不满足逐场 OS 反射正性的显式边界说明，将幺正性限定在约束/BRST 物理态空间。

独立终审与结构验收：

- 第一轮独立终审：1 Critical（上述协变 delta），1 Suggestion（timelike $X^0$ 的 OS/幺正性边界需显式隔离）；
- 修复后第二轮独立复核：**Critical 0**；仅保留“下一路线节点尚未创建”的预期 Suggestion，其余全 Pass；
- 971 行，39 个 Wiki 链接实例、16 个唯一目标，缺失 0；控制字符 0；`$$` 154（偶数）、无分隔符冲突；
- frontmatter：prerequisites 6/6、used_by 2/2、tags 5/5、evidence_status 正确；
- 练习 15/15，答案 15/15；导航上一页/下一页/总路线均正确；
- 12 个受修改文件的 `git diff --check` 均通过。

### 节点十九：复坐标与全纯分解（2026-09-09）

创建正式路线页 `弦理论/数学/复坐标与全纯分解.md`（1180 行），在二维 Euclidean 场论固定约定之后系统推导向量、一形式、张量分量在复坐标下的变换规则、局部全纯/反全纯分解及全局边界条件，并将 Lorentz 光锥坐标经 Wick 旋转与两个解析扇区的对应做显式推导。

涵盖：坐标反解与 Wirtinger 导数、坐标一形式与对偶基、向量分量与一形式分量的 Jacobian/逆 Jacobian 系数差异（含全纯坐标变换公式）、度量分量 $g_{z\bar z}=1/2$ 下指标升降（交换 $z\leftrightarrow\bar z$）、$dz\,d\bar z$ / $dz\wedge d\bar z$ / $d^2z$ 的三重区分、Laplacian $\Delta=4\partial\bar\partial$、Cauchy–Riemann 方程的 Wirtinger 形式 $\bar\partial F=0$、调和函数的局部全纯分解 $\phi=f(z)+g(\bar z)$、非单连通区域周期、奇点/源、边界条件、紧致曲面和零模等全局限制、全纯导数字段 $J\equiv\partial\phi$、Lorentz 光锥坐标 $(\sigma^\pm)$ 与 Wick 旋转后 $(\bar z,-z)$ 的对应（含负号显式重定义）、闭弦 $X^\mu=X_L^\mu(z)+X_R^\mu(\bar z)$ 的两扇区与两组振子、开弦边界条件使两扇区退化为一组独立振子的对照、周期/动量/绕数约束、复坐标下对称张量分量 $T_{zz},T_{z\bar z},T_{\bar z\bar z}$、仓库约定下 $T_{zz}=-(\partial\phi)^2$ 和 $T_{z\bar z}=0$、从 $\nabla^aT_{ab}=0$ 经 $g^{z\bar z}=2$ 因子约化导出 $\bar\partial T_{zz}=0$、经典 $(h,\bar h)$ 张量型入口（明确不等同于量子初级场共形权）、$(1,0)/(0,1)$ 微分形式类型分裂、跨学科禁止误连 7 条、20 道练习与答案。

双向关系与图谱串行补齐：

- `二维 Euclidean 场论.md` 前一节点：`used_by` 新增回链、导航下一页改为真实链接、适用边界同步；
- `复分析.md`：`used_by` 与正文关系段新增回链；
- `全纯函数.md`：`used_by` 与正文关系段新增回链，说明正文局部分解向二维场的推广；
- `共形映射.md`：`used_by` 与正文关系段新增回链，说明张量分量变换与 $(h,\bar h)$ 入口；
- `黎曼曲面.md`：`used_by`、全纯/反全纯分解正文段、关系段三处新增回链；
- `Klein-Gordon 场.md`：`used_by` 与正文关系段新增回链，说明 $\partial\bar\partial X=0$ 的二维方程改写；
- `弦理论与大模型跨学科关系图谱.md`：新增专用复坐标反类比行（$z,\bar z$≠左右上下文、扇区≠encoder/decoder/MoE、$\partial\bar\partial\phi=0$≠零梯度、局部分解≠张量/模型分解、$(h,\bar h)$≠hidden dimension/tensor shape、闭弦振子≠双塔网络、monodromy/周期/绕数≠token 循环/位置编码）；
- 全库该节点引用 16 处，双向回链 7/7 页均确认。

独立终审与结构验收：

- 第一轮独立逐式终审：**Critical 0**；3 项 Suggestion（Lorentz→Euclidean 负号显式重定义、开弦边界条件补充、守恒方程公共因子 2 约化说明）、4 项 Nice to have；
- 三项 Suggestion 全部落实并独立聚焦复验通过：**Critical 0**；
- 1180 行，26 个 Wiki 链接实例、15 个唯一目标，缺失 0；控制字符 0；`$$` 212（偶数）；
- frontmatter：prerequisites 4/4、used_by 2/2、tags 5/5、evidence_status 正确；
- 练习 20/20，答案 20/20，编号连续一致；导航上一页可点击，下一页保留普通文本（二维自由玻色子未创建），总路线可点击；
- 未创建后续 Wiki 链接；`git diff --check` 通过。

### 节点二十：二维自由玻色子（2026-09-09）

创建正式路线页 `弦理论/物理学/二维自由玻色子.md`（1014 行），继承 `d^2z=dx\,dy`、$g_{z\bar z}=1/2$、$\Delta=4\partial\bar\partial$ 与 $S_E=(4\pi\alpha')^{-1}\int(\partial_aX)^2$ 的仓库约定，系统建立二维无质量自由玻色子的量子计算入口。

涵盖：作用量变分与 $\Delta X=0$、二次动力学算符及平面对数二点函数、红外尺度和加法常数歧义、对第一/第二插入点求导的符号区分、$\langle\partial X\partial X\rangle=-(\alpha'/2)(z-w)^{-2}$、全纯—反全纯分离点相关与重合接触项、自由场分点正规序及正号反项、度量变分分量 $T_{zz}^{\mathrm{metric}}=-(2\pi\alpha')^{-1}\partial X\cdot\partial X$、CFT 归一化 $T(z)=2\pi T_{zz}^{\mathrm{metric}}=-(1/\alpha'):\!\partial X\cdot\partial X\!:$、$TX$ 与 $T\partial X$ 奇异乘积、$TT$ 单重/双重收缩、单玻色子 $c=1$ 与 $D$ 个坐标场 $c=D$、timelike 指标闭合与物理态空间边界、$J=i\partial X$ 的 $\alpha'/2$ 系数及单位归一化电流、Gaussian 高点函数、常数零模、紧致世界面 $\delta_h-1/V$ 投影、紧致/非紧致目标空间边界、局部短距离/世界面全局/目标空间全局三层区分、跨学科禁止误连 12 条、20 道练习与答案。

双向关系与图谱串行补齐：

- `复坐标与全纯分解.md`：`used_by` 新增本页，导航下一页改为真实链接，并在正文、适用边界和关系段写回量子自由场后继；
- `二维 Euclidean 场论.md`：`used_by`、范围说明、适用边界和关系段新增本页回链；
- `Wick 定理.md`：`used_by` 与关系段新增本页，明确 Gaussian 收缩如何用于分点正规序和 $TT$ 奇异项；
- `场的正则量子化.md` 与 `Green 函数.md`：补齐正文关系回链；
- `传播子.md`、`玻色子.md`、`Klein-Gordon 场.md` 原有 YAML 与正文回链继续有效；
- `弦理论与大模型跨学科关系图谱.md`：新增专用自由玻色子反类比行，禁止把对数二点函数、Gaussian 路径积分、全纯导数、正规序、自收缩、能动张量、中心荷、零模、紧致识别和 $c=D$ 误写为 attention/embedding、参数初始化、causal attention、LayerNorm、训练发散、损失梯度、模型容量、零梯度、tokenization 或网络层数。

独立终审与结构验收：

- 独立逐式终审：**Critical 0、Suggestion 0、Nice-to-have 0**；作用量、Green 方程、所有导数符号、接触项、分点反项、$2\pi$ 归一化链、$TX/T\partial X/TT$、$c=D$、电流归一化、timelike/零模/紧致边界均通过；
- 1014 行，28 个 Wiki 链接实例、12 个唯一目标，目标页缺失 0；控制字符 0；`$$` 142（偶数）；
- frontmatter YAML 可解析；练习 20/20、答案 20/20，编号连续一致；
- 导航上一页可点击，下一页保留普通文本（二维自由费米子未创建），总路线可点击；
- 未创建后续 Wiki 链接；`git diff --check` 通过；
- 扩展检查发现若干前驱旧页原本已有指向更后续未创建路线节点的断链，本节点没有新增这些历史断链，且本节点自身及本轮新增回链目标全部存在。

### 节点二十一：二维自由费米子（2026-09-09）

创建正式路线页 `弦理论/物理学/二维自由费米子.md`（781 行），沿用 `d^2z=dx\,dy` 与 $\bar\partial[1/(z-w)]=\pi\delta^{(2)}(z-w)$，并把作用量系数 $1/(2\pi)$、动力学算符 $K=\bar\partial/\pi$、传播子 $1/(z-w)$ 和 $T(z)=-\tfrac12:\!\psi\partial\psi\!:$ 固定为同一套归一化。

涵盖：Grassmann 路径积分变量、量子场算符和费米粒子态的对象区分；左右手征自由作用量及 Grassmann 变分中分部积分负号与奇变量换序负号相消；一阶动力学算符和简单极点传播子；二点函数交换反对称性；左右手征分离点收缩与重合接触项；费米四点 Wick 配对的 $+,-,+$ 符号；固定字段顺序的分点正规序；$T\psi$ 奇异乘积及 $h=1/2$；$TT$ 四阶极点及实手征 Majorana 费米子 $c=1/2$；两个实场组成复手征费米子并给出 $c=1$；复费米子 $U(1)$ 流 $J=:\!\Psi^\dagger\Psi\!:$ 与单位二阶极点；$D$ 个实世界面费米子 $c_\psi=D/2$；左右中心荷的分别记账；NS/R 自旋结构、Ramond 零模和全局传播子的范围入口；Majorana、Weyl、Dirac 与复费米子辨析；世界面旋量身份和目标时空向量指标的区分；局部短距离、世界面全局和目标时空三层边界；跨学科禁止误连 12 条；20 道练习与答案。

双向关系与图谱串行补齐：

- `二维自由玻色子.md`：`used_by`、导航下一页、事实边界和关系段改为本页真实链接；
- `费米子.md`：`used_by` 与关系段新增本页，说明反对易统计如何落实为二维自由 CFT 的简单极点、能动张量和中心荷；
- `Grassmann 变量.md`：`used_by` 与关系段新增本页，说明 Grassmann 奇场、换序负号和一阶动力学算符的使用；
- `Dirac 场.md` 原有 YAML 与正文回链继续有效；
- `二维 Euclidean 场论.md`、`复坐标与全纯分解.md`、`Wick 定理.md` 与 `传播子.md` 作为已存在前驱由本页链接，不新增错误后继占位；
- `弦理论与大模型跨学科关系图谱.md`：新增专用自由费米子反类比行，禁止把 Grassmann 反对易、费米换序负号、Pauli 不相容、简单极点、左右手征、NS/R、Ramond 零模、中心荷、费米 Wick 符号和自旋结构误写为负权重、损失惩罚、token 去重、attention、上下文方向、训练模式、零梯度、模型容量、attention mask 或 tensor shape。

独立终审与结构验收：

- 独立逐式终审：**Critical 0、Suggestion 0、Nice-to-have 0**；作用量—动力学算符—传播子—能动张量归一化闭环、Grassmann 变分与 Wick 符号、分点反项、$T\psi$、$TT$、$c=1/2$、$c=D/2$、复费米子 $U(1)$ 流及局部/全局边界全部通过；
- 781 行，25 个 Wiki 链接实例、11 个唯一目标，目标页缺失 0；控制字符 0；`$$` 100（偶数）；
- frontmatter YAML 可解析；练习 20/20、答案 20/20，编号连续一致；
- 导航上一页可点击，下一页“算符乘积展开”保持普通文本，因为目标文件尚未创建；总路线可点击；
- 未预造“算符乘积展开”或“正规序”Wiki 链接；`git diff --check` 通过。

### 节点二十二：算符乘积展开（2026-09-09）

创建正式路线页 `弦理论/物理学/算符乘积展开.md`（1040 行），沿用 $d^2z=dx\,dy$、$\bar\partial[1/(z-w)]=\pi\delta^{(2)}(z-w)$，并在全页约定中固定 $T_X=-(1/\alpha'):\!\partial X\cdot\partial X\!:$ 和 $T_\psi=-\frac12:\!\psi\partial\psi\!:$ 两套归一化。

涵盖：一般 OPE 结构式 $\sum_k C_{AB}{}^k(z-w,\bar z-\bar w)\mathcal O_k(w,\bar w)$ 与相关函数语境；展开中心及中心切换对导数项的影响；完整 OPE 与 $\sim$ 奇异部分的三重区分；正则 OPE 不为零的边界；Laurent 负幂与对数奇异性共存；围道积分只看简单极点的留数；极点阶数与发散因果的区分；径向排序含费米分次符号入口；自由玻色子单导数正负号来自不同求导变量、双导数二阶极点、$\partial X\bar\partial X$ 分离点；自由费米子简单极点与交换反对称性、费米四点 Wick $+,-,+$ 符号；Wick 收缩生成 OPE 的六步算法；Taylor 展开产生导数项的机制；$T_X X$、$T_X\partial X$、$T_\psi\psi$ 三个示例；$T_XT_X$ 双重收缩与单重收缩及 $c=D$、$T_\psi T_\psi$ 及 $c=1/2$；一般 $TT$ OPE 标准形式与中心荷定义；$c$ 与 $\bar c$ 分扇区记账；接触项不会总显示在分离点 OPE 中；局部 OPE 与全局数据的分层清单；OPE 结合一致性入口；Weyl 反常与平面 $TT$ 的区别；正规序与 OPE 的互补关系；跨学科禁止误连 12 条；20 道练习与答案。

双向关系与图谱串行补齐：

- `二维自由费米子.md`：`used_by`、导航下一页、事实边界和关系段改为本页真实链接；
- `二维自由玻色子.md`：`used_by` 与关系段新增本页；
- `Weyl 反常.md`：`used_by` 与关系段新增本页，说明平面 $TT$ OPE 与曲背景迹反常共享中心荷但不相等；
- `弦理论与大模型跨学科关系图谱.md`：新增专用 OPE 反类比行，禁止把 OPE 极点、算符基、短距离极限、收敛域、Laurent 负幂、Wick 收缩、单重/双重收缩、围道积分、结合一致性和 OPE 因子化误写为 attention、token vocabulary、训练后期、context window、负权重、attention mask、多头注意力、top-k、Transformer 层组合或低秩分解；
- `Wick 定理.md`、`Laurent 级数.md`、`Cauchy 积分公式.md`、`留数定理.md` 和路线图早已预置本页链接，创建后自动成为有效双链。

独立终审与结构验收：

- 独立逐式终审：**Critical 0、Suggestion 0、Nice-to-have 0**；一般 OPE 定义、相关函数语境、展开中心、收敛域与径向排序；完整 OPE 与 $\sim$ 区分；Laurent/围道/留数；玻色单导数正负号、$\partial X\partial X$、费米简单极点与 $+,-,+$；Wick 收缩与 Taylor 展开算法；$T_X$、$T_\psi$ 归一化；$T_X X$、$T_X\partial X$、$T_\psi\psi$、玻色/费米 $TT$ OPE 及 $c=D$/$c=1/2$；接触项、左右中心荷、局部/全局边界；全部未越界替代正规序/Ward/共形权/径向量子化/态算符对应/Virasoro；
- 1040 行，30 个 Wiki 链接实例、12 个唯一目标，目标页缺失 0；控制字符 0；`$$` 144（偶数）；
- frontmatter YAML 可解析；练习 20/20、答案 20/20，编号连续一致；
- 导航上一页可点击，下一页“正规序”保持普通文本，因为目标文件尚未创建；总路线可点击；
- 未预造“正规序”Wiki 链接；`git diff --check` 通过。

## 最终复验结果

2026-09-07 完成所有修改后的全量回归检查：

- prerequisites 依赖图：188 节点、399 条边、缺失 0、歧义 0、环 0、逆层级 0、跨目录公式 83（公式页→其他 76，其他→公式页 7）、文字基础要求 4。**全部通过。**
- 全库链接与结构：188 文件、1054 个 Obsidian 链接、断链 0、歧义 0、理论导航缺失 0、公式答案缺失 0、控制字符 0、占位符 0。**全部通过。**
- Python 代码语法：9/9 通过 `compile` 语法检查。**全部通过。**
- 参考资料总索引：分类为第 9 节（教材与正式标准）和第 10 节（官方软件与 API 文档），无重复 URL、无 localhost 链接。**通过。**
- 项目 01（感知机）：NumPy 1.26.4 实际运行通过，4 轮收敛，predictions `[0,0,0,1]`。**端到端通过。**
- 项目 02–07：因 torch/torchvision/peft/datasets/faiss/gradio 缺包、Hugging Face API 不可达、无 Ollama 模型服务或权重，**未端到端运行，已如实记录阻塞原因。**

## 当前工作区状态

- 父项目 `/home/admin/github/cnyarx/xian` 是 Git 仓库（remote `git@github.com:cnyarx/xian.git`）；
- 当前分支：master；
- 2026-09-09 完成算符乘积展开节点后的精确 `git status --porcelain=v1 -z` 统计为 101 项：74 个已跟踪修改、27 个未跟踪文件；
- 27 个未跟踪文件为：
  1. `弦理论/弦理论核心思维模型与争议.md`；
  2. `弦理论/数学/复坐标与全纯分解.md`；
  3. `弦理论/物理学/BRST 上同调.md`；
  4. `弦理论/物理学/BRST 对称性.md`；
  5. `弦理论/物理学/Faddeev-Popov 行列式.md`；
  6. `弦理论/物理学/Faddeev-Popov 鬼场.md`；
  7. `弦理论/物理学/Feynman 图.md`；
  8. `弦理论/物理学/Weyl 反常.md`；
  9. `弦理论/物理学/Wilson 线与 Wilson 圈.md`；
  10. `弦理论/物理学/Yang-Mills 理论.md`；
  11. `弦理论/物理学/beta 函数.md`；
  12. `弦理论/物理学/二维 Euclidean 场论.md`；
  13. `弦理论/物理学/二维自由玻色子.md`；
  14. `弦理论/物理学/二维自由费米子.md`；
  15. `弦理论/物理学/反常消除.md`；
  16. `弦理论/物理学/圈展开.md`；
  17. `弦理论/物理学/手征反常.md`；
  18. `弦理论/物理学/有效场论.md`；
  19. `弦理论/物理学/正规化与重整化.md`；
  20. `弦理论/物理学/生成泛函.md`；
  21. `弦理论/物理学/紫外发散与红外发散.md`；
  22. `弦理论/物理学/规范协变导数.md`；
  23. `弦理论/物理学/规范固定.md`；
  24. `弦理论/物理学/重整化群.md`；
  25. `弦理论/物理学/量子反常.md`；
  26. `弦理论/物理学/算符乘积展开.md`；
  27. `弦理论与大模型跨学科关系图谱.md`；
- 未经用户明确要求，未执行 git add、commit 或 push。

## 持续边界

弦理论教程继续按 `弦理论/弦理论完整学习路线图.md` 推进。当前稳定节点为"算符乘积展开"，下一节点为阶段 4 的"正规序"。`弦理论/物理学/算符乘积展开.md` 已创建并通过独立逐式终审，最终 **Critical 0、Suggestion 0、Nice-to-have 0**；其上一页已与二维自由费米子形成双向导航，数学前驱、自由场前驱、Weyl 反常和跨学科图谱已经同步。正式页导航中的下一节点继续保持普通文本预告，因为 `弦理论/物理学/正规序.md` 当前尚未创建；创建后应立即把本页下一页改为真实 Wiki 链接，并同步新页上一页回链、本页 `used_by`、Wick 定理、二维自由玻色子、二维自由费米子等前驱关系和跨学科图谱。后续应按路线图分别建立正规序、Ward 恒等式、初级场与后裔场、共形权、径向量子化、态—算符对应及 Witt/Virasoro 结构；不得因为本页已使用自由理论正规序记号、径向排序入口、权重结构预告和 $TT$ OPE，就跳过这些独立节点。

交付优先级：首先保证概念内容和说明正确，其次保证前驱、后继与相关概念关系准确；每个节点都必须主动检查数学、物理学、弦理论与大模型之间的真实交叉点。跨学科关系必须显式写入 `弦理论与大模型跨学科关系图谱.md`，并尽量在两端概念页形成双向导航；类比必须同时注明共同结构、证据范围和禁止等价化边界。

第二批跨学科双向写回已完成。后续新增关系仍应只连接正文真实出现的概念，并继续区分：数学对象直接相同、共享结构但不等价、同名异义和禁止误连。

本交接文档中“项目实际运行与环境边界”的完整清单（项目 01–07 的依赖、网络和模型服务阻塞）仍是当前唯一可验证的端到端边界，后续接手即可据此判断哪些项目需要补环境。

## 写作与验收规则

- 只解释正文真实出现的重要概念，不能把局部公式符号或延伸知识伪装成正文概念；
- 专业概念首次出现时优先给中文，并保留必要英文原名；
- 类比必须说明边界，不能当证明；
- 定量结论必须写实验条件或删除无依据的固定数字；
- 公式必须检查形状、定义域、求导变量、计数口径和单位；
- 外部模型 ID、revision、URL、许可证不得猜测；
- 失败、超时、缺依赖和未验证必须如实记录；
- 所有写操作由主线程串行完成，子 Agent 只做只读审查；
- 不要修改 `.qwen/tmp` 中的临时抽取文件作为最终实现。

## 结构重组记录（2026-09-09，经用户确认执行）

本次重组只动桥接层与链接路径，未改动任何正式路线节点的正文内容（`弦理论/物理学/Weyl 反常.md` 除外，见下）。

### 已执行的变更

1. **桥接层铺平**：根目录旧命名空间 `数学/`(8)、`物理学/`(4)、`计算机学/`(9) 共 21 个跨学科概览页全部移动到仓库根目录，三个空目录已删除。学科归属改由 frontmatter tags 标识（原有 `数学`/`物理学`/`计算机学` tag 保留），并为根目录全部 24 个图谱层文件（21 个概览页 + 3 篇跨学科文档）统一新增 `跨学科` tag。
2. **Weyl 反常合并**：删除旧概览页 `物理学/Weyl 反常.md`（43 行），其独有内容已并入正式页 `弦理论/物理学/Weyl 反常.md`：别名（缩放反常、世界面缩放对称性失效）入 aliases；坐标网格直观类比入"Weyl 反常"小节并保留 `[[世界面]]` 链接；图谱层关联（临界维数、中心荷、对称性与不变量）入"与其他概念的关系"；来源 `[[为什么标准超弦理论要求十维]]` 入参考资料。原指向旧概览页的 12 处链接已重定向到正式页。
3. **链接改写**：全库 `[[X]]`、`[[X]]`、`[[X]]` 路径式链接（约 165 处，分布在图谱层内部、`大模型/` 4 个文件和两篇根目录文档）统一改写为纯文件名链接 `[[X]]`。三篇根目录文档的 71 处入链本就是纯文件名形式，移动与否均可解析，未做改动。

### 新约定

- 根目录 `*.md`（带 `跨学科` tag）= 跨学科图谱层；`弦理论/`、`大模型学习教程/`、`大模型/` = 正式命名空间，本次零结构改动。
- 本交接文档此前章节中出现的 `数学/…`、`物理学/…`、`计算机学/…` 路径均为历史记录，现已失效；对应文件在仓库根目录。
- 路线图中 `[[世界面]]`、`[[RNS 超弦理论]]`、`[[临界维数]]`、`[[中心荷]]` 等 23 处链接是**规划中正式节点的预链接**（重组前即未解析），刻意保留不改写，以免把"计划中"误标为"已完成"。**后续创建这些正式节点时，必须按 Weyl 反常模式处理同名根目录概览页：内容并入正式页（不丢失、不重复）、删除概览页、重定向入链，禁止同名两页并存。**
- 预先存在且本次不处理的断链：路线图及各正式页共约 505 处规划节点预链接（如 Ward 恒等式、Virasoro 代数），以及本文档内 4 处历史简写链接（重整化、鬼场、共形反常、Euclidean 场论）。

### 重组后校验（均通过）

- 全库 Wiki 链接扫描（4915 个实例，Obsidian 解析规则：精确路径 / 相对路径 / 后缀匹配 / 唯一文件名）：本次重组造成的断链 **0**；
- 根目录 24 个文件 + 正式 Weyl 页 YAML frontmatter 全部可解析；
- 旧路径残留（wikilink 与纯文本形式）：0；`git diff --check`：通过；
- Git 状态：81 modified / 22 deleted / 49 untracked（deleted = 21 个移动的概览页 + 1 个合并删除的 Weyl 旧页；untracked = 原 28 + 移动后新路径 21）。未执行 git add、commit 或 push。
