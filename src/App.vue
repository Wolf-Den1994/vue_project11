<template>
  <div class="container">
    <div class="card">
      <h1>Vue Composition Api</h1>
      <small>data, computed, methods, watch</small>
      <hr>

      <div class="form-control">
        <input type="text" ref="textInput">
        <input type="text" v-model="firstName">
      </div>

      <button class="btn" @click="change">Изменить</button>
    </div>

    <framework-info
      :name="name"
      :version="version"
      @change-version="changeVersion"
    ></framework-info>
  </div>
</template>

<script>
import {
  ref,
  reactive,
  toRefs,
  isRef,
  isReactive,
  computed,
  watch,
} from 'vue'
import FrameworkInfo from "@/FrameworkInfo";
export default {
  setup() {
    const name = ref('VueJS')
    const version = ref(3)
    const textInput = ref(null)
    const firstName = ref('')

    // console.log(isRef(name)) //true
    // console.log(isRef(version.value)) //false

    const framework = reactive({
      name: 'VueJS',
      version: 3
    })

    // console.log(isReactive(framework)) //true
    // console.log(isReactive(framework.name)) //false

    // const doubleVersion = computed(() => version.value * 2)

    // watch([doubleVersion, name], (newValues, oldValues) => {
    //   console.log('new', newValues, 'old', oldValues) // new [8, 'Vue JS!'] old [6, 'VueJS']
    // })

    watch(firstName, (newValue, oldValue) => {
      // console.log(newValue) // input.value
    })

    function changeInfo() {
      name.value = 'Vue JS!'
      version.value = 4

      // console.log(textInput.value) // input element
    }

    const changeVersion = (num) => {
      version.value = num
    }

    return {
      name,
      version,
      change: changeInfo,
      textInput,
      firstName,
      changeVersion,
    }
  },
  components: {
    FrameworkInfo
  }
}
</script>