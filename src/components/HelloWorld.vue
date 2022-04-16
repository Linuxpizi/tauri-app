<script setup lang="ts">
import { open, DialogFilter, OpenDialogOptions } from '@tauri-apps/api/dialog'
import { ref } from 'vue'
import { NButton, /*NConfigProvider, NInput, NDatePicker, NSpace*/ } from 'naive-ui'
// import { createTheme, inputDark, datePickerDark } from 'naive-ui'
// import { zhCN, dateZhCN } from 'naive-ui'

defineProps<{ msg: string }>()

const count = ref(0)
// const darkTheme = createTheme([inputDark, datePickerDark])

const op = () => {
  const opts: OpenDialogOptions = {
    title: "string",
    filters: [{ name: "pdf name", extensions: ["pdf"] }, { name: "image name", extensions: ["png", "jpg"] }],
    directory: false,
  }
  open(opts).then(console.log)
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <button type="button" @click="count++">count is: {{ count }}</button>
  <NButton type="primary" @click="op">hello</NButton>

  <!-- <NConfigProvider :theme="darkTheme" :locale="zhCN" :date-locale="dateZhCN">
    <NSpace vertical>
      <NInput />
      <NDatePicker />
    </NSpace>
  </NConfigProvider>-->
</template>

<style scoped>
body {
  background: rgb(196, 11, 11);
}

a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
