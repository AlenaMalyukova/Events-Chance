<template>
  <div class="cards-wrap">
    <el-card class="cards-wrap-card" shadow="never">
      <span> Name: {{item.value}}</span>
      <span v-if="item.chance"> Chance: {{item.chance}}</span>
    </el-card>
    <el-button 
      class="cards-wrap__btn-delete" 
      type="primary" 
      size="mini" 
      icon="el-icon-delete"
      @click="deleteCard">
    </el-button>
  </div>
</template>

<script>
export default {
  name: 'EventsCard',
  props: {
    item: Object
  },
  methods: {
    deleteCard() {
      this.$emit('delete-card', this.item)
    }
  }
}
</script>
<style scoped>
.cards-wrap {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 2px;
}

.cards-wrap-card {
  width: 90%;
}

.cards-wrap__btn-delete {
  height: min-content;
}
</style>