<script setup>
import { ref, nextTick, onUpdated } from 'vue'
import { formatDate } from '../utils/'
const count = ref(0)
// 文本插值
const msg = ref('Hello')
// 原始HTML
// const rawHtml = ref('<span style="color: red">This should be red.</span>')
const dynamicId = ref('dynamic-id')
// 使用JavaScript表达式 调用函数
const date = ref(new Date())

// 指令参数
const url = ref('https://github.com/bubucuo/vue-lemon')

async function increment() {
  count.value++
  await nextTick()
  // 现在 DOM 已经更新了
  count.value++
}

onUpdated(() => {
  console.log('render')

  console.log('toggle', toggle.value)
})

// 复选框
const checked = ref(false)
// 多个复选框
const checkedNames = ref([])
// 单选
const picked = ref('One')
// 下拉框
const selected = ref('')

// 值绑定
const toggle = ref(false)
// 单选按钮
const pick = ref('first')
const first = ref('first')
const second = ref('second')
</script>


<template>
  <div class="counter">
    <h1>This is an counter page</h1>

    <button @click="count++">count is: {{ count }}</button>
    <button @click="increment">next tick: count is: {{ count }}</button>

    <!-- 文本插值 -->
    <h5>Message: {{ msg }}</h5>

    <!-- 原始HTML -->
    <!-- <p>Using text interpolation: {{ rawHtml }}</p> -->
    <!-- <p>Using v-html directive: <span v-html="rawHtml"></span></p> -->

    <!-- Attribute 绑定 -->
    <div v-bind:id="dynamicId"></div>

    <!-- <input type="text" v-bind="msg"> -->

    <!-- 使用JavaScript表达式 -->
    <h5>{{ count + 2 }}</h5>
    <h5>{{ count % 2 ? 'odd' : 'even' }}</h5>
    <h5>{{ msg.split('').reverse().join('') }}</h5>
    <div :id="`list-${count}`">omg</div>

    <!--  调用函数 -->
    <time :title="formatDate(date)" :datetime="date">
      {{ formatDate(date) }}
    </time>

    <!-- 指令参数 -->
    <a :href="url"> github </a>

    <input v-model="msg" placeholder="edit" />
    <textarea v-model="msg" placeholder="add multiple lines"></textarea>

    <!-- 复选框 -->
    <div>
      <input type="checkbox" id="checkbox" v-model="checked" />
      <label for="checkbox">{{ checked }}</label>
    </div>

    <!-- 多个复选框 -->
    <div>Checked names: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
    <label for="jack">Jack</label>

    <input type="checkbox" id="john" value="John" v-model="checkedNames" />
    <label for="john">John</label>

    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
    <label for="mike">Mike</label>

    <div>Picked: {{ picked }}</div>

    <input type="radio" id="one" value="One" v-model="picked" />
    <label for="one">One</label>

    <input type="radio" id="two" value="Two" v-model="picked" />
    <label for="two">Two</label>

    <!-- 下拉框 -->
    <div>Selected: {{ selected }}</div>
    <select v-model="selected">
      <option disabled value="">Please select one</option>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>

    <!-- 值绑定 -->
    <div>值绑定</div>
    <input type="checkbox" v-model="toggle" true-value="yes" false-value="no" />
    <input type="checkbox" v-model="toggle" true-value="really" false-value="oh no" />
    <label for="toggle">{{ toggle }}</label>

    <!-- 单选按钮 -->
    <div>单选按钮</div>
    <input type="radio" v-model="pick" :value="first" />
    <input type="radio" v-model="pick" :value="second" />

    <!-- 在 "change" 事件后同步更新而不是 "input" -->
    <div>修饰符</div>
    <input v-model.lazy="msg" />
  </div>
</template>

<style>
.red {
  color: red;
}
.green {
  color: green;
}
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
