<template>
  <div class="container" @click="doFlip">
    <div class="card" :class="{ flipped: card.flipped }">
      <img v-if="card.name === '1'" class="front" src="../../assets/1.png" />
      <img v-if="card.name === '2'" class="front" src="../../assets/2.png" />
      <img v-if="card.name === '3'" class="front" src="../../assets/3.png" />
      <img v-if="card.name === '4'" class="front" src="../../assets/4.png" />
      <img v-if="card.name === '5'" class="front" src="../../assets/5.png" />
      <img v-if="card.name === '6'" class="front" src="../../assets/6.png" />
      <img v-if="card.name === '7'" class="front" src="../../assets/7.png" />
      <img v-if="card.name === '8'" class="front" src="../../assets/8.png" />

      <img class="back" src="../../assets/back.png" />
      <!-- ToDo: fix number showing on front -->
      <h2 class="card-number">{{ card.number }}</h2>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { toRefs } from 'vue'
import { useStore } from 'vuex'
import type { ICard } from '@/IType'
import { GameStoreKey } from '@/stores'

interface IGameCardProps {
  card: ICard
}

const props = defineProps<IGameCardProps>()

const emit = defineEmits(['onFlip'])

const { card } = toRefs(props)
const { commit } = useStore(GameStoreKey)

const doFlip = () => {
  if (card.value.flipped) {
    return
  }
  commit('flips', [card.value])
  emit('onFlip', card.value)
}
</script>

<style scoped>
.container {
  width: 100px;
  height: 121px;
  margin-right: 3px;
  cursor: pointer;
  position: relative;
  perspective: 800px;
}

.card {
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
}
.card-number {
  position: absolute;
  top: 25px;
  left: 25px;
  color: rgb(0, 0, 0);
  font-size: 40px;
  -webkit-text-stroke: 2px black;
  backface-visibility: hidden;
}

.card.flipped {
  transform: rotateY(180deg);
}

.card img {
  display: block;
  height: 100%;
  width: 100%;
  position: absolute;
  backface-visibility: hidden;
}

.card .back {
  background: blue;
  transform: rotateY(0deg);
}

.card .front {
  background: blue;
  transform: rotateY(180deg);
}

@media screen and (max-width: 450px) {
  .container {
    width: 92px;
    height: 111px;
    margin-right: 1px;
  }
}

@media screen and (max-width: 380px) {
  .container {
    width: 85px;
    height: 102px;
    margin-right: 1px;
  }
}

@media screen and (max-width: 360px) {
  .container {
    width: 70px;
    height: 84px;
    margin-right: 1px;
  }
}
</style>
