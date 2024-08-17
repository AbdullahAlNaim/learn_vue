<template>
  <form @submit.prevent="submitData">
    <div>
      <label for="name">Name</label>
      <input type="text" for="name" v-model="enteredName">
    </div>
    
    <div>
      <label for="Phone">Phone</label>
      <input type="tel" for="name" v-model="enteredPhone"> 
    </div>
    
    <div>
      <label for="">Email</label>
      <input type="email" for="name" v-model="enteredEmail">
    </div>

    <div>
      <button>Add Contact</button>
    </div>
 </form>
</template>

<script>
export default {
  emits: ['add-contact'],
  data() {
    return {
         enteredName: '',
         enteredPhone: '',
         enteredEmail: '',
      }
  },
  methods: {
    submitData() {
      this.$emit('add-contact', this.enteredName, this.enteredPhone, this.enteredEmail)
      console.log('pressed add new friend');
    }
  }
}
</script>