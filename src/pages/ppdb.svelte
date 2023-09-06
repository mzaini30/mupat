<script>
  import { halaman_aktif } from "../state/tombol-aktif";
  import gosit from "gosit";
  import TampilkanPostingan from "../komponen/tampilkan-postingan.svelte";

  let banyaknya_yang_mendaftar = 0;

  $halaman_aktif = "ppdb";

  async function run() {
    let result = await gosit(
      "1S_-lKdbmroS6h1LJg9_9oVqwPLHl5R_TuZzrfeIdlio", // spreadsheet id
      "Form Responses 1", // sheet name
    );
    // console.log(result);
    banyaknya_yang_mendaftar = result.length;
  }
  run();
</script>

<div class="p-3">
  <p class="mb-3 text-lg">
    {banyaknya_yang_mendaftar} calon siswa telah mendaftar
  </p>
  <a
    class="rounded p-2 bg-green-500 text-white w-full block text-center"
    href="#/form">Pendaftaran Siswa Baru</a
  >
</div>
<TampilkanPostingan kategori="ppdb"></TampilkanPostingan>

<!-- <iframe
  class="w-full min-h-100"
  src="https://docs.google.com/forms/d/e/1FAIpQLSdnP4SPAuU-OckkG_rc6Q89iqw1ZU3F0tzwF3HT-brI3bDimg/viewform"
  frameborder="0"
></iframe> -->
