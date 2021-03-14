<template>
  <div id="app">
    <Header/>
    <Reports/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Reports from './components/Reports.vue'

export default {
  name: 'app',
  components: {
    Header,
    Reports
  },
}
</script>

<style lang="postcss">
@tailwind base;
@tailwind components;
@tailwind utilities;

html, body, #app {
  width: 100%;
  height: 100%;
  overflow: auto;
}
*{
  margin: 0; padding: 0; box-sizing: border-box;font-family: 'Inter', sans-serif;;
}
.flex{
  display:flex;
  align-items: center;
}
.open{
  display:block !important;
}
.relative{
  position:relative;
}
.absolute{
  position:absolute;
}
.max-width{
  position: relative;
  left:50%;
  transform: translateX(-50%);
  max-width: 80rem;
}
body{
  background:#F7FAFC
}
ul{
  list-style-type: none;
}
a{
  text-decoration: none;
}
.active{
  color:#3CC13B !important;
}
.inactive{
  color:#F03738 !important; 
}
</style>
