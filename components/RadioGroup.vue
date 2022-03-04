<template>
  <div>
    <p>{{ computedText }}</p>
    <RadioItem 
      v-for="(item, index) in options"
      :key="index"
      v-bind="item"
      :isDisabled="isDisabled"
      :groupId="groupId"
      @input="setSelected"
      :selectedItem="selectedItem"
    ></RadioItem>
  </div>
</template>

<script>

export default {
  name: 'RadioGroup',
  props: {
    options: {
      type: Array,
      default: [],
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
  data() {
    return {
      selectedItem: null,
      select: null,
    };
  },
  methods: {
    setSelected(value) {
      this.selectedItem = value;
    }
  },
  
  computed: {
    computedText() {
      if (this.selectedItem) {
        return `Выбрано значение ${ this.selectedItem }`;
      }
      return "Значение не выбрано";
    },
  }
}
</script>
