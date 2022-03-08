<template>
  <div>此文件不适用ts</div>
  <div>多标签</div>
  <div class="hr">
    <p>画个三角形{{b}}</p>
  </div>
</template>
<script setup>

function newFn(x) {
  console.log('newFn', x)
  return function (y) {
    return x + y
  }
}
let b = newFn(3)
console.log('b', b)
let c = b(2)
console.log('c', c, b(54))
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