<script>

let syukudais= [
   {title: "自由研究", point: 20},
   {title: "日記", point: 10}
]

let total = 0
function calcPoint(){
  let sum = 0
  for (let i = 0; i < syukudais.length; i = i + 1 ) {
    sum = sum + syukudais[i].point
  }
  total = sum
}
function addSyukudai(){
  syukudais.push({title:"", point:0})
  syukudais = syukudais

}
</script>

<main>

  {#each syukudais as syukudai}
  <div>
    <label>宿題
      <input type="text" bind:value={syukudai.title} />
    </label>
    <label>ポイント
      <input type="number" bind:value={syukudai.point}/>
    </label>
  </div>
  {/each}

<button on:click={addSyukudai}>宿題を追加</button>
<button on:click={calcPoint}>計算</button>

<p>合計: {total}</p>

</main>

<style>

</style>
