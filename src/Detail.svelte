<script>
  import { mode, subjects, sub, accounts, account } from "./stores.js";
  let name = $sub;
  let subject = $subjects.find((x) => x.name == name).subject;
  function isadmin() {
    if ($accounts[$account].role == "admin") {
      return true;
    } else {
      return false;
    }
  }
  function change_subject() {
    alert("บันทึก");
    let newcredit = document.getElementById("credit").value;
    let newtotal = document.getElementById("total").value;
    let newdescription = document.getElementById("description").value;
    let new_short_description =
      document.getElementById("short_description").value;

    if (newtotal < $subjects.find((x) => x.name == name).register) {
      alert("จำนวนผู้ลงทะเบียนเกินกว่าค่าที่แก้");
    } else {
      $subjects.find((x) => x.name == name).credit = newcredit;
      $subjects.find((x) => x.name == name).total = newtotal;
      $subjects.find((x) => x.name == name).description = newdescription;
      $subjects.find((x) => x.name == name).short_description =
        new_short_description;
      $subjects.find((x) => x.name == name).remaining =
        newtotal - $subjects.find((x) => x.name == name).register;

      $mode = "allsubjects";
    }
  }
</script>

<h1>Detail</h1>
{name}
<br />
{#if !isadmin()}
  วิชา<br />{subject}
  <br />
  หน่วยกิต<br />{$subjects.find((x) => x.name == name).credit}
  <br />
  จำนวนโควต้า<br />{$subjects.find((x) => x.name == name).total}
  <br />
  จำนวนที่ลงทะเบียน<br />{$subjects.find((x) => x.name == name).register}
  <br />
  description<br />{$subjects.find((x) => x.name == name).description}
{:else}
  วิชา<br />
  {subject}
  <br />
  หน่วยกิต<br />
  <input
    type="text"
    id="credit"
    value={$subjects.find((x) => x.name == name).credit}
  />
  <br />
  จำนวนโควต้า<br />
  <input
    type="text"
    id="total"
    value={$subjects.find((x) => x.name == name).total}
  />
  <br />
  จำนวนที่ลงทะเบียน<br />
  {$subjects.find((x) => x.name == name).register}
  <br />
  description<br />
  <input
    type="text"
    id="description"
    value={$subjects.find((x) => x.name == name).description}
  />
  <br />
  short description<br />
  <input
    type="text"
    id="short_description"
    value={$subjects.find((x) => x.name == name).short_description}
  />
{/if}

<button on:click={() => change_subject()}>บันทึก</button>
