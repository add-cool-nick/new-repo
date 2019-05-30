<template>

  <div  class="app">
    <Navbar />
    <Heading />
    <Form />
    
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import Heading from './components/Heading.vue'
import Form from './components/Form.vue'
import Navbar from './components/Navbar.vue'

export default {
  name: 'App',
  components: {
    Heading,
    Form,
    Navbar
  },
  data () {
    return {
      //
    }
  }
}
</script>




