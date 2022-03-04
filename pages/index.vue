<template>
  <div>
    <RadioGroup 
      class="radio-group"
      :options="groupFirst.options"
      :isDisabled="groupFirst.isDisabled"
      :groupId="groupFirst.groupId"
    ></RadioGroup>
    <RadioGroup 
      class="radio-group"
      :options="groupSecond.options"
      :isDisabled="groupSecond.isDisabled"
      :groupId="groupSecond.groupId"
    ></RadioGroup>
    <div class="radio-group">
      <p>{{ computedText }}</p>
      <RadioItem 
        v-for="(item, index) in groupThird.options"
        v-bind="item"
        :key="index"
        :isDisabled="groupThird.isDisabled"
        :groupId="groupThird.groupId"
        @input="setSelected"
        :selectedItem="groupThird.selectedItem"
      ></RadioItem>
    </div>
  </div>
</template>

<script>

export default {
  name: 'IndexPage',
  data() {
    return {
      groupFirst: {
        groupId: "groupFirst",
        isDisabled: false,
        options: [
          {id: 1, value: 1, text: "Значение 1"},
          {id: 2, value: 2, text: "Значение 2"},
          {id: 3, value: 3, text: "Значение 3"},
        ],
      },
      groupSecond: {
        groupId: "groupSecond",
        isDisabled: true,
        options: [
          {id: 1, value: 1, text: "Значение 1"},
          {id: 2, value: 2, text: "Значение 2"},
          {id: 3, value: 3, text: "Значение 3"},
        ],
      },
      groupThird: {
        selectedItem: null,
        groupId: "groupThird",
        isDisabled: false,
        options: [
          {id: 1, value: 1, text: "Значение 1"},
          {id: 2, value: 2, text: "Значение 2"},
          {id: 3, value: 3, text: "Значение 3"},
        ],
      }
    };
  },
  methods: {
    setSelected(value) {
      this.groupThird.selectedItem = value;
    }
  },
  computed: {
    computedText() {
      if (this.groupThird.selectedItem) {
        return `Выбрано значение ${ this.groupThird.selectedItem }`;
      }
      return "Значение не выбрано";
    },
  }
}
</script>



<style scoped>
.radio-group {
  margin-top: 30px;
}
</style>
