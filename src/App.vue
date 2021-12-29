<template>
  <div id="app" class="app">
    <div class="row">
      <div class="col">
        <span v-text="'<my-button color=\'color\' />'"></span>
        <ReusableButton :color="color" :text-color="textColor">default</ReusableButton>
      </div>
      <div class="col">
        <span>&:hover, &:focus</span>
        <ReusableButton focus :color="color" :text-color="textColor">default</ReusableButton>
      </div>
    </div>
    <div class="row">
      <div class="col">
      <span v-text="'<my-button color=\'color\' outlined />'"></span>
        <ReusableButton :color="color" :text-color="textColor" outlined>default</ReusableButton>
      </div>
      <div class="col">
        <span>&:hover, &:focus</span>
        <ReusableButton :color="color" :text-color="textColor" focus outlined>default</ReusableButton>
      </div>
    </div>
    <div class="row">
      <div class="col">
      <span v-text="'<my-button color=\'color\' text />'"></span>
        <ReusableButton :color="color" :text-color="textColor" text>default</ReusableButton>
      </div>
      <div class="col">
        <span>&:hover, &:focus</span>
        <ReusableButton :color="color" :text-color="textColor" focus text>default</ReusableButton>
      </div>
    </div>
    <div class="row">
      <div class="col">
      <span v-text="'<my-button color=\'color\' no-shadow />'"></span>
        <ReusableButton :color="color" :text-color="textColor" no-shadow>default</ReusableButton>
      </div>
      <div class="col">
        <span>&:hover, &:focus</span>
        <ReusableButton :color="color" :text-color="textColor" focus no-shadow>default</ReusableButton>
      </div>
    </div>
    <div class="row">
      <div class="col">
      <span v-text="'<my-button color=\'color\' disabled />'"></span>
        <ReusableButton :color="color" :text-color="textColor" disabled>default</ReusableButton>
      </div>
      <div class="col">
        <span>&:hover, &:focus</span>
        <ReusableButton :color="color" :text-color="textColor" focus disabled>default</ReusableButton>
      </div>
    </div>
  </div>
</template>

<script>
import ReusableButton from './components/reusable-button.vue'
export default {
  name: 'App',
  components: {
    ReusableButton
  },
  data () {
    return {
      color: '#fe6434',
      textColor: '#666666'
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600;700&display=swap');
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.app {
  font-family: 'Fira Code', monospace;
  width: 100vw;
  height: 100vh;
  overflow: scroll;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.row {
  display: flex;
  gap: 100px;
  justify-content: center;
  margin-top: 25px;
}

.col {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  /* align-items: center; */
  gap: 10px;
  font-weight: 600;
  color: rgba(0, 0, 0, 0.7);
  font-size: 1.15rem;
}

</style>
