<template>
    <div>
        <main class="common-section">
            <Banner></Banner>
            <Breadcrumbs firstRoute="About" secoundRoute="List of Sponsors"></Breadcrumbs>
            <Title title="List of Sponsors"></Title>

            <div class="content">
                <div v-for="sponsor in sponsorsList" class="level-box">
                    <div class="level-svg-box">
                        <img :src="sponsor.imgSrc" alt="">
                    </div>
                    <div v-for="sponsorLogoList in sponsor.sponsorLogos" class="sponsor-logo-box">
                        <div v-for="logo in sponsorLogoList" class="sponsor-logo-item">
                            <img :src="logo" alt="">
                        </div>
                    </div>
                    <el-divider></el-divider>
                </div>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue'
import Title from '@/components/layout/Title.vue'

import DiamondLogo from '../assets/img/sponsors/level-svg/TOPBS&IOPBS_diamond.png'
import PlatinumLogo from '../assets/img/sponsors/level-svg/TOPBS&IOPBS_platinum.png'
import GoldLogo from '../assets/img/sponsors/level-svg/TOPBS&IOPBS_gold.png'
import SilverLogo from '../assets/img/sponsors/level-svg/TOPBS&IOPBS_silver.png'
import BronzeLogo from '../assets/img/sponsors/level-svg/TOPBS&IOPBS_bronze.png'

useSeoMeta({
    title: 'List of Sponsors - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Explore the list of sponsors for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page is currently under construction, but stay tuned for updates showcasing the esteemed sponsors who support and contribute to the success of the conference.',
    keywords: 'List Of Sponsors, Sponsors, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

const sponsorConfig = [
    { key: 'diamond Sponsor', path: '@/assets/img/sponsors/diamond/*.{png,jpg,svg,jpeg}' },
    { key: 'platinum Sponsor', path: '@/assets/img/sponsors/platinum/*.{png,jpg,svg,jpeg}' },
    { key: 'gold Sponsor', path: '@/assets/img/sponsors/gold/*.{png,jpg,svg,jpeg}' },
    { key: 'silver Sponsor', path: '@/assets/img/sponsors/silver/*.{png,jpg,svg,jpeg}' },
    { key: 'bronze Sponsor', path: '@/assets/img/sponsors/bronze/*.{png,jpg,svg,jpeg}' },
]

const cols = ref(4);
const allGroupedSponsors = sponsorConfig.map(config => {
    const results: Record<string, string[][]> = {};

    sponsorConfig.forEach(config => {


        let modules: Record<string, string>;

        switch (config.key) {
            case 'diamond Sponsor':
                modules = import.meta.glob('@/assets/img/sponsors/diamond/*.{png,jpg,jpeg,svg}', { eager: true, query: '?url', import: 'default' });
                break;
            case 'platinum Sponsor':
                modules = import.meta.glob('@/assets/img/sponsors/platinum/*.{png,jpg,jpeg,svg}', { eager: true, query: '?url', import: 'default' });
                break;
            case 'gold Sponsor':
                modules = import.meta.glob('@/assets/img/sponsors/gold/*.{png,jpg,jpeg,svg}', { eager: true, query: '?url', import: 'default' });
                break;
            case 'silver Sponsor':
                modules = import.meta.glob('@/assets/img/sponsors/silver/*.{png,jpg,jpeg,svg}', { eager: true, query: '?url', import: 'default' });
                break;
            case 'bronze Sponsor':
                modules = import.meta.glob('@/assets/img/sponsors/bronze/*.{png,jpg,jpeg,svg}', { eager: true, query: '?url', import: 'default' });
                break;
            default:
                modules = {};
                break;
        }

        const galleryImages: string[] = Object.values(modules);
        const groupedList: string[][] = [];

        galleryImages.forEach((image, index) => {
            const groupIndex = Math.floor(index / cols.value);
            if (!groupedList[groupIndex]) {
                groupedList[groupIndex] = [];
            }
            groupedList[groupIndex].push(image);
        });

        results[config.key] = groupedList;
    });
    console.log(results);
    return results;
})



const sponsorsList = [
    {
        level: 'Diamond Sponsor',
        imgSrc: DiamondLogo,
        sponsorLogos: allGroupedSponsors[0]['diamond Sponsor']
    },
    {
        level: 'Platinum Sponsor',
        imgSrc: PlatinumLogo,
        sponsorLogos: allGroupedSponsors[1]['platinum Sponsor']
    },
    {
        level: 'Gold Sponsor',
        imgSrc: GoldLogo,
        sponsorLogos: allGroupedSponsors[2]['gold Sponsor']
    },
    {
        level: 'Silver Sponsor',
        imgSrc: SilverLogo,
        sponsorLogos: allGroupedSponsors[3]['silver Sponsor']
    },
    {
        level: 'Bronze Sponsor',
        imgSrc: BronzeLogo,
        sponsorLogos: allGroupedSponsors[4]['bronze Sponsor']
    }
]

console.log(sponsorsList);

</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;


    .content {
        margin: 1rem auto;
        text-align: center;
        width: 90%;

        .level-box {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            gap: 2rem;

            .level-svg-box {
                width: 10rem;
                height: auto;

                img {
                    width: 100%;
                    height: auto;
                }
            }

            .sponsor-logo-box {
                width: 100%;
                display: flex;
                justify-content: center;
                align-items: center;
                gap: 2rem;
                flex-wrap: wrap;
                margin-top: 1rem;

                .sponsor-logo-item {
                    width: calc(100% / 4 - 2rem);
                    height: auto;

                    img {
                        width: 90%;
                        height: auto;
                        max-width: 100%;
                        max-height: 100%;
                        object-fit: cover;
                    }
                }


            }
        }

    }
}
</style>