---
layout: post
title: 'IRR and XIRR'
date: 2021-10-07 17:46
---

#### **计算收益率**

对于一笔固定的投资计算收益率很简单：

$$ r = \frac{P_{365} - P_{0}}{P_{0}} $$

- P 为现金流（Cash Flow）

但是对于多次出入金的情况，则不能使用这种方式计算收益率。于是有了 IRR 和 XIRR 等算法。

#### **Time value of money**

同一笔钱，比如 \$1,000，在当下的价值与其在未来的价值是不同的，一般来说当下的钱价值更高，因为可以立即进行投资升值。

如果现在有收益率为 5% 的投资渠道，这笔钱一年后就是 \$1,050。

反之一年后的 \$1,000 折算到当下则只有

$$ \frac{\$1,000}{1.05} = \$952.38 $$

![Economics_of_climate_change_chapter3_discounting_curves.png](/assets/irr-and-xirr/Economics_of_climate_change_chapter3_discounting_curves.png)

#### **NPV**

Net Present Value 是将未来的现金流折算成当前的现金流，加总起来成为净现值。

#### **IRR**

Internal Rate of Return

#### **XIRR**

Extended Internal Rate of Return

#### **参考资料**

1. <https://www.ablebits.com/office-addins-blog/2019/07/24/excel-xirr-nonperiodic-cash-flows/>
