<script>
  export let params = {};

  import excaliburZen from "excalibur-zen";
  import api from "../../data/api.json";
  import toast from "only-toast";
  import { push } from "svelte-spa-router";

  let password_lama, password_baru;

  async function mengganti_password() {
    let cek_dulu = await excaliburZen(api.server, {
      id: api.auth,
      kunci: "cek-kombinasi-username-dan-password",
      username: params.username,
      password: password_lama,
    });
    cek_dulu = await cek_dulu.json();
    if (cek_dulu[0].banyak == 1) {
      // username dan password lama sudah sesuai
      let mengubah_password = await excaliburZen(api.server, {
        id: api.auth,
        kunci: "ubah-password",
        username: params.username,
        password: password_baru,
      });
      if (mengubah_password) {
        toast("Password berhasil diubah");
        push("/profil");
      }
    } else {
      toast("Password lama salah");
      password_lama = "";
    }
  }
</script>

<form
  action=""
  class="p-4 [&_.input]:(block border border-blue-500 rounded p-1 w-full mb-3) [&_.tombol]:(bg-green-500 text-white text-center w-full p-3 rounded)"
  on:submit|preventDefault={mengganti_password}
>
  <label for="">Password Lama</label>
  <input type="text" class="input" bind:value={password_lama} />
  <label for="">Password Baru</label>
  <input type="text" class="input" bind:value={password_baru} />
  <input class="tombol" type="submit" value="Ubah" />
</form>
