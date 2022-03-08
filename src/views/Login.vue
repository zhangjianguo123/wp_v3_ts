<template>
  <div>此文件不适用ts</div>
  <div>多标签</div>
  <div class="hr">
    <p>画个三角形</p>
  </div>
</template>
<script setup>
let num = 0
function curry(fn, currArgs) {
  return function () {
    let args = [].slice.call(arguments)
    num++
    console.log("这是调用时的参数", args,fn.length, num)

    // 首次调用时，若未提供最后一个参数currArgs，则不用进行args的拼接
    if (currArgs !== undefined) {
      num++
      console.log("undefined", num, currArgs)
      args = args.concat(currArgs);
    }

    // 递归调用
    if (args.length < fn.length) {
      num++
      console.log("<<<<", num, args)
      return curry(fn, args);
    }
    num++
    console.log("递归出口",num)
    // 递归出口
    return fn.apply(null, args);
  }
}

function fn(a, b, c) {
  console.log('打印this、', this)
  return a + b + c
}

let newFun = curry(fn)
console.log(newFun(1,)(2,56))
</script>
<style lang="less">
.hr {
  background-color: pink;

  p {
    font-size: 20px;
    font-weight: 700;
  }
}
</style>