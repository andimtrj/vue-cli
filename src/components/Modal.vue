<template>
  <div class="backdrop">
    <div class="modal">
      <h1>{{ header }}</h1>
      <p>modal content</p>
    </div>
  </div>
</template>

<script>
  export default{
    props: [
      'header'
    ]
  }
</script>

<style>
  .modal{
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
  }

  .backdrop{
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
  }

  .modal h1{
    color: #03cfb4;
    border: none;
    padding: 0;
  }

  /* 
    There are 2 ways for styling in vue:
    1. Scoped Style -> the css only works for 1 vue file
    2. .[***.vue] [tag] -> the css only affect for the tag in 1 file.
    3. Without scoped -> css global
  */

</style>