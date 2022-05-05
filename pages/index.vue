<template>
  <div>
    <!--- navigation section -->
    <TheHeader :menu_data="menu" />
    <!-- slider section -->
    <div
      class="
        container-full
        bg-dark
        slider_background
        d-flex
        justify-content-center
      "
      :style="{ 'background-image': `url(${slider[0].acf.picture})` }"
    >
      <div class="row align-items-center">
        <div class="col-12 text-center">
          <p class="text-dark arraval-text">{{ slider[0].acf.slider_title }}</p>
          <p class="stext-dark display-6">{{ slider[0].acf.slider_caption }}</p>
          <a :href="slider[0].acf.slider_button_link"
            ><p class="text-dark h5 underline">
              {{ slider[0].acf.slider_butten_text }}
            </p></a
          >
        </div>
      </div>
    </div>
    <!-- trends title section -->
    <div id="trend" class="container pt-5 pb-4">
      <div class="row pt-5">
        <div class="col-12 text-center">
          <p class="text-dark h1">Trending</p>
        </div>
      </div>
    </div>
    <!-- trends section -->
    <div class="container pb-5 pt-2">
      <div class="row">
        <div
          v-for="trenditem in trend"
          :key="trenditem.id"
          class="col-lg-4 col-md-4"
        >
          <div
            class="service_background pt-5 ps-4 text-start"
            :style="{
              'background-image': `url(${trenditem.acf.trend_image.url})`,
            }"
          ></div>
        </div>
      </div>
    </div>

    <!-- collection section -->
    <div class="container-full py-5">
      <div class="row gx-0 gy-5 g-md-0 g-lg-0">
        <div class="col-lg-7 col-md-7 collec-sec-back">
          <img :src="baner[0].acf.baner_left_image" alt="" class="w-100" />
        </div>
        <div
          class="col-lg-5 col-md-5 text-start py-5 sandel-background"
          :style="{
            'background-image': `url(${baner[0].acf.baner_right_imagr})`,
          }"
        >
          <p class="text-end display-5 collec-text">
            {{ baner[0].acf.baner_text_top }} <br />
            {{ baner[0].acf.baner_text_bottem }}
          </p>
        </div>
      </div>
    </div>

    <!-- products section -->
    <div id="popular" class="container py-5">
      <div class="row">
        <div class="col-12 text-center pb-4">
          <p class="text-dark h1">Most popular</p>
        </div>
      </div>
      <div class="row">
        <div
          v-for="product in popular_products"
          :key="product.id"
          class="col-lg-3 col-md-3 text-center img_hover"
        >
          <img class="res-img" :src="product.acf.popular_image" alt="" />
          <p class="text-cente text-muted">
            {{ product.acf.pupolar_image_title }}
          </p>
        </div>
      </div>
    </div>

    <!-- devider section -->
    <div class="container py-md-5 my-md-5">
      <div class="row">
        <div class="col-12">
          <hr />
        </div>
      </div>
    </div>

    <!-- discount section -->
    <div id="discount" class="container py-2 py-md-5 py-lg-5 text-center my-5">
      <p class="text-muted">{{ discount[0].acf.discount_title }}</p>
      <p class="display-6">
        <span class="discount-number">{{
          discount[0].acf.discount_persentage
        }}</span>
        {{ discount[0].acf.discount_persentage_black_text }}
      </p>
      <a :href="discount[0].acf.discount_button_link">
        <p class="text-dark h5 underline">
          {{ discount[0].acf.discount_button_text }}
        </p>
      </a>
    </div>

    <!-- discount picture -->
    <div class="container py-md-5 py-lg-5">
      <div class="row">
        <div
          v-for="discount_baner_item in discount_baner"
          :key="discount_baner_item.id"
          class="col-lg-6 col-md-6 pe-md-5 pe-lg-5"
        >
          <div
            class="diccount-bg"
            :style="{
              'background-image': `url(${discount_baner_item.acf.discount_baner_image})`,
            }"
          ></div>
          <p class="text-center disc-img-title pt-3">
            {{ discount_baner_item.acf.discount_baner_image_title }}
          </p>
        </div>
      </div>
    </div>

    <!-- social media -->
    <div id="contact" class="container py-5 text-center my-5">
      <p class="h2">{{ social_media[0].acf.social_media_title }}</p>
      <p class="text-muted">{{ social_media[0].acf.social_media_subtitle }}</p>
      <hr class="my-5" />
      <a
        v-for="social_icon in social_icons"
        :key="social_icon.id"
        :href="social_icon.acf.icon_link"
      >
        <img
          :src="social_icon.acf.social_icon"
          alt=""
          class="h5 text-muted ps-2"
        />
      </a>
    </div>
    <!-- footer -->
    <TheFooter :footer_data="copyright" />
  </div>
</template>

<script>
import axios from "axios";
import TheHeader from "@/components/Navigation/TheHeader";
import TheFooter from "@/components/TheFooter";
export default {
  components: {
    TheHeader,
    TheFooter,
  },
  asyncData(context) {
    const menu = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/menu"
    );
    const slider = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/slider"
    );
    const trend = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/trend"
    );
    const baner = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/baner"
    );
    const popular_products = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/popular_products"
    );
    const discount = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/discount"
    );
    const discount_baner = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/discount_baner"
    );
    const social_media = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/social_media"
    );
    const social_icons = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/social_icons"
    );
    const copyright = axios.get(
      "https://backend.52hertzcouture.com/wp-json/wp/v2/copyright"
    );

    return axios
      .all([
        menu,
        slider,
        trend,
        baner,
        popular_products,
        discount,
        discount_baner,
        social_media,
        social_icons,
        copyright,
      ])
      .then(
        axios.spread((...responses) => {
          const menu = responses[0];
          const slider = responses[1];
          const trend = responses[2];
          const baner = responses[3];
          const popular_products = responses[4];
          const discount = responses[5];
          const discount_baner = responses[6];
          const social_media = responses[7];
          const social_icons = responses[8];
          const copyright = responses[9];

          return {
            menu: menu.data,
            slider: slider.data,
            trend: trend.data,
            baner: baner.data,
            popular_products: popular_products.data,
            discount: discount.data,
            discount_baner: discount_baner.data,
            social_media: social_media.data,
            social_icons: social_icons.data,
            copyright: copyright.data,
          };
        })
      )
      .catch((e) => {
        context.error(e);
      });
  },
};
</script>


<style scoped>
/*slide component style */
.slider_background {
  background-repeat: no-repeat;
  background-position: top center;
  background-size: cover;
  min-height: 70vh;
}

@media (max-width: 768px) {
  .slider_background {
    background-size: 100% 100%;
    min-height: 40vh;
  }
}

/* trends component style */
.service_background {
  background-repeat: no-repeat;
  background-position: center center;
  background-size: 100% 100%;
  min-height: 50vh;
}

@media (max-width: 768px) {
  .service_background {
    background-position: center;
    background-size: 100% 100%;
    min-height: 70vh;
  }
}

.sandel-background {
  background-repeat: no-repeat;
  background-position: center right;
}

/* diccount background */
.diccount-bg {
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  min-height: 90vh;
}
</style>
