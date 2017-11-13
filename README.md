# 回归测试工具
A regression test tool

Linux下的回归测试工具，用于进行多项回归测试

# 用法

    ./test

运行后，程序自动检索tests目录下的所有测试集，并按顺序依次进行回归测试，并统计测试结果输出passed或failed。

每项回归测试的标准输出结果与错误输出结果均重定向至logs文件夹内。

# 文件夹定义

* *tests*文件夹用于存放测试集

* *logs*文件夹用于存放每个测试集的脚本输出

# 测试集编写方法

每个测试集的测试脚本（以下简称测试脚本）为测试集目录下的 test 文件。

每个测试脚本与回归测试工具之间，通过 tests/result.temp 文件进行通信，如果测试集运行结束后，向 tests/result.temp中写入 1，则表明测试通过，否则，测试不通过。

每个测试脚本可以接收参数（见 tests/01example1 ）。若参数为1，则表明该次运行的是正确代码，输出正确结果（该功能用于校准正确结果）。若没有参数，则表明需要进行回归测试，运行测试代码，并将测试代码的 输出/错误输出 结果重定向至特定文件，并使用diff命令与标准结果进行比对，根据比对结果返回 测试通过/失败 。


