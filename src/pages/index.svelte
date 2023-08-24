<script>
  import wali_kelas from "../gambar/beranda/wali kelas.png";
  import ekskul from "../gambar/beranda/ekskul.png";
  import fasilitas from "../gambar/beranda/fasilitas.png";
  import guru from "../gambar/beranda/guru.png";
  import sekolah from "../gambar/beranda/sekolah.png";
</script>

<div
  class="[&_img]:(rounded-[50%] w-15 block mx-auto h-auto) p-4 grid grid-cols-3 gap-2 text-center [&_a]:mb-5"
>
  <a href="#/">
    <img src={sekolah} alt="" />
    <p>Profil Sekolah</p>
  </a>
  <a href="#/">
    <img src={guru} alt="" />
    <p>Info Guru</p>
  </a>
  <a href="#/">
    <img src={wali_kelas} alt="" />
    <p>Info Walas</p>
  </a>
  <a href="#/">
    <img src={ekskul} alt="" />
    <p>Info Ekskul</p>
  </a>
  <a href="#/">
    <img src={fasilitas} alt="" />
    <p>Fasilitas</p>
  </a>
</div>
