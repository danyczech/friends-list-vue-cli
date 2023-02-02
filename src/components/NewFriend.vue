<template>
  <form @submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input type="text" v-model="enteredName" placeholder="Your name" />
    </div>
    <div>
      <label>Phone</label>
      <input type="tel" v-model="enteredPhone" placeholder="Your phone" />
    </div>
    <div>
      <label>E-mail</label>
      <input type="email" v-model="enteredEmail" placeholder="Your e-mail" />
    </div>
    <div>
      <button>Add friend</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ["add-contact"],
  data() {
    return {
      enteredName: "",
      enteredPhone: "",
      enteredEmail: "",
    }
  },
  methods: {
    submitData() {
      this.$emit(
        "add-contact",
        this.enteredName,
        this.enteredPhone,
        this.enteredEmail
      )
    },
  },
}
</script>
