<template>
  <div class="list-wrap">
    <EventsInput @add-event="addEvent"/>
    <el-card class="list-wrap-of-events">
      <div slot="header" class="list-wrap-of-events__list-title">
        <span>Your Events</span>
      </div>
      <EventsCard 
        v-for="(item, idx) in list" :key="idx"
        :item='item'
        @delete-card="deleteCard">
      </EventsCard>
      <div class="list-wrap-of-event__btn-predict" v-if="list.length > 0" >
        <el-button @click="predictEvents" type="primary">Predict</el-button>
      </div>
    </el-card>
  </div>
</template>

<script>
import EventsInput from './EventsInput'
import EventsCard from './EventsCard'

export default {
  name: 'EventsList',
  components: {
    EventsInput,
    EventsCard
  },
  data: () =>({
    list: []
  }),
  methods: {
    addEvent(item) {
      const obj = {value: item}
      this.list.push(obj)
    },
    predictEvents() {
      let list = []
      
      this.list.forEach(i => {
        i = this.predictEvent(i)
        list.push(i)
      })

      this.list = list
      console.log(this.list)
    },
    //сделать вывод в карточку
    getRandomInt(min, max) {   //рандомное число
      min = Math.ceil(min)
      max = Math.floor(max)
      const randomInteg = Math.floor(Math.random() * (max - min)) + min
      return randomInteg
    },
    predictEvent(item) {
      return {
        value: item.value,
        chance: this.getRandomInt(0, 101)
      }
    },
    deleteCard(card) {
      this.$delete(this.list, this.list.indexOf(card))
    }
  }
}
</script>
<style scoped>
.list-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.list-wrap-of-events {
  max-width: 700px;
  width: 100%;
}

.ist-wrap-of-events__list-title {
  padding-bottom: 10px;
}

.list-wrap-of-event__btn-predict {
  padding-top: 15px;
}
</style>