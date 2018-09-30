<template>
    <div class="pointofsale">
        <!-- masukan router link ke dalam sini -->
            <div class="row container">
              <div v-for="item in produk" :key="item" class="col-lg-3 py-2">
                <div class="card" style="width: 13rem;">
                  <img class="card-img-top img-fluid" :src="gambarDefault" alt="Card image cap">
                  <div class="card-block">
                    <div class="card-text jarak">
                      <p>{{item.text}}</p>
                      <li>Nama Produk</li>
                      <li>Price</li>
                      <li>Unit</li>
                    </div>
                  </div>
                </div>
              </div>    
            </div>

            <!-- bagian konsol bawah -->
              <div class="container-fluid my-auto fixed-bottom console bg-light">
                <div class="col-lg-3">
                  <div class="sekrol">
                    <li>
                      <span class="kiri">Coklat A</span>
                      <div class="kanan">
                        <button class="bulet" @click="kurang_jumlah">-</button>
                        <input v-model="jumlah_beli" class="kolom_pendek"/>
                        <button class="bulet" @click="tambah_jumlah">+</button>
                      </div>
                    </li>
                  </div>
                </div>
              </div>
            <!-- /.bagian konsol bawah -->
    </div>
</template>

<script>
export default {
    name: 'pointofsale',
    data() {
        return {
            gambarDefault: 'static/img/default.jpg',
            produk: [{'text': 'Produk 1'}, {'text': 'Produk 2'}, {'text': 'Produk 3'}, {'text': 'Produk 4'}]
        }
    }
}
</script>

<style>
  .console {
    z-index: 300 !important; 
    height: 125px;
  }

  .kolom_pendek {
    width: 23px;
    height: 20px;
    text-align: center;
  }

  .bulet {
    border-radius: 50%;
  }

  .jarak {
    padding-left: 3px;
  }

  li {
    list-style-type: none;
    font-size: 0.9em;
  }

  .sekrol {
    /* overflow:scroll; */
    height: 125px;
    overflow-y:scroll;
  }

  .sekrol li {
    margin-top: 10px;
    clear: both;
  }

  .kiri {
    float: left;
  }

  .kanan {
    float: right;
    margin-right: 10px;
  }
</style>
