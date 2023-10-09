<script>
  import excaliburZen from "excalibur-zen";
  import api from "../data/api.json";
  import toast from "only-toast";
  import { push } from "svelte-spa-router";

  //   let id = "0ce5bba79b60d7fed796f33ec9cb9080"; // id, nama, username, password, kode_unik
  // https://sdmuh4t-smr.sch.id/excalibur/scubus-index.php?halaman=olah-sql&database=0ce5bba79b60d7fed796f33ec9cb9080
  //   let server = "";
  let nama, username, password;

  async function daftar_baru() {
    let cek_usernamenya_dulu = await excaliburZen(api.server, {
      id: api.auth,
      kunci: "cek-apakah-username-sudah-digunakan",
      username,
    });
    cek_usernamenya_dulu = await cek_usernamenya_dulu.json();
    let banyaknya = cek_usernamenya_dulu[0].banyak;
    if (banyaknya == 0) {
      //   toast("Username belum terdaftar");
      let mulai_mendaftar = await excaliburZen(api.server, {
        id: api.auth,
        kunci: "buat-baru",
        nama,
        username,
        password,
        kode_unik: crypto.randomUUID().split("-")[0],
      });
      if (mulai_mendaftar) {
        toast("Berhasil registrasi");
        push("/profil");
      }
    } else {
      //   console.log("Username sudah terdaftar");
      username = "";
      toast("Username sudah terdaftar");
    }
  }
</script>

<form
  action=""
  class="p-4 [&_.input]:block [&_.input]:border [&_.input]:border-blue-500 [&_.input]:rounded [&_.input]:p-1 [&_.input]:w-full [&_.input]:mb-3 [&_.tombol]:bg-green-500 [&_.tombol]:text-white [&_.tombol]:text-center [&_.tombol]:w-full [&_.tombol]:p-3 [&_.tombol]:rounded"
  on:submit|preventDefault={daftar_baru}
>
  <label for="">Nama</label>
  <input type="text" bind:value={nama} class="input" />
  <label for="">Username</label>
  <input type="text" class="input" bind:value={username} />
  <label for="">Password</label>
  <input type="text" class="input" bind:value={password} />
  <input class="tombol" type="submit" value="Daftar" />
</form>
