<template>
  <div>
    <n-input
      v-model:value="expression"
      rows="1"
      type="textarea"
      placeholder="Your math expression (ex: 2*sqrt(6) )..."
      size="large"
      autocomplete="off"
      autocorrect="off"
      autocapitalize="off"
      spellcheck="false"
    />
    <br />
    <br />

    <n-card v-if="result !== ''" title="Result ">
      {{ result }}
    </n-card>
  </div>
</template>

<script setup lang="ts">
import { withDefaultOnError } from '@/utils/defaults';
import { evaluate } from 'mathjs';
import { computed, ref } from 'vue';

const expression = ref('');

const result = computed(() => withDefaultOnError(() => evaluate(expression.value) ?? '', ''));
</script>

<style lang="less" scoped></style>
