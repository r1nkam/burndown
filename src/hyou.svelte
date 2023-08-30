<script>

</script>

<main>
 <div class="parent">
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
 </div>
</main>

<style>
  .parent{
    border:2px solid rgb(0, 0, 0);
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(3, 1fr);
  }

  .parent div{
    min-height:88px;
    min-width:88px;
    border: 1px solid #ddd;
  }
</style>
