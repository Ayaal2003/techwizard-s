<template>
  <div class="tabs">
    <button
      v-for="tab in tabs"
      :key="tab.id"
      :class="['tab-button', { active: currentTab === tab.id }]"
      @click="currentTab = tab.id"
    >
      {{ tab.label }}
    </button>
  </div>
</template>

<script>
export default {
  props: {
    tabs: {
      type: Array,
      required: true,
    },
    initialTab: {
      type: String,
      default: "home",
    },
  },
  data() {
    return {
      currentTab: this.initialTab,
    };
  },
  watch: {
    currentTab(newTab) {
      this.$emit("tab-change", newTab);
    },
  },
};
</script>

<style scoped>
.tabs {
  display: flex;
  justify-content: space-around;
  background-color: #f0f0f0;
  padding: 10px;
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
}
.tab-button {
  padding: 10px 20px;
  border: none;
  background: none;
  cursor: pointer;
  font-size: 16px;
}
.tab-button.active {
  border-bottom: 2px solid #007bff;
  color: #007bff;
}
</style>
