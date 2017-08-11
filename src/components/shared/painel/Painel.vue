<template>
  <div class="panel text-center">
    <h2 class="panel-title text-center" @dblclick="visivel = !visivel">{{ titulo }}</h2>
    
    <transition name="panel-fade">
      <div class="panel-body" v-show="visivel">
        <slot>

        </slot><!-- end panel-body -->
      </div>
    </transition>
  </div><!-- end panel -->
</template>

<script>
export default {
   props: ['titulo'],
   data() {
      return {
        visivel: true
      }
   }
}
</script>

<style>
.panel {
  padding: 0 auto;
  border: solid 2px grey;
  display: inline-block;
  margin: 5pt;
  width: 200px;
  height: 100%;
  vertical-align: top;
}

.panel .panel-title {
  background: lightblue;
  margin: 0 0 15pt 0;
  padding: 2.5pt;
  text-transform: uppercase;
}


.panel-fade-enter, .panel-fade-leave-active {
  opacity: 0
}

.panel-fade-enter-active, .panel-fade-leave-active {
  transition: opacity .4s
}
</style>
