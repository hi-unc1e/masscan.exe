# MASSCAN 中文版， Windows编译说明

在编译时先后遇到报大量错误【第一处】跟报错 `LNK2019`的问题【第二处】， 参考以下链接，成功解决问题。
- 问题一：https://github.com/robertdavidgraham/masscan/issues/417
- 问题二：https://github.com/robertdavidgraham/masscan/issues/426

感谢 @zxibang  @kouzhudong  两位的解答，经过调试终于完美解决报错LNK2019的问题。具体步骤如下：

0. 克隆 https://github.com/robertdavidgraham/masscan 到本地
1. 在`masscan\vs10\masscan.vcxproj`中对应位置，分别添加`<ClCompile` Include="..\src\misc-rstfilter.c" />`、`<ClInclude Include="..\src\misc-rstfilter.h" />`
2. 在`masscan\vs10\masscan.vcxproj.filters`中对应位置，分别添加`<ClCompile Include="..\src\misc-rstfilter.c">
      <Filter>Source Files\misc</Filter>
    </ClCompile>` 及  `<ClCompile Include="..\src\misc-rstfilter.h">
      <Filter>Source Files\misc</Filter>
    </ClCompile>`
3. 重新生成，即可编译成功。

![image](https://user-images.githubusercontent.com/67778054/99552800-63ec7080-29f8-11eb-88d5-896d844d6ecf.png)

另外，如果不想麻烦，你可以直接本库中的源代码，在VS中自己编译一遍即可。

# MASSCAN: Mass IP port scanner

This is an Internet-scale port scanner. It can scan the entire Internet
in under 6 minutes, transmitting 10 million packets per second,
from a single machine.

