---
layout: post
title: "内部收益率"
date: 2021-10-07 17:46
---

#### **计算收益率**

对于一笔固定的投资计算收益率很简单：

$$ C*{n} = C*{0}(1+r)^{n} $$

- r - 收益率
- C - 现金流（Cash Flow）

但是对于多次出入金的情况，则不能使用这种方式计算收益率。于是有了 IRR 和 XIRR 等算法。

#### **Time value of money**

同一笔钱，比如 \$1,000，在当下的价值与其在未来的价值是不同的，一般来说当下的钱价值更高，因为可以立即进行投资升值。

如果现在有收益率为 5% 的投资渠道，这笔钱一年后就是 \$1,050。

反之一年后的 \$1,000 折算到当下则只有

$$ \frac{\$1,000}{1.05} = \$952.38 $$

![Economics_of_climate_change_chapter3_discounting_curves.png](/assets/Economics_of_climate_change_chapter3_discounting_curves.png)

#### **NPV**

Net Present Value 是将未来的现金流折算成当前的现金流，加起来成为净现值。

$$ NPV(r,N) = \sum^{N}_{t=0}\frac{C_{t}}{(1+r)^t} $$

- r - 折扣率
- t - 时间
- $$C_{t}$$ - 现金流

#### **IRR**

Internal Rate of Return 是 NPV 为 0 时的折扣率，即

$$ NPV(r,N) = \sum^{N}_{t=0}\frac{C_{t}}{(1+r)^t} = 0 $$

如果上述公式的求和序列只有 $$t=0$$ 和 $$t=n$$ 两项，则退化为一开始提到的只有一笔固定投资的情况。

#### **XIRR**

Extended Internal Rate of Return 与 IRR 的区别在于：

IRR 中的时间单位为 **年**

而 XIRR 则可以更细地切割为 **日**，公式中的时间 $$t$$ 写为分数即可。

#### **参考资料**

1. <https://www.ablebits.com/office-addins-blog/2019/07/24/excel-xirr-nonperiodic-cash-flows/>

2. <https://en.wikipedia.org/wiki/Net_present_value>

3. <https://en.wikipedia.org/wiki/Internal_rate_of_return>
