<template>
  <div>Count: {{ nilai }}</div>
  <button @click="add">Add</button>
  <div>Result: {{ result }}</div>
  <UserComponent :label="label" :user="user" class="active"  blablabla="testings" @submit="onSubmit">
    <div>ini slot</div>
    </UserComponent>
  <button @click="changeName">Change</button>
</template>

<script>
import { ref, reactive, toRefs, computed, watchEffect, watch,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  onActivated,
  onDeactivated,
  onErrorCaptured} from 'vue'
import UserComponent from "./components/UserComponent.vue"
export default {
  components: { UserComponent },
  setup() {
    const label = ref("biodata")
    const user = reactive({
      name: "nusendra",
      age: 25
    })
    const counter = reactive({
      nilai: 0,
      foo: 'bar'
    })

    const num1 = ref(1)
    const num2 = ref(2)

    const addNum = ref(1)

    const add = () => {
      result.value = 5
      counter.nilai++
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

    const changeName = () => {
      user.name = "Admin"
    }

    const onSubmit = val => {
      console.log(val)
    }

    return {
      ...toRefs(counter),
      add,
      result,
      label,
      user,
      changeName,
      onSubmit
    }
  }
}
</script>
