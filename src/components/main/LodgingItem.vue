<script setup>
import { ref } from 'vue';

const liked = ref(false);
const clickLiked = () => {
  liked.value = !liked.value;
} ;

const props= defineProps({
      picture: String,
      alt: String,
      title: String,
      period: String,
      price: String,
      rating: Number,
      badge: String

});
</script>

<template>
  <div class="item po-rel">
    <img :src="props.picture" alt="props.alt">
    <div class="title">{{ props.title }}</div>
    <div class="per_pri">{{ props.period}}</div>
    <div class="per_pri">{{ props.price}}
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" aria-hidden="true" role="presentation" focusable="false" style="display: block; height: 8px; width: 8px; fill: currentcolor;"><path fill-rule="evenodd" d="m15.1 1.58-4.13 8.88-9.86 1.27a1 1 0 0 0-.54 1.74l7.3 6.57-1.97 9.85a1 1 0 0 0 1.48 1.06l8.62-5 8.63 5a1 1 0 0 0 1.48-1.06l-1.97-9.85 7.3-6.57a1 1 0 0 0-.55-1.73l-9.86-1.28-4.12-8.88a1 1 0 0 0-1.82 0z"></path></svg>
        {{ props.rating }}
    </div>
    <div v-if="props.badge" class="badge">{{ props.badge }}</div>
    <div v-if="liked"><button @click="clickLiked" class="heart"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640"><path style="fill: white" d="M305 151.1L320 171.8L335 151.1C360 116.5 400.2 96 442.9 96C516.4 96 576 155.6 576 229.1L576 231.7C576 343.9 436.1 474.2 363.1 529.9C350.7 539.3 335.5 544 320 544C304.5 544 289.2 539.4 276.9 529.9C203.9 474.2 64 343.9 64 231.7L64 229.1C64 155.6 123.6 96 197.1 96C239.8 96 280 116.5 305 151.1z"/></svg></button></div>
    <div v-else><button @click="clickLiked" class="heart"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640"><path style="fill: black; stroke:aliceblue; stroke-width: 30px; fill-opacity: 0.5;" d="M305 151.1L320 171.8L335 151.1C360 116.5 400.2 96 442.9 96C516.4 96 576 155.6 576 229.1L576 231.7C576 343.9 436.1 474.2 363.1 529.9C350.7 539.3 335.5 544 320 544C304.5 544 289.2 539.4 276.9 529.9C203.9 474.2 64 343.9 64 231.7L64 229.1C64 155.6 123.6 96 197.1 96C239.8 96 280 116.5 305 151.1z"/></svg></button></div>
  </div>

</template>

<style scoped>

.po-rel {position: relative;}
.po-rel .badge { position: absolute; top: 10px; left: 10px; 
  background-color: #ffffffab; padding: 7px 12px; 
  border-radius: 25px; font-size: 0.8rem; ;
}
.heart { position: absolute; top: 4px; right: 1px; 
  width: 40px; height: 40px;
  background: transparent;  padding: 0; 
  border: none; cursor: pointer;
}
.heart svg { width: 30px; height: 30px; 
  transition: transform 0.3s ease;}
.heart:hover svg{ transform: scale(1.1);}

.item { width: 180px; }
.item img { width: 180px; height: 180px; border-radius: 16px; object-fit: cover;}
svg { display: inline !important; }
.item .title { color: #000; font-size: 0.9rem;}
.item .per_pri { color: #000000a9; font-size: 0.8rem; margin-top: 3px; }

@media (min-width: 1887px) {
.item { width: 240px; }
.item img { width: 240px; height: 240px; border-radius: 16px; object-fit: cover;}
}

</style>
