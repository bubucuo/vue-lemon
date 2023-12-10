<script setup>
import { ref, onUpdated } from 'vue'
// 文本插值
const msg = ref('Hello')

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
  <div className="item">修饰符</div>
  <input v-model.lazy="msg" />
  <input v-model.number="age" />
  <input v-model.trim="msg" />
</template>

<style scoped>
.item {
  margin-top: 2rem;
  display: flex;
  position: relative;
}

.details {
  flex: 1;
  margin-left: 1rem;
}
</style>
