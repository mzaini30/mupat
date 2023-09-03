<script>
  import { halaman_aktif } from "../state/tombol-aktif";

  let kode_unik;
  let id = "0ce5bba79b60d7fed796f33ec9cb9080"; // id, nama, username, password, kode_unik
  // https://sdmuh4t-smr.sch.id/excalibur/scubus-index.php?halaman=olah-sql&database=0ce5bba79b60d7fed796f33ec9cb9080
  let is_login = false;

  kode_unik = crypto.randomUUID().split("-")[0];

  $halaman_aktif = "profil";
</script>

<div
  class="p-4 [&_.input]:(block border border-blue-500 rounded p-1 w-full mb-3) [&_.tombol]:(bg-green-500 text-white text-center w-full p-3 rounded)"
>
  {#if is_login}{:else}
    <form action="">
      <label>Username</label>
      <input class="input" type="text" />
      <label>Password</label>
      <input type="text" class="input" />
      <input type="submit" class="tombol" value="Login" />
    </form>
    <p class="mt-10 text-center">
      Belum memiliki akun? <a class="underline text-blue-500" href="#/daftar"
        >Daftar</a
      >
    </p>
  {/if}
</div>

<!-- <div class="px-2">
  <p>Kode unik</p>
  <p>{kode_unik}</p>
</div> -->
