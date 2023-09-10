<script>
  export let kategori;

  import excaliburZen from "excalibur-zen";
  import api from "../data/api.json";
  import { lexer } from "marked";

  let data = [];

  async function dapatkan_data() {
    let datanya = await excaliburZen(api.server, {
      id: api.tulisan,
      kunci: "ambil-tertentu",
      kategori,
    });
    datanya = await datanya.json();

    data = datanya;
    data = data.map((x) => {
      // ini gambar pertama default
      let gambar_pertama =
        "https://asset.kompas.com/crops/qDmc_rkFp61Qbh8eXzq0yvByids=/0x0:780x520/750x500/data/photo/2019/07/28/5d3d88afe9a3f.jpg";

      //       const markdownText = `Ini adalah gambar pertama ![](https://example.com/gambar1.jpg) dalam teks Markdown.
      // Ini adalah gambar kedua ![](https://example.com/gambar2.jpg).`;

      // Mencari semua tautan gambar dalam format Markdown tanpa teks alternatif
      const imageLinks = x.isi.match(/\!\[\]\(([^)]+)\)/g);

      if (imageLinks) {
        // Ekstrak URL dari tautan gambar
        const imageUrls = imageLinks.map((link) => {
          const match = link.match(/\!\[\]\(([^)]+)\)/);
          if (match && match.length === 2) {
            return match[1]; // URL gambar ada di indeks ke-1
          }
          return null;
        });

        console.log("URL Gambar Pertama:", imageUrls[0]);
        gambar_pertama = imageUrls[0];
      } else {
        console.log("Tidak ada gambar dalam teks Markdown.");
      }

      return {
        id: x.id,
        judul: x.judul,
        isi: x.isi,
        kategori: x.kategori,
        gambar_pertama,
      };
    });
  }
  dapatkan_data();
</script>

<!-- <pre>{JSON.stringify(data, null, 2)}</pre> -->
<div class="p-3 grid grid-cols-1 gap-2">
  {#if data}
    {#each data as x}
      <a href="#/tulisan/{x.id}" class="rounded border block overflow-hidden">
        <img src={x.gambar_pertama} alt="" />
        <span class="p-2 block">{x.judul}</span>
      </a>
    {/each}
  {/if}
</div>
