<template>
  <div>
    <el-button @click="ElMessage('hello')">button</el-button>
    <ElButton :icon="ElIconEditPen" type="success">button</ElButton>
    <LazyElButton type="warning">lazy button</LazyElButton>
    <el-icon :size="20">
      <ElIconEdit/>
    </el-icon>
    <el-button>{{ i18n.t('home') }}</el-button>
    <el-select v-model="locale" @change="handleLanguage">
      <el-option v-for="(item, key) in locales" :key="key" :value="key" :label="item"></el-option>
    </el-select>
    <div>Now: {{ time }}</div>
  </div>
</template>

<script setup lang="ts">

const { $dayjs, $timeFromNow } = useNuxtApp();

const i18n = useI18n()
const {locale} = i18n

const locales = ref({
  cn: '简体中文',
  en: 'English',
  russ: 'Русский'
})

// 获取本地存储的语言
const language = useCookie<string>('language')
if (language.value) {
  locale.value = language.value
}

// 语言切换
const handleLanguage = (value: string) => {
  language.value = value
}

// const time = ref($dayjs().format('YYYY-MM-DD'))
const time = ref($dayjs().to($dayjs('2024-01-01')))

</script>
