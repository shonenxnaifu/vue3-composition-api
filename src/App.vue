<template>
  <div>Count: {{ nilai }}</div>
  <button @click="add">Add</button>
  <div>Result: {{ result }}</div>
</template>

<script>
import { ref, reactive, toRefs, computed, watchEffect, watch } from 'vue'
export default {
  setup() {
    const counter = reactive({
      nilai: 0,
      foo: 'bar'
    })

    const num1 = ref(1)
    const num2 = ref(2)

    const addNum = ref(1)

    const add = () => {
      result.value = 5
      // counter.nilai++
      num1.value++
      num2.value++
    }

    const result = computed({
      get: () => counter.nilai + addNum.value,
      set: val => addNum.value = val
    })

    // watchEffect(() => {
    //   console.log(counter.nilai)
    // }, {
    //       onTrigger(e) {
    //         console.log(e)
    //       },
    //       onTrack(e) {
    //             console.log(e)
    //       }
    //     }
    // )

    // watch(num1, (after, before) => {
    //   console.log(num1.value)
    //   console.log(after)
    //   console.log(before)
    // })

    // watch(() => counter.nilai, (current, before) => {
    //   console.log(counter.nilai)
    //   console.log(current)
    //   console.log(before)
    // })

    watch([num1, num2], (current, before) => {
        console.log(num1.value)
        console.log(num2.value)
      })


    return {
      ...toRefs(counter),
      add,
      result
    }
  }
}
</script>
