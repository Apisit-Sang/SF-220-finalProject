<script>
  let x = [];
  import { accounts, account, mode } from "./stores.js";

  function removesubjects(subject) {
    let confirm = prompt(
      "กรุณายืนยันวิชาที่ต้องการถอน(กรอก 'ยืนยัน' เพื่อยืนยันวิชาที่ต้องการถอน)"
    );
    if (confirm == "ยืนยัน") {
      x.push(subject);
      x = x;
    }
  }

  function confirm(x) {
    let i = 0;
    let len = x.length;
    for (; i < len; i++) {
      $accounts[$account].sub.splice($accounts[$account].sub.indexOf(x[i]), 1);
    }
    $mode = "alladd";
  }
</script>

<div><h1>ถอดถอนรายวิชา</h1></div>

<div><table>
  <tr>
    <th>รายวิชา</th>
    <th>เพิ่มเติม</th>
  </tr>
  {#each $accounts[$account].sub as i}
    <tr>
      <td>{i}</td>
      <td><button on:click={() => removesubjects(i)}>ลบ</button> </td>
    </tr>
  {/each}
</table></div>

<div>
<p>วิชาที่ต้องการถอน</p>
<p>{x}</p>
</div>

<div>
<button on:click={() => confirm(x)}>ยืนยันวิชาที่ต้องการถอน</button>
</div>

<style>
  *{
      padding:0px;
      margin: 0px;
      box-sizing: border-box;
        }
  div{
    display: flex;
    justify-content: center;
  }
  div h1{
    margin-top: 50px;
  }
  div table{
    margin-top:40px;
    border-collapse: collapse;
    background-color:#C7D0D8;
            
    padding: 10px;
    text-align: center;
            
    width:540px;
    height: 200px;
    box-shadow: 0px 10px 30px 5px rgba(87,85,101,.2);
  }
  tr{
    border-bottom: 1px dashed grey;
    background-color: white;
    height: 50px;
  }
  td{
    border-top: 1px dashed grey;
  }

</style>