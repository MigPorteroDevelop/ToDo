<script>

export default {
  props: {
    message: {
      required: true,
      type: String,
    },
    show: {
      required: true,
      type: Boolean,
    },
    type: {
      required: false,
      default: "danger",
      validator(value) {
        return ["danger", "warning", "info"].includes(value);
      }
    }
  },

  computed: {
    backgroundColor() {
      const options = {
        danger: "var(--danger-color)",
        info: "var(--info-color)",
        warning: "var(--warning-color)",
      }
      return options[this.type];
    }
  },
  emits: ['close'],
  methods: {
    closeAlert() {
      this.$emit('close');
    }
  }
}
</script>

<template>
  <div class="alert" v-if="show" :style="{ backgroundColor }">
    ToDo title is required
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