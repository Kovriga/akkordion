<script setup lang="ts">

import { ref } from 'vue';
import AkkordionListItem from '@/components/AkkordionListItem.vue';
import { Ref, UnwrapRef } from 'vue/dist/vue';

let akkordionList: any = ref()

async function myPost() {
  akkordionList.value = await fetch(`https://jsonplaceholder.typicode.com/posts`).then((r) => r.json())
}

myPost()

let show: Ref<UnwrapRef<boolean>> = ref(false);
</script>

<template>
  <div class="akkordion-list">
    <div v-for="item in akkordionList" :key="item" class="akkordion-list--block" >
      <akkordion-list-item :akkordionItem="item" :show="show"/>
    </div>
  </div>
</template>

<style scoped lang="sass">
.akkordion-list
  border: #282828 solid 1px
  width: 800px
  margin: 1em auto
  border-radius: 1em

  .akkordion-list--block
    border-bottom: #282828 solid 1px
</style>