<script>
  import { halaman_aktif } from "../state/tombol-aktif";

  let kode_unik;
  let id = "0ce5bba79b60d7fed796f33ec9cb9080"; // id, nama, username, password, kode_unik
  // https://sdmuh4t-smr.sch.id/excalibur/scubus-index.php?halaman=olah-sql&database=0ce5bba79b60d7fed796f33ec9cb9080

  kode_unik = crypto.randomUUID().split("-")[0];

  $halaman_aktif = "profil";
</script>

<div class="px-2">
  <p>Kode unik</p>
  <p>{kode_unik}</p>
</div>
