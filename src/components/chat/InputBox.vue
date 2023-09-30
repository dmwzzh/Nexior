<template>
  <div class="input-box">
    <el-input v-model="value" :rows="2" type="textarea" placeholder="Please input" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { ElInput, ElButton } from 'element-plus';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { ROUTE_CHAT_INDEX } from '@/router/constants';

export default defineComponent({
  name: 'InputBox',
  components: {
    ElInput,
    ElButton,
    FontAwesomeIcon
  },
  props: {
    modelValue: {
      type: String,
      required: true
    }
  },
  emits: ['update:modelValue'],
  data() {
    return {
      value: this.modelValue
    };
  },
  watch: {
    value(val) {
      this.$emit('update:modelValue', val);
    },
    modelValue(val) {
      if (val !== this.value) {
        this.value = val;
      }
    }
  }
});
</script>

<style lang="scss" scoped>
.sidebar {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  .top {
    display: flex;
    flex-direction: column;
  }
  .bottom {
    display: flex;
    flex-direction: column;
  }
}
</style>