<script>
  import excalibur from "excalibur-zen";
  import api from "../../data/api.json";
  import markdown from "markdown";
  import { marked, parse } from "marked";

  export let params;

  let data = {
    judul: "",
    isi: "",
  };

  async function ambil_data() {
    let datanya = await excalibur(api.server, {
      id: api.tulisan,
      kunci: "dapatkan",
      idnya: params.id,
    });
    datanya = await datanya.json();
    data = datanya[0];
    // console.log(markdown.markdown.toHTML(data.isi));
  }
  ambil_data();
</script>

<!-- {JSON.stringify(data)} -->
<div class="prose max-w-full p-3">
  <h1>{data.judul}</h1>
  {@html marked(data.isi)}
</div>
