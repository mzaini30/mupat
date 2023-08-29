<script>
  import { halaman_aktif } from "../state/tombol-aktif";
  import TampilkanPostingan from "../komponen/tampilkan-postingan.svelte";

  $halaman_aktif = "informasi";
</script>

<!-- <iframe
  class="rumble"
  width="640"
  height="360"
  src="https://rumble.com/embed/v1q79es/?pub=1ksg7a"
  frameborder="0"
  allowfullscreen
></iframe> -->
<TampilkanPostingan kategori="informasi"></TampilkanPostingan>
