<template>
  <div class="container">
    <div class="card">
      <h1>Vue Composition Api</h1>
      <small>data, computed, methods, watch</small>
      <hr>
      <p>Название: <strong>{{ name }}</strong></p>
      <p>Версия: <strong>{{ version }}</strong></p>

      <button class="btn" @click="change">Изменить</button>
    </div>
  </div>
</template>

<script>
import { ref, reactive, toRefs, isRef, isReactive } from 'vue'
export default {
  setup() {
    const name = ref('VueJS')
    const version = ref(3)

    // console.log(isRef(name)) //true
    // console.log(isRef(version.value)) //false

    const framework = reactive({
      name: 'VueJS',
      version: 3
    })

    // console.log(isReactive(framework)) //true
    // console.log(isReactive(framework.name)) //false

    function changeInfo() {
      name.value = 'Vue JS!'
      version.value = 4
      // framework.name = 'Vue JS!'
      // framework.version = 4
    }

    return {
      // framework,
      // name: framework.name,
      // version: framework.version,
      // ...toRefs(framework),
      name,
      version,
      change: changeInfo
    }
  }
  // data() {
  //   return {
  //     name: 'VueJS',
  //     version: 3
  //   }
  // },
  // methods: {
  //   changeInfo() {
  //     this.name = 'Vue JS!'
  //     this.version = 4
  //   }
  // }
}
</script>