<template>
  <el-card class="wrapper">
    <el-input 
      class="wrapper__input" 
      placeholder="Please input event" 
      v-model="input" 
      clearable>
    </el-input>
    <el-button 
      class="wrapper__btn-add"
      type="primary"
      ref="addEvent"
      :disabled="!input.trim()"
      @click="addEvent" 
      clearable>Add
    </el-button>
  </el-card>
</template>

<script>
export default {
  name: 'EventsInput',
  data: () => ({
    input: '',
    // rules: {
    //   input: [
    //     {
    //       required: true, message: 'Please input ...', 
    //     }
    //   ]
    // }
  }),
  methods: {
    addEvent() {
      this.$emit('add-event', this.input)
      this.input = '' 
    }
  }
  
}
</script>
<style scoped>
.wrapper {
  max-width: 700px;
  width: 100%;
}
.wrapper__input {
  max-width: 500px;
}
</style>