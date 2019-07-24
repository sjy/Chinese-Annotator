<template>
  <ElTag :class="['tag', classObject]" @click="selectTag" effect="plain" type="info" size="large">
    <div class="tag-name">{{ name }}</div>
    <div class="shortcuts" v-if="shortcuts">（{{ shortcuts }}）</div>
  </ElTag>
</template>

<script>
export default {
  name: 'tag',
  props: {
    name: {
      type: String,
      required: true
    },
    shortcuts: {
      type: String,
      default: ''
    },
    selected: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    classObject() {
      return {
        'machine-active': this.machineSelected,
        active: this.selected
      }
    }
  },
  methods: {
    selectTag() {
      this.$emit('selectTag')
    }
  }
}
</script>

<style lang="scss" scoped>
.tag {
  margin: 0 10px;
  font-size: 16px;

  .shortcuts {
    position: absolute;
    width: 100%;
    text-align: center;
    z-index: 0;
  }

  &:hover {
    color: #409eff;
    border: 1px solid #c6e2ff;
    background-color: #ecf5ff;
  }

  &.machine-active {
    border: 6px solid #2196f3;
  }

  &.active {
    color: white;
    background-color: #4caf50;
  }
}
</style>
