<template>
    <footer class="pt-5 text-white">
        <div class="container-fluid">
            <div class="row">
                <div class="col-md-5 mb-4">
                    <h4 class="font-weight-bold">TENTANG</h4>
                    <hr
                        style="
                            border-top: 3px solid rgb(226 232 240);
                            border-radius: 0.5rem;
                        "
                    />

                    <p>
                        Toko Sayur Online Terpercaya di Indonesia. Produk Fresh
                        Langsung Dari Pasar & Harga Termurah! Belanja sekarang.
                    </p>
                    <div class="social">
                        <a href="#" class="mr-4" style="color: #265a5c">
                            <i class="fab fa-facebook fa-2x"></i
                        ></a>
                        <a href="#" class="mr-4" style="color: #265a5c">
                            <i class="fab fa-twitter fa-2x"></i
                        ></a>
                        <a href="#" class="mr-4" style="color: #265a5c">
                            <i class="fab fa-instagram fa-2x"></i
                        ></a>
                        <a href="#" style="color: #265a5c">
                            <i class="fab fa-youtube fa-2x"></i
                        ></a>
                    </div>
                </div>
                <div class="col-md-3 mb-4">
                    <h4 class="font-weight-bold">PEMBAYARAN</h4>
                    <hr
                        style="
                            border-top: 3px solid rgb(226 232 240);
                            border-radius: 0.5rem;
                        "
                    />

                    <div class="row">
                        <div class="col-md-4 col-4 mb-3">
                            <div class="card h-100 border-0 rounded-lg shadow">
                                <div class="card-body p-2 text-center">
                                    <img
                                        src="@/assets/payment/BCA.png"
                                        style="width: 50px"
                                    />
                                </div>
                            </div>
                        </div>

                        <div class="col-md-4 col-4 mb-3">
                            <div class="card h-100 border-0 rounded-lg shadow">
                                <div class="card-body p-2 text-center">
                                    <img
                                        src="@/assets/payment/BNI.png"
                                        style="width: 45px"
                                    />
                                </div>
                            </div>
                        </div>

                        <div class="col-md-4 col-4 mb-3">
                            <div class="card h-100 border-0 rounded-lg shadow">
                                <div class="card-body p-2 text-center">
                                    <img
                                        src="@/assets/payment/BRI.png"
                                        style="width: 60px"
                                    />
                                </div>
                            </div>
                        </div>

                        <div class="col-md-4 col-4 mb-3">
                            <div class="card h-100 border-0 rounded-lg shadow">
                                <div class="card-body p-2 text-center">
                                    <img
                                        src="@/assets/payment/GOPAY.png"
                                        style="width: 60px"
                                    />
                                </div>
                            </div>
                        </div>

                        <div class="col-md-4 col-4 mb-3">
                            <div class="card h-100 border-0 rounded-lg shadow">
                                <div class="card-body p-2 text-center">
                                    <img
                                        src="@/assets/payment/indomaret-logo.png"
                                        style="width: 60px"
                                    />
                                </div>
                            </div>
                        </div>

                        <div class="col-md-4 col-4 mb-3">
                            <div class="card h-100 border-0 rounded-lg shadow">
                                <div class="card-body p-2 text-center">
                                    <img
                                        src="@/assets/payment/atm-bersama.jpg"
                                        style="width: 40px"
                                    />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="col-md-4 mb-4">
                    <h4 class="font-weight-bold">KONTAK</h4>
                    <hr
                        style="
                            border-top: 3px solid rgb(226 232 240);
                            border-radius: 0.5rem;
                        "
                    />
                    <p>
                        <i class="fa fa-clock"></i> Toko Buka Setiap Hari :
                        <br />
                        Senin - Minggu ( 06.00 s/d 18.00 )
                    </p>
                    <p>
                        <i class="fa fa-map-marker"></i> Pasar Larangan,
                        Kecamatan Candi, Kabupaten Sidoarjo, Jawa Timur, 61271
                    </p>
                </div>
            </div>

            <div class="row text-center mt-3 pb-3">
                <div class="col-md-12">
                    <hr />
                    &copy; <strong>Bakul Sayur</strong> 2022<br />
                    made with <i class="fa fa-heart"></i> by
                    <a
                        href="http://instagram.com/egaalfy_/"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="font-weight-bold"
                        style="color: #113c4a"
                        >eaf.dev</a
                    >
                </div>
            </div>
        </div>
    </footer>
</template>

<script>
export default {
    name: 'FooterComponent',
};
</script>
