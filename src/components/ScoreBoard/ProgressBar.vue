<template>
  <div class="board">
    <span>Cards not Matched</span>
    <h2 class="ml-2">{{ nonMatchedPairs }}</h2>
  </div>
</template>

<script lang="ts" setup>
import { computed } from 'vue'
import { useStore } from 'vuex'
import { GameStoreKey } from '@/stores'

const { state } = useStore(GameStoreKey)
const nonMatchedPairs = computed(() => state.nonMatchedPairs)
</script>

<style scoped>
.board {
  display: flex;
  flex-direction: row;
  padding: 10px;
  background-color: #bbada0;
  border-radius: 5px;
  justify-content: space-between;
  align-items: center;
  color: #eae0d1;
}

span {
  font-size: 19px;
  font-weight: bold;
  display: block;
  width: 100%;
  text-align: center;
}

h2 {
  color: #fff;
  padding-left: 10px;
}
@media screen and (max-width: 450px) {
  .board {
    width: 105px;
  }
  span {
    font-size: 17px;
  }
}

@media screen and (max-width: 380px) {
  .board {
    width: 95px;
  }
}

@media screen and (max-width: 360px) {
  .board {
    width: 90px;
  }
  span {
    font-size: 15px;
  }
}
</style>
