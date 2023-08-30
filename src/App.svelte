<script>
  let pageTitle = "りんか：2023年夏休み宿題計画";
  let point = 70;
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
    "2023-08-04",
    "2023-08-05",
    "2023-08-06",
    "2023-08-07",
    "2023-08-08",
    "2023-08-09",
    "2023-08-10",
    "2023-08-11",
    "2023-08-12",
    "2023-08-13",
    "2023-08-14",
    "2023-08-15",
    "2023-08-16",
    "2023-08-17",
    "2023-08-18",
    "2023-08-19",
    "2023-08-20",
    "2023-08-21",
    "2023-08-22",
    "2023-08-23",
    "2023-08-24",
    "2023-08-25",
    "2023-08-26",
    "2023-08-27",
    "2023-08-28",
    "2023-08-29",
    "2023-08-30",
    "2023-08-31",
  ];

  import { cdate } from "cdate";

  function miyasuiDay(day) {
    let cd = cdate(day);
    return cd.text("%-m/%-d");
  }

  function chanzuke(name) {
    return name + "ちゃん";
  }

  function calcWeekday(day) {
    let cd = cdate(day);
    return "weekday-" + cd.text("%w");
  }

  let startAt = "2023-07-21";

  let endAt = "2023-08-31";

  function makeGraph() {
    let summerdays = [];

    // for文の条件は（最初にやること、続く条件、ループごとにやること）
    // 続く条件とは、比較演算子でTRUEであるということ
    // つまり、今回は、夏休み終了日を超えるまで、ループが続く
    for (
      let day = cdate(startAt);
      day <= cdate(endAt);
      day = day.add(1, "day")
    ) {
      summerdays.push(day.text("%Y-%m-%d"));
    }

    days = summerdays;

    let goukei = 0;
    for (let i = 0; i < syukudais.length; i = i + 1) {
      goukei = goukei + syukudais[i].point;
    }
    point = goukei;
  }

  let syukudais = [
    { title: "日誌（1ページ1ポイント）", point: 40 },
    { title: "自由研究", point: 20 },
    { title: "日記", point: 10 },
  ];

  function addSyukudai() {
    syukudais.push({ title: "", point: 0 });
    syukudais = syukudais;
  }

  //
</script>

<main>
  <h1>{pageTitle}</h1>

  <div class="data_form no-print">
    <div>
      <label
        >グラフのタイトル
        <input type="text" bind:value={pageTitle} />
      </label>
    </div>

    <div>
      <label
        >夏休み開始日
        <input
          class="start_at"
          name="startAt"
          type="date"
          bind:value={startAt}
        />
      </label>
      <label
        >夏休み最終日
        <input class="end_at" name="endAt" type="date" bind:value={endAt} />
      </label>
    </div>

    {#each syukudais as syukudai}
      <div>
        <label
          >宿題
          <input class="title" type="text" bind:value={syukudai.title} />
        </label>
        <label>
          <input class="point" type="number" bind:value={syukudai.point} />
        </label>
      </div>
    {/each}

    <button on:click={addSyukudai}>宿題を追加する</button>

    <hr />

    <button on:click={makeGraph}>表を作成</button>
  </div>

  <div class="container">
    <div class="naiyou">
      <ul>
        {#each syukudais as shukudai}
          <li>{shukudai.title}: {shukudai.point}</li>
        {/each}
      </ul>
    </div>
    <div
      class="parent"
      style="grid-template-columns: repeat({days.length}, 1fr);"
    >
      {#each days as day}
        <div class="miyasuiday {calcWeekday(day)}">{miyasuiDay(day)}</div>
      {/each}
    </div>
    <div
      class="parent graph"
      style="grid-template-columns: repeat({days.length}, 1fr);"
    >
      {#each Array(point) as _}
        {#each days as day}
          <div class="cell {calcWeekday(day)}" />
        {/each}
      {/each}
    </div>
  </div>
</main>

<style>
  /* このスタイルタグの中がｃｓｓ */

  /* このコンテナは表のいちばん外側の要素 */
  .container {
    border: 2px solid rgb(0, 0, 0);
    position: relative;
  }

  .title {
    width: 300px;
  }

  .point {
    width: 60px;
  }

  .parent {
    display: grid;
  }

  .naiyou {
    background-color: #fff;
    position: absolute;
    z-index: 9999;
    text-align: left;
    right: 30px;
    top: 40px;
  }

  .naiyou ul {
    list-style-type: none;
    padding: 0 20px;
  }

  .naiyou li {
    margin-left: 0;
  }

  .graph {
    position: relative;
  }

  .graph::before {
    content: "";
    position: absolute;
    top: 0px;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      to top right,
      transparent 49.9%,
      black 50%,
      black 50.1%,
      transparent 50%
    );
  }

  .miyasuiday {
    font-size: 5px;
    min-height: 10px;
    min-width: 20px;
    border: 0.5px solid #333;
  }

  .cell {
    min-height: 10px;
    min-width: 20px;
    border: 1px solid #ddd;
  }

  .weekday-6 {
    background-color: #b4eaff;
  }

  .weekday-0 {
    background-color: #ffcbd6;
  }

  @media print {
    .no-print {
      display: none;
    }
  }
</style>
