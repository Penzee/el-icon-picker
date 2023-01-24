<script setup lang="ts">
import { ref } from 'vue';
import ElIconPicker from './components/el-icon-picker.vue';

const icon = ref<string>('');
</script>

<template>
  <el-form>
    <el-form-item label="图标">
      <ElIconPicker v-model="icon"></ElIconPicker>
    </el-form-item>
  </el-form>
</template>

<style scoped>
</style>
