<script>
  import { halaman_aktif } from "../state/tombol-aktif";

  let kode_unik;

  kode_unik = crypto.randomUUID().split("-")[0];

  $halaman_aktif = "profil";
</script>

<div class="px-2">
  <p>Kode unik</p>
  <p>{kode_unik}</p>
</div>
