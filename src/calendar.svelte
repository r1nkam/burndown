<script>
  let point = 10
  let days = [
    "2023-07-21",
    "2023-07-22",
    "2023-07-23",
    "2023-07-24",
    "2023-07-25",
    "2023-07-26",
    "2023-07-27",
    "2023-07-28",
    "2023-07-29",
    "2023-07-30",
    "2023-07-31",
    "2023-08-01",
    "2023-08-02",
    "2023-08-03",
  ]

  import {cdate} from "cdate"

  function miyasuiDay(day){
     let cd = cdate(day)
     return cd.text("%-m/%-d")
  }

  function chanzuke(name){
    return name + "ちゃん"
  }

  function calcWeekday(day){
    let cd = cdate(day)
    return "weekday-" + cd.text("%w")
  }

</script>

<main>
<h1>{chanzuke("りんか")}の表</h1>

 <div class="parent" style="grid-template-columns: repeat({days.length}, 1fr);">
  {#each days as day}
    <div>{miyasuiDay(day)}</div>
  {/each}
  {#each Array(point) as _}
    {#each days as day}
      <div class="{calcWeekday(day)}"></div>
    {/each}
  {/each}
 </div>
</main>

<style>
  .parent{
    border:2px solid rgb(0, 0, 0);
    display: grid;
    grid-template-rows: repeat(3, 1fr);
  }

  .parent div{
    min-height:20px;
    min-width:20px;
    border: 1px solid #ddd;
  }

  .weekday-6{
    background-color: #b4eaff;

  }

  .weekday-0{
    background-color: #ffcbd6;
  }
</style>
