<script>
  import wali_kelas from "../gambar/beranda/wali kelas.png";
  import ekskul from "../gambar/beranda/ekskul.png";
  import fasilitas from "../gambar/beranda/fasilitas.png";
  import guru from "../gambar/beranda/guru.png";
  import sekolah from "../gambar/beranda/sekolah.png";
  import { halaman_aktif } from "../state/tombol-aktif";

  $halaman_aktif = "index";
</script>

<div
  class="[&_img]:rounded-[50%] [&_img]:w-[3.75rem] [&_img]:block [&_img]:mx-auto [&_img]:h-auto p-4 grid grid-cols-3 gap-2 text-center [&_a]:mb-5"
>
  <a href="#/tulisan/2">
    <img src={sekolah} alt="" />
    <p>Profil Sekolah</p>
  </a>
  <a href="#/tulisan/3">
    <img src={guru} alt="" />
    <p>Info Guru</p>
  </a>
  <a href="#/tulisan/4">
    <img src={wali_kelas} alt="" />
    <p>Info Walas</p>
  </a>
  <a href="#/tulisan/5">
    <img src={ekskul} alt="" />
    <p>Info Ekskul</p>
  </a>
  <a href="#/tulisan/6">
    <img src={fasilitas} alt="" />
    <p>Fasilitas</p>
  </a>
</div>
