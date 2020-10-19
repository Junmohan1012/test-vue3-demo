<template>
  <div class="about">
    <template v-if="detail">
      <h1>{{detail.text}}</h1>
      <div>创建时间：{{detail.time}}</div>
    </template>
    <div v-else class="empty">别看了这里啥也没有</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { useRoute } from 'vue-router';
import { useStore } from 'vuex';

export default defineComponent({
  data: () => ({}),
  setup() {
    const route = useRoute();
    const { state } = useStore();
    const { item } = route.params;
    const detail = state.todoListMap[`${item}`];
    return { detail };
  },
});
</script>

<style lang="less">
.about {
  text-align: center;
  h1 {
    color: @color-primary;
  }
}
</style>
