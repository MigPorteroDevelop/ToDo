<script>

export default {
  props: ['show'],
  emits: ['close'],
  methods:{
    closeAlert(){
      this.$emit('close');
    }
  }
}
</script>

<template>
  <div class="alert" v-if="show">
    <div>ToDo title is required</div>
    <div @click="closeAlert" class="close-alert">&times;</div>
  </div>
</template>

<style scoped>
.alert {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: var(--danger-color);
  margin-bottom: 20px;
  padding: 0 20px 0 20px;
  border-radius: 10px;
  height: 30px;
}

.close-alert {
  font-size: 50px;
  cursor: pointer;
}
</style>