<template>
  <label
    :key="groupId + id"
    :for="groupId + id"
  >
    <div>
      <input
        :isDisabled="isDisabled"
        :id="groupId + id"
        v-model="computedSelected"
        type="radio"
        :value="value"
      >
      <span> {{ text }} </span>
    </div>
  </label>
</template>

<script>
export default {
  name: 'RadioItem',
  props: {
    selectedItem: {
      type: Number,
      default: null,
    },
    id: {
      type: Number,
    },
    value: {
      type: Number,
      default: null,
    },
    text: {
      type: String,
      default: '',
    },
    isDisabled: {
      type: Boolean,
      default: false,
    },
    groupId: {
      type: String,
      default: '',
    },
  },
  
  computed: {
    computedSelected: {
      get: function getValue() {
        return this.selectedItem;
      },

      set: function setValue() {
        this.$emit('input', this.value);
      }
    }
  }
}
</script>
