<script setup lang="ts">
import { ComponentInternalInstance, defineEmits, defineProps, getCurrentInstance } from 'vue'

const { appContext: {app: { config: { globalProperties } } } } = getCurrentInstance() as ComponentInternalInstance

interface Props {
  modelValue: string
}
const props = defineProps<Props>()

const emits = defineEmits(['update:modelValue'])
</script>

<template>
  <el-popover trigger="focus" :width="256">
    <template #reference>
      <el-button :icon="modelValue">{{ modelValue }}</el-button>
    </template>
    <div class="el-icon-picker">
      <component v-for="icon in globalProperties.$icons" :key="icon"
        :class="[icon, 'icon', { 'icon-active': icon == modelValue }]"
        :is="icon"
        @click="emits('update:modelValue', icon)">
      </component>
    </div>
  </el-popover>
</template>

<style scoped>
.el-icon-picker {
  height: 256px;
  overflow-y: scroll;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

.icon {
  display: inline-block;
  width: 24px;
  height: 24px;
  color: var(--el-text-color-regular);
  font-size: 20px;
  border-radius: 4px;
  cursor: pointer;
  text-align: center;
  line-height: 45px;
  margin: 5px;
}

.icon:hover {
  color: var(--el-color-primary);
}

.icon-active {
  color: var(--el-color-primary);
}
</style>