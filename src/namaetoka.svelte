<script>
let namae = "りんか"
let age = 12
let result = ""
let startAt = ""
let endAt = ""

function createNatubun() {
  // result = namae + "(" + age + ")"
  result = `${namae}(${age})の夏休みは${startAt}から${endAt}です。`
} 
</script>

<main>
  <h1>{namae}({age})の自由研究</h1>
  <div>
    <label>名前
      <input name="namae" type="text" bind:value={namae} />
    </label>
    <label>年齢
      <input name="age" type="number" bind:value={age}/>
    </label>
  </div>

  <div>
    <label>夏休み開始日
      <input name="startAt" type="date" bind:value={startAt}/>
    </label>
    <label>夏休み最終日
      <input name="endAt" type="date" bind:value={endAt}/>
    </label>
  </div>

  <div style="background-color: #ddd; height: 100px;">
    {result}
  </div>

  <button on:click={createNatubun}>文章作成</button>
</main>

<style>

</style>
