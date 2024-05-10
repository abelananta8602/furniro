<template>
  <q-header reveal elevated class="bg-white text-primary">
    <q-toolbar>
      <q-toolbar-title>
        <div class="q-gutter-sm" style="display: flex; align-items: right">
          <img
            src="images/logofuniro.png"
            alt="Funiro"
            style="margin-top: 15px; height: 20px"
          />
          <span
            class="text-dark"
            style="
              margin-top: 8px;
              margin-left: 5px;
              font-size: 25px;
              font-weight: bold;
            "
            >Furniro</span
          >

          <q-space></q-space>
          <div class="q-gutter-md" style="display: flex">
            <q-btn class="text-dark" flat label="Home" to="/" />
            <q-btn class="text-dark" flat label="Shop" to="/shop" />
            <q-btn class="text-dark" flat label="About" to="/about" />
            <q-btn class="text-dark" flat label="Contact" to="/contact" />
          </div>
          <q-space></q-space>
          <div>
            <q-btn style="color: black" icon="settings" flat round />
            <q-btn style="color: black" icon="search" flat round />
            <q-btn style="color: black" icon="favorite_border" flat round />
            <q-btn style="color: black" icon="shopping_cart" flat round />
          </div>
        </div>
      </q-toolbar-title>
    </q-toolbar>
  </q-header>
  <div class="relative-position" style="height: 600px">
    <q-img
      class="absolute full-width"
      src="images/gambarhomepage.png"
      style="height: 100%; object-fit: cover"
    >
      <div style="height: 330px; width: 550px" class="absolute text-on-image">
        <div class="text-dark q-mt-md text-h6">New Arrival</div>
        <div
          style="color: #b88e2f; font-weight: bold"
          class="text-h3 q-mt-sm q-mb-md"
        >
          Discover Our New Collection
        </div>
        <p class="text-dark">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut elit
          tellus, luctus nec ullamcorper mattis.
        </p>
        <q-btn
          style="background-color: #b88e2f; width: 30%; height: 20%"
          label="Buy Now"
        />
      </div>
    </q-img>
  </div>
  <div class="text-h6 text-center q-mb-lg q-mt-xl">Our Products</div>
  <div class="row q-col-gutter-md">
    <div v-for="product in products" :key="product.id" class="row">
      <div class="q-pa-md q-pl-xl q-ml-xl">
        <div class="row q-col-gutter-md">
          <div
            class="q-pl-md col-xs-12 col-sm-6 col-md-3"
            v-for="product in products"
            :key="product.id"
          >
            <q-card class="product-card">
              <q-img :src="product.image" :alt="product.name">
                <template v-slot:actions>
                  <div
                    class="absolute-top-left text-caption text-white q-pa-xs bg-red"
                    v-if="product.discount"
                  >
                    {{ product.discount }}
                  </div>
                  <div
                    class="absolute-top-right text-caption text-white q-pa-xs bg-green"
                    v-if="product.new"
                  >
                    New
                  </div>
                </template>
              </q-img>
              <q-card-section>
                <div class="text-h6 q-mb-xs">{{ product.name }}</div>
                <div class="text-subtitle2">
                  Rp {{ formatPrice(product.price) }}
                  <s v-if="product.originalPrice" class="q-ml-sm text-grey-6">
                    Rp {{ formatPrice(product.originalPrice) }}
                  </s>
                </div>
              </q-card-section>
              <q-card-actions align="right">
                <q-btn flat icon="shopping_cart">Add to cart</q-btn>
                <q-btn flat icon="favorite_border"></q-btn>
                <q-btn flat icon="share"></q-btn>
                <q-btn flat icon="compare_arrows"></q-btn>
              </q-card-actions>
            </q-card>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="row justify-center q-mt-lg">
    <q-btn label="Show More" color="yellow" />
  </div>
</template>

<script>
export default {
  name: "MyLayoutHeader",
  data() {
    return {
      products: [
        {
          id: 1,
          name: "Slytherine",
          price: "2.500.000",
          originalPrice: "3.500.000",
          discount: "-30%",
          new: false,
          image: "images/chair.jpg",
        },
        {
          id: 2,
          name: "Leviosa",
          price: "2.500.000",
          originalPrice: "",
          discount: "",
          new: true,
          image: "images/chair2.jpg",
        },
        {
          id: 3,
          name: "Lolito",
          price: "7.000.000",
          originalPrice: "14.000.000",
        },
        {
          id: 3,
          name: "Lolito",
          price: "7.000.000",
          originalPrice: "14.000.000",
        },
      ],
    };
  },
  methods: {
    formatPrice(value) {
      // Menghapus titik dan mengonversi string ke number
      const numericValue = Number(value.split(".").join(""));

      // Format ulang ke bentuk mata uang
      const numberFormat = new Intl.NumberFormat("id-ID", {
        style: "currency",
        currency: "IDR",
        minimumFractionDigits: 0,
      });

      return numberFormat.format(numericValue).replace(/Rp/g, "Rp ");
    },
  },
};
</script>

<style>
.product-card {
  max-width: 300px;
  width: 100%;
}
.bg-red {
  background-color: red;
}
.bg-green {
  background-color: green;
}

.relative-position {
  position: relative;
}
.full-width {
  width: 100%;
}
.absolute {
  position: absolute;
  top: 0;
  left: 0;
}
.text-on-image {
  width: 100%;
  bottom: 20px;
  top: 30%;
  left: 75%;
  transform: translateX(-50%);
  text-align: left;
  background-color: #fff3e3 !important;
  padding: 20px;
}
.bg-white {
  background-color: #fff;
}
.text-primary {
  color: #1976d2;
}
</style>
