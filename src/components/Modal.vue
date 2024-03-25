<template>
  <div class="backdrop" @click.self="closeModal">
    <div
      class="modal"
      :class="{ sale: theme === 'sale', dark: theme === 'dark' }"
    >
      <!-- <h1>{{ header }}</h1>
      <p>{{ text }} </p> -->
      <slot> </slot> <!-- similar like yield and section in laravel --> 
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["theme"],
  methods: {
    closeModal() {
      this.$emit("close");
    }
  }
};
</script>

<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}

.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}

.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}

.modal.sale {
  background: crimson;
  color: white;
}

.modal.sale h1 {
  color: white;
}

.modal.sale a{
  color: purple;
}

.modal.dark {
  background: darkslategrey;
  color: white;
}

.modal.dark a{
  color: coral;
}

.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
}

.modal .actions a {
  text-decoration: none;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  margin: 10px
}

.modal .actions a:hover{
  text-decoration: underline;
}

/* 
    There are 2 ways for styling in vue:
    1. Scoped Style -> the css only works for 1 vue file
    2. .[***.vue] [tag] -> the css only affect for the tag in 1 file.
    3. Without scoped -> css global
  */
</style>
