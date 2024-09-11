
##### 1、js 小数计算精度丢失
第三方库：
（1）[decimal.js文档](https://mikemcl.github.io/decimal.js) [github地址](https://github.com/MikeMcl/decimal.js) 作者：MikeMcl  6.3k star
（3）[bignumber文档](https://mikemcl.github.io/bignumber.js/)  [github地址](https://github.com/MikeMcl/bignumber.js) 作者：MikeMcl 6.6k star

#####  2、toFixed() 不一定是四舍五入；
```
1.15.toFixed(1) // 1.1， 实际应为1.2

方法1：使用Math.round 解决
/**
 * 四舍五入保留几位小数
 * @param {Number} num 原始数据
 * @param {Number} decimalPlaces 保留几位小数
 */
export function customRound(num, decimalPlaces) {
  const factor = Math.pow(10, decimalPlaces);
  return Math.round(num * factor) / factor;
}
```
```
方法2： 使用 `Intl.NumberFormat`
`Intl.NumberFormat` 是一个内置的 JavaScript 国际化对象，它可以用来格式化数字，包括四舍五入到特定的小数位数。
function customRound(num, decimalPlaces) {
  return new Intl.NumberFormat('en-US', {
    minimumFractionDigits: decimalPlaces,
    maximumFractionDigits: decimalPlaces,
    round: 'halfawayfromzero'
  }).format(num);
}
```

#####  3、console.log('%s ====>>>导出成功', a) %s 为占位符，a的值替换该占位符
