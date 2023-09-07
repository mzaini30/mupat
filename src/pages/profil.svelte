<script>
  import { halaman_aktif } from "../state/tombol-aktif";
  import localforage from "localforage";
  import toast from "only-toast";
  import api from "../data/api.yml";
  import excaliburZen from "excalibur-zen";

  let kode_unik;
  // let id = "0ce5bba79b60d7fed796f33ec9cb9080"; // id, nama, username, password, kode_unik
  // https://sdmuh4t-smr.sch.id/excalibur/scubus-index.php?halaman=olah-sql&database=0ce5bba79b60d7fed796f33ec9cb9080
  let is_login = false;
  let username, password;
  let data_profil = {};
  let is_admin = false;

  async function cek_is_login() {
    let ceknya = await localforage.getItem("is_login");
    if (ceknya && ceknya == true) {
      is_login = true;
    }
    let ambil_data_profil = await localforage.getItem("data_profil");
    if (ambil_data_profil) {
      data_profil = ambil_data_profil;
    }
  }
  cek_is_login();

  kode_unik = crypto.randomUUID().split("-")[0];

  $halaman_aktif = "profil";

  async function keluar() {
    localforage.setItem("is_login", false);
    is_login = false;
  }

  async function mulai_login() {
    let yuk_login = await excaliburZen(api.server, {
      id: api.auth,
      kunci: "cek-kombinasi-username-dan-password",
      username,
      password,
    });
    yuk_login = await yuk_login.json();
    let banyaknya = yuk_login[0].banyak;
    if (banyaknya == 1) {
      // jika benar
      is_login = true;
      localforage.setItem("is_login", true);
      let ambil_datanya = await excaliburZen(api.server, {
        id: api.auth,
        kunci: "ambil-isinya",
        username,
        password,
      });
      ambil_datanya = await ambil_datanya.json();
      data_profil = ambil_datanya[0];
      localforage.setItem("data_profil", data_profil);
      toast(`Selamat datang ${data_profil.nama}`);
      if (data_profil.username == "admin") {
        is_admin = true;
      } else {
        is_admin = false;
      }
    } else {
      toast("Kombinasi username dan password salah");
      username = "";
      password = "";
      // jika salah
    }
  }
</script>

<div
  class="p-4 [&_.input]:(block border border-blue-500 rounded p-1 w-full mb-3) [&_.tombol]:(bg-green-500 text-white text-center w-full p-3 rounded)"
>
  {#if is_login}
    <!-- <pre>{JSON.stringify(data_profil, null, 2)}</pre> -->
    <h1 class="text-[30px]">{data_profil.nama}</h1>
    <p>{data_profil.kode_unik}</p>
    {#if is_admin}
      <a
        class="w-full rounded bg-green-500 p-2 text-white block text-center mt-3"
        href="https://bea493d6-75bf-4a34-92bb-1660cc05090b.vercel.app/#/tulisan-baru"
        >Dashboard Admin</a
      >
    {/if}
    <div
      class="grid pt-4 grid-cols-2 gap-4 [&>*]:(bg-red-500 text-white block text-center p-3 rounded)"
    >
      <button on:click={keluar}>Logout</button>
      <a href="#/ganti-password/{encodeURIComponent(data_profil.username)}"
        >Ganti Password</a
      >
    </div>
  {:else}
    <form action="" on:submit|preventDefault={mulai_login}>
      <label>Username</label>
      <input class="input" type="text" bind:value={username} />
      <label>Password</label>
      <input type="password" bind:value={password} class="input" />
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
