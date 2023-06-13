<template>
   <v-container :fluid="true" class="pa-2 pa-xl-4 presentation">
      <v-row class="justify-center presentation__title">
         <v-col cols="auto">
            <span class="d-inline-block h1-text text-center">Zadbaj o leśne zwierzęta razem z nami</span>
         </v-col>
      </v-row>
      <v-row class="justify-space-around presentation__item">
         <v-col>
            <div class="presentation__info">
               <span class="presentation__info-text">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Odio quo expedita voluptate, commodi ullam id inventore accusamus magnam consequuntur voluptatum nulla laborum in aperiam, nemo officia qui. Voluptatum, quasi. Sunt officiis dolorum vero reiciendis consequatur nam doloremque cumque repellat, voluptatum eum dicta id hic qui rerum voluptatibus optio ullam voluptas doloribus error ab! Porro, officiis repellendus perspiciatis vero esse accusantium beatae ipsam, nesciunt quae perferendis debitis nihil, explicabo architecto possimus! Tenetur consequuntur amet optio nesciunt eaque maxime ullam totam harum cum? Officiis illum quos similique maiores nesciunt animi quod repellendus voluptate laudantium. Fugit, consequatur facere. Hic incidunt sequi exercitationem neque voluptas! Qui fuga architecto fugit ipsum. Est quia eius reiciendis dolores quis voluptatum ullam ad laboriosam adipisci qui, non ut provident autem illo fugiat itaque quae dolor ea odio nam eos accusantium placeat. Cupiditate temporibus fugit quae minus ex sequi magni laborum voluptas quia, architecto velit eos deserunt! Quam, quod.</span>
               <button type="button" class="collapser">Rozwiń</button>
               <div class="blur"></div>
            </div>
         </v-col>
         <v-col cols="6">
            <div class="presentation__img">
               <content-plug />
            </div>
         </v-col>
      </v-row>
      <v-row class="justify-space-around presentation__item">
         <v-col cols="6">
            <div class="presentation__img">
               <content-plug />
            </div>
         </v-col>
         <v-col>
            <div class="presentation__info">
               <span class="presentation__info-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda pariatur facilis corporis optio dignissimos soluta fugiat quas ad autem quia, animi itaque minima corrupti necessitatibus delectus alias? Sunt maiores eos aliquam! Cupiditate ipsam delectus sint expedita doloremque earum natus omnis exercitationem fuga error? Sunt inventore vel molestiae esse ratione exercitationem repellendus assumenda rem possimus deleniti labore, officia, dolore, consequatur iste perferendis. Facere repellat repudiandae nisi odio ipsa et nostrum corporis, eos aperiam, iure tenetur esse, nulla dolorem voluptate dolore officiis alias vero blanditiis totam cum consequuntur dicta illo reiciendis. Dolor in accusamus fugiat quia sunt voluptatum error asperiores architecto quaerat!</span>
               <button type="button" class="collapser">Rozwiń</button>
               <div class="blur"></div>
            </div>
         </v-col>
      </v-row>
   </v-container>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue';
import ContentPlug from '@/components/ContentPlug.vue';

export default defineComponent({
   name: 'VPresentation',

   components: {
      ContentPlug
   },

   setup() {
      const defineMinHeight = (element: HTMLElement) => {
         const minHeight = (document.querySelector('.presentation__img') as HTMLElement).offsetHeight;
         const maxHeight = (element.firstChild as HTMLElement).offsetHeight;

         element.dataset.minHeight = `${minHeight}px`;
         element.dataset.maxHeight = `${maxHeight}px`;

         const collapser = element.querySelector('.collapser') as HTMLElement;
         if (collapser) {
            if (maxHeight > minHeight) {
               collapser.style.display = 'block';
            } else {
               collapser.style.display = 'none';
            }
         }

         const blur = element.lastChild as HTMLElement;
         if (blur) {
            if (maxHeight > minHeight) {
               blur.style.display = 'block';
            } else {
               blur.style.display = 'none';
            }
         }
      }

      const toggleText = (event: Event) => {
         const target = event.target as HTMLElement;

         const infoBlock = target.closest('.presentation__info') as HTMLElement;
         if (infoBlock) {
            const minHeight = parseInt(infoBlock.dataset.minHeight as string);
            const maxHeight = parseInt(infoBlock.dataset.maxHeight as string);
            const collapser = infoBlock.querySelector('.collapser');

            if (infoBlock.classList.contains('opened')) {
               infoBlock.style.height = `${minHeight}px`;
               infoBlock.classList.remove('opened');
               if (collapser) {
                  collapser.textContent = 'Rozwiń';
               }
            } else {
               infoBlock.style.height = `${maxHeight}px`;
               infoBlock.classList.add('opened');
               if (collapser) {
                  collapser.textContent = 'Zwiń';
               }
            }
         }
      };

      onMounted(() => {
         const infoBlocks = document.querySelectorAll('.presentation__info');
         infoBlocks.forEach((element) => {
            defineMinHeight(element as HTMLElement);
         });

         const collapsers = document.querySelectorAll('.presentation__info .collapser');
         collapsers.forEach((button) => {
            button.addEventListener('click', toggleText);
         });
      });

      return {
         defineMinHeight
      };
   }
});
</script>





<style lang="scss" scoped>
.presentation__info,
.presentation__img {
   height: calc(33.3vh);
}

.presentation__info {
   overflow: hidden;
   position: relative;
   transition: 0.7s ease;

   & .collapser {
      padding: 5px 10px;
      border-radius: 5px;
      background: #43A047;
      color: #fff;
      opacity: 0.7;
      position: absolute;
      left: 50%;
      bottom: 5px;
      transform: translateX(-50%);
      z-index: 2;
      transition: 0.25s;

      &:hover {
         opacity: 1;
      }
   }

   & .blur {
      width: 100%;
      height: 40%;
      background: linear-gradient(to bottom, transparent 0%, rgba(255, 255, 255, .7) 35%, #fff 100%);
      position: absolute;
      left: 0;
      bottom: 0;
      z-index: 1;
      transition: 0.7s;
   }

   &.opened .collapser {
      opacity: 0.3;

      &:hover {
         opacity: 1;
      }
   }

   &.opened .blur {
      opacity: 0;
   }
}
</style>