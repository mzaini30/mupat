<script>
  import { halaman_aktif } from "../state/tombol-aktif";
  import gosit from "gosit";
  import TampilkanPostingan from "../komponen/tampilkan-postingan.svelte";
  import excalibur from "excalibur-zen";
  import api from "../data/api.json";

  let linkGoogleForms;
  let banyaknya_yang_mendaftar = 0;

  $halaman_aktif = "ppdb";

  async function run() {
    let datanya = await excalibur(api.server, {
      id: api.spreadsheet,
      kunci: "ambil",
    });
    datanya = await datanya.json();
    console.log(datanya);
    linkGoogleForms = datanya[0].link_google_forms;
    // let result = await gosit(
    //   "1S_-lKdbmroS6h1LJg9_9oVqwPLHl5R_TuZzrfeIdlio", // spreadsheet id
    //   "Form Responses 1", // sheet name
    // );
    let result = await gosit(
      datanya[0].spreadsheet_id, // spreadsheet id
      datanya[0].sheet_name, // sheet name
    );
    // console.log(result);
    banyaknya_yang_mendaftar = result.length;
  }
  run();
</script>

<iframe
  src={linkGoogleForms}
  frameborder="0"
  class="w-full h-[calc(100vh-198px)]"
></iframe>
