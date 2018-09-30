<template>
  <div class="hello">
      <div class=" page-top">

        <nav class="navbar navbar-expand navbar-dark bg-dark static-top">

        <a class="navbar-brand mr-1" href="#">Griya Coklat Nglanggeran</a>

        <!-- <button class="btn btn-link btn-sm text-white order-1 order-sm-0" id="sidebarToggle" href="#">
            <i class="fas fa-bars"></i>
        </button> -->

        <div class="d-none d-md-inline-block form-inline ml-auto mr-0 mr-md-3 my-2 my-md-0"></div>
        <!-- Navbar -->
        <ul class="navbar-nav ml-auto ml-md-0">

            <li class="nav-item dropdown no-arrow">
            <a class="nav-link dropdown-toggle" href="#" id="userDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                <i class="fas fa-user-circle fa-fw"></i>
            </a>
            <div class="dropdown-menu dropdown-menu-right" aria-labelledby="userDropdown">
                <a class="dropdown-item" href="#">Settings</a>
                <a class="dropdown-item" href="#">Activity Log</a>
                <div class="dropdown-divider"></div>
                <a class="dropdown-item" href="#" data-toggle="modal" data-target="#logoutModal">Logout</a>
            </div>
            </li>
        </ul>
        </nav>

        <div id="wrapper">

        <!-- Sidebar -->
        <ul class="sidebar navbar-nav">
          <li class="nav-item active">
            <a class="nav-link" href="#!">
              <i class="fas fa-fw fa-tachometer-alt"></i>
              <span>Aplikasi Kasir</span>
            </a>
          </li>
    
          <li class="nav-item">
            <a class="nav-link" href="#">
              <i class="fas fa-fw fa-table"></i>
              <span>Log Transaksi</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">
              <i class="fas fa-fw fa-table"></i>
              <span>Transaksi</span></a>
          </li>
        </ul>

        <div id="content-wrapper">

            <div class="container-fluid">

              <!-- Breadcrumbs-->
              <ol class="breadcrumb">
                <li class="breadcrumb-item">
                  <a href="#">Katalog</a>
                </li>
                <li class="breadcrumb-item active">Overview</li>
              </ol>
            </div>

          <!-- masukan router link ke dalam sini -->
            <div class="row container">
              <div v-for="index in produk" :key="index" class="col-lg-3 py-2">
                <div class="card" style="width: 13rem;">
                  <img class="card-img-top img-fluid" :src="gambarDefault" :alt="index.text">
                  <div class="card-block">
                    <div class="card-text jarak">
                      <p>{{index.text}}</p>
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
                <div class="col-lg-4">
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
          <!-- /.content-wrapper -->
          
        </div>
        <!-- /#wrapper -->

        <!-- Logout Modal-->
        <div class="modal fade" id="logoutModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Mau Pergi ?</h5>
                <button class="close" type="button" data-dismiss="modal" aria-label="Close">
                  <span aria-hidden="true">×</span>
                </button>
              </div>
              <div class="modal-body">Silahkan logout untuk keluar dari program.</div>
              <div class="modal-footer">
                <button class="btn btn-secondary" type="button" data-dismiss="modal">Cancel</button>
                <a class="btn btn-primary" href="#">Logout</a>
              </div>
            </div>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'hello',
  data () {
      return {
        jumlah_beli: 0,
        hasLogin: true,
        gambarDefault: 'static/img/default.jpg',
        produk: [{'text': 'Produk 1'}, {'text': 'Produk 2'}, {'text': 'Produk 3'}, {'text': 'Produk 4'}]
      }
  },
  methods: {
    tambah_jumlah() {
      this.jumlah_beli++;
    },
    kurang_jumlah() {
      if(this.jumlah_beli > 0)
        this.jumlah_beli--;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
