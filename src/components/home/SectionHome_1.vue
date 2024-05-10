<template>
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
</template>

<script></script>

<style>
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
</style>
