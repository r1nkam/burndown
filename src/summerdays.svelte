<script>
import {cdate} from "cdate"

  let startAt = "2023-07-21"
  let endAt = "2023-08-31"
  let summerdays = []

  function calcDate(){
    let startDate = cdate("2023-07-21")
    let endDate = cdate("2023-8-31")
    let days = []

    for(let day = startDate; day <= endDate; day = day.add(1, "day")){
      days.push(day.text("%Y-%m-%d"))
    }
    
    summerdays = days
  }

</script>

<main>
 <div>
  <label>夏休み開始日
   <input name="startAt" type="date" bind:value={startAt}/>
  </label>
  <label>夏休み最終日
   <input name="endAt" type="date" bind:value={endAt}/>
  </label>
 </div>
<button on:click={calcDate}>計算</button>

<div>{summerdays}</div>
<div>夏休みは{summerdays.length}日です。</div>
 
</main>

<style>

</style>
