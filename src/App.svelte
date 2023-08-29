<script>
  import Router from "svelte-spa-router";
  import Gelombang from "./komponen/gelombang.svelte";
  // @ts-ignore
  import routes from "virtual:generated-pages-svelte";
  import "@unocss/reset/tailwind.css";
  // import "warna-tailwind/warna.css";
  import "./App.css";
  import "uno.css";
  import stat_aja from "stat-aja";
  import logo from "./gambar/logo.png";
  import { halaman_aktif } from "./state/tombol-aktif";

  // stat_aja({ judul: "Judul Aplikasi", tipe: "Aplikasi Android" });
</script>

<div class="bg-[#a7f3d0] w-full h-25 absolute top-0 left-0"></div>
<div class="p-2 z-99 relative">
  <div class=" inline-block">
    <div class="grid grid-cols-2">
      <img class="h-auto w-[70px] block mx-auto" src={logo} alt="" />
      <div>
        <p class=" text-xl">MUP4T</p>
        <p class="text-[12px] text-teal-800">Sekolah Tahfidz Al-Qur'an</p>
      </div>
    </div>
  </div>
</div>
<div class="scale-y-[-1] -mt-15">
  <Gelombang></Gelombang>
</div>
<div class="mb-20">
  <Router {routes} />
</div>
<div
  class="bawah fixed bottom-0 [&_.aktif]:text-green-600 left-0 w-full bg-white shadow shadow-gray-500 grid grid-cols-4 [&_a]:(p-2 text-center text-sm text-gray-700) [&_a_span]:(block mx-auto text-[20px] mb-1)"
>
  <a href="#/" class={$halaman_aktif == "index" ? "aktif" : null}
    ><span class="i-material-symbols:home"></span> Home</a
  >
  <a href="#/ppdb" class={$halaman_aktif == "ppdb" ? "aktif" : null}
    ><span class="i-material-symbols:person-add"></span> PPDB</a
  >
  <a href="#/informasi" class={$halaman_aktif == "informasi" ? "aktif" : null}
    ><span class="i-bi:info-circle-fill"></span> Informasi</a
  >
  <a href="#/profil" class={$halaman_aktif == "profil" ? "aktif" : null}
    ><span class="i-material-symbols:person"></span> Profil</a
  >
</div>
