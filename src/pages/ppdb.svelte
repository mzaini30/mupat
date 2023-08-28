<script>
  import { halaman_aktif } from "../state/tombol-aktif";
  import gosit from "gosit";

  let banyaknya_yang_mendaftar = 0;

  $halaman_aktif = "ppdb";

  async function run() {
    let result = await gosit(
      "1oyMFLapk7et99ygMKYq8sJbKs2uX2_SaBzTpmd2Xg5c", // spreadsheet id
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
    href="https://docs.google.com/forms/d/e/1FAIpQLSdnP4SPAuU-OckkG_rc6Q89iqw1ZU3F0tzwF3HT-brI3bDimg/viewform"
    >Pendaftaran Siswa Baru</a
  >
</div>

<!-- <iframe
  class="w-full min-h-100"
  src="https://docs.google.com/forms/d/e/1FAIpQLSdnP4SPAuU-OckkG_rc6Q89iqw1ZU3F0tzwF3HT-brI3bDimg/viewform"
  frameborder="0"
></iframe> -->
