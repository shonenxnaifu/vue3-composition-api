<template>
  <div>
    <div>{{ label }}: {{ user.name }}</div>
    <div>{{ description }}</div>
    <button @click="submit">Submit</button>
    <hr/>
    <slot/>
  </div>
</template>

<script>
import {ref, toRefs, computed, onMounted} from 'vue'
export default {
  name: "UserComponent",
  props: {
    label: {
      type: String,
      default: ""
    },
    user: {
      type: Object,
      default: () => {}
    }
  },
  setup(props, { attrs, slots, emit}) {
    const message = ref("ini adalah component")
    const { label, user } = toRefs(props)
    const description = computed(() => {
      return `${label.value}: ${user.value.name}`
    })

    onMounted(() => {
      console.log(attrs)
      console.log(slots)
    })

    const submit = () => {
      emit("submit", "emit dari user component")
    }

    console.log(user.value.name)

    return { description, submit }
  }
}
</script>

<style scoped>

</style>
