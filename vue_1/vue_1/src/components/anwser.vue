<script setup>
import { reactive, ref } from 'vue'

const inputText = ref('')
const tags = reactive([])

const addTag = () => {
  const text = inputText.value.trim()
  
  // 空值检查
  if (text === '') {
    alert('标签不能为空')
    return
  }
  
  // 去重检查
  if (tags.includes(text)) {
    alert('标签已存在')
    return
  }
  
  tags.push(text)
  inputText.value = ''
}

const removeTag = (index) => {
  tags.splice(index, 1)
}
</script>

<template>
  <div style="max-width: 500px; margin: 50px auto; font-family: sans-serif;">
    <h2>🏷️ 标签输入器</h2>
    
    <div style="display: flex; gap: 8px; margin-bottom: 20px;">
      <input 
        v-model="inputText"
        @keyup.enter="addTag"
        placeholder="输入标签，按回车添加..."
        style="flex: 1; padding: 8px; border: 1px solid #ddd; border-radius: 4px;"
      />
      <button 
        @click="addTag"
        style="padding: 8px 20px; background: #2196F3; color: white; border: none; border-radius: 4px; cursor: pointer;"
      >
        添加
      </button>
    </div>

    <div style="display: flex; flex-wrap: wrap; gap: 8px;">
      <span 
        v-for="(tag, index) in tags" 
        :key="index"
        style="display: inline-flex; align-items: center; padding: 4px 12px; background: #e3f2fd; color: #1976D2; border-radius: 20px; font-size: 14px;"
      >
        {{ tag }}
        <button 
          @click="removeTag(index)"
          style="margin-left: 6px; background: none; border: none; color: #f44336; cursor: pointer; font-size: 16px; padding: 0;"
        >
          ×
        </button>
      </span>
    </div>

    <p v-if="tags.length === 0" style="color: #999; margin-top: 20px;">
      还没有标签，添加一个吧
    </p>
  </div>
</template>