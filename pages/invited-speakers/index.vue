<template>
    <div>
        <main class="common-section">
            <Banner></Banner>
            <!-- <h1 class="title">Invited Speakers</h1> -->
            <Breadcrumbs firstRoute="Program" secoundRoute="Invited Speakers"></Breadcrumbs>
            <Title title="Invited Speakers"></Title>
            <div class="content">
                <speaker class="speaker" v-for="item in speakers" :speaker="item"></speaker>
            </div>
        </main>
        <p style="text-align: center; color: #e5716b"><B>Speakers are currently being invited</B></p>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue';
import Speaker from './components/speaker.vue';
import Title from '@/components/layout/Title.vue';


const speakers = reactive<any>([]);

const getSpeakers = async () => {
  let res = await CSRrequest.get('/invited-speaker/pagination', {
    params: {
      page: 1,
      size: 100,
    },
  })
    console.log(res);
  if (res.code === 200) {
    Object.assign(speakers, res.data.records);
  }
};

onMounted(() => {
  getSpeakers();
});



</script>
<style lang="scss" scoped>
.common-section {
    // width: $common-section-width;
    margin: $common-section-margin;
    font-family: $common-section-font-family;

    .title {
        margin-left: 7.4%;
        font-size: 2.5rem;
        color: $main-color;
    }
    .content {
        width: 80%;
        margin: 1rem auto;
        text-align: center;
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;
        gap: 2rem;
        padding: 2rem;
        h1 {
            font-size: 1.5rem;
        }

        .speaker {
          width: calc(100% / 5 - 2rem);

          @media screen and (max-width: 1200px) {
            width: calc(100% / 3 - 2rem);
          }
          @media screen and (max-width: 800px) {
            width: calc(100% / 2 - 2rem);
          }
          @media screen and (max-width: 500px) {
            width: calc(100% - 2rem);
          }
        }
    }
}
</style>