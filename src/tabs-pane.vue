<template>
  <div class="tabs-pane" :class="classes" v-if="active">
    <slot/>
  </div>
</template>

<script>
export default {
  name:'g-tabs-pane',
  inject:['eventBus'],
  data(){
    return {
      active:false
    }
  },
  props:{
    name:{type:String}
  },
  created() {
    this.eventBus.$on('update:selected',
        (selected) => {
          this.active = selected === this.name;
        })
  },
  computed:{
    classes(){
      return { active : this.active}
    }
  }

}
</script>

<style lang="scss" scoped>
.tabs-pane {
  flex-shrink: 0;
  padding: 1em 2em;
  &.active{

  }
}

</style>