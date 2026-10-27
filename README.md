# compat

**检查工具调用在不同模型上的兼容情况。**

`compat` —— 按模型逐一校验工具模式的兼容性，标出不兼容项

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`compat.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install fosterunix-compat
```

装完直接用命令名调用：

```bash
compat --help
```

也可以不用安装，直接把 `compat.py` 拷走用——它只依赖标准库。

## 为什么需要它

不兼容要指明是模式本身还是模型的限制

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 工具调用兼容矩阵 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python compat.py --file input.txt
python compat.py --text "示例内容"
python compat.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 类型推断基于 AST，动态构造的返回值会标为无法判定。
- 不校验业务语义，只校验结构。

## 跑测试

```bash
python test_compat.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/fosterunix/compat>

---

## 关于作者

fosterunix 做工具调用兼容矩阵相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://fosterunix.github.io>
- 仓库：<https://github.com/fosterunix/compat>

## 许可

MIT，见 [LICENSE](LICENSE)。
