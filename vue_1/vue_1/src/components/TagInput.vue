<template>
    <div style="max-width:500px;margin:50px auto; font-family:sans-serif;">
        <h2>🏷️ 标签输入器</h2>
        <div style="display:flex; gap: 8px;margin-bottom: 20px;">
            <label for="tagsInput">输入标签：</label>
            <input id="tagsInput" type="text" v-model="tags" @keydown.enter.prevent="getTags"
            style="flex: 1;padding: 8px; border: 1px solid #ddd; border-radius: 4px;">
            <button @click="getTags"
            style="cursor:pointer;padding: 8px 20px; border: 1px solid #ddd;border-radius: 4px;"
            >添加</button>
        </div>
        <div style="display: flex; flex-wrap: wrap; gap: 8px;">
            <p v-if="tagArr.length === 0">还没有标签,添加一个吧!</p>
            <span v-for="(tag,index) in tagArr">{{ tag }}</span>
        </div>

    </div>
</template>

<script setup>
import { reactive,ref} from 'vue';
const tags = ref('');
const tagArr = reactive([]);
const getTags = () => {
    const text = tags.value.trim();
    if(text === ''){
        alert("标签不能为空!");
        return;
    }
    if(tagArr.includes(tags.value)){
        alert('标签已存在')
        return
    }
    tagArr.push(tags.value);
    tags.value = '';
}
</script>
