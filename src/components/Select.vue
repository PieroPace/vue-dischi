<template>
  <div class="col-6">
    <label class="text-white mx-2 fs-5" :for="'select' + type">
      {{ type }}:
    </label>
    <select
      :id="'select' + type"
      v-model="selected"
      @change="$emit('changeValue', selected)"
    >
      <option>All</option>
      <option
        v-for="(element, index) in array"
        :key="index + type"
        :value="element"
      >
        {{ element }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Select",
  props: ["type", "array"],
  data() {
    return {
      selected: "All",
    };
  },
  methods: {
  },
};
</script>

<style></style>
