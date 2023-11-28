<script setup lang="ts">
import { Ref, ref, UnwrapRef } from 'vue';
import ArrowCollapseDown from '@/components/icons/ArrowCollapseDown.vue';
import ArrowCollapseUp from '@/components/icons/ArrowCollapseUp.vue';

let show: Ref<UnwrapRef<boolean>> = ref(false);
const props = defineProps(['akkordionItem'])
</script>

<template>
  <div class="akkordion-list-item">
    <div class="akkordion-list--title" @click="show = !show">
      <h2>
        {{ props.akkordionItem.title }}
      </h2>
      <arrow-collapse-down v-if="!show"/>
      <arrow-collapse-up v-else/>
    </div>
    <transition name="bounce">
      <p v-show="show" class="akkordion-list--body">
        {{ props.akkordionItem.body }}
      </p>
    </transition>
  </div>
</template>

<style scoped lang="sass">
.bounce-enter-active
  animation: bounce-in .5s

.bounce-leave-active
  animation: bounce-in .5s reverse

.akkordion-list--title
  display: flex
  margin: 1em
  justify-content: space-between

.akkordion-list--body
  margin: 1em

@keyframes bounce-in
  0%
    transform: scale(0)
  50%
    transform: scale(1.5)
  100%
    transform: scale(1)
</style>