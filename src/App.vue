<template>
  <div>Count: {{ nilai }}</div>
  <button @click="add">Add</button>
  <div>Result: {{ result }}</div>
  <div>{{ temp }}</div>
</template>

<script>
import { ref, reactive, toRefs, computed } from 'vue'
export default {
  setup() {
    let temp = ref('yoiii')
    const counter = reactive({
      nilai: 0
    })

    const addNum = ref(1)

    const add = () => {
      counter.nilai++
    }

    const result = computed(() => counter.nilai + addNum.value)

    return {
      ...toRefs(counter),
      add,
      result,
      temp
    }
  }
}
</script>
