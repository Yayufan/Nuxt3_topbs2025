<template>
    <div class="mobile-menu">
        <ol>
            <div>
                <li>
                   <nuxt-link to="/" @click="closeMenu"> <img src="/img/bugle.svg" alt="">
                    Home</nuxt-link>
                </li>
            </div>
            <div v-for="item in menu">
                <li @click="item.isActive = !item.isActive">
                    <img :src="'/img/' + item.icon" alt="">
                    {{ item.title }}
                    <img v-if="item.submenu" class="arrow" :class="{ 'is-active': item.isActive }"
                        src="@/public/img/chevron-down.svg" alt="">
                </li>
                <div class="submenu" :class="{ 'is-open': item.isActive }">
                    <nuxt-link v-for="submenu in item.submenu" :to="submenu.link" @click="closeMenu">{{ submenu.title }}</nuxt-link>
                </div>
            </div>
            <div>
                <li>
                    <img src="/img/book.svg" alt="">
                    Login
                </li>
            </div>
        </ol>
    </div>
</template>
<script lang="ts" setup>

const emits = defineEmits(['closeMenu']);

const closeMenu = () => {
    emits('closeMenu');
}

const menu = reactive([
    {
        title: 'TOPBS & IOPBS', icon: 'bulb.svg', isActive: false, submenu: [
            { title: 'Message from President', link: '/message-from-president' },
            { title: 'Conference Information', link: '/conference-information' },
            { title: 'Organizing Committee', link: '/organizing-committee' },
            { title: 'Board Member', link: '/board-member' },
            { title: 'Download Center', link: '/download-center' },
            { title: 'Activity Photos', link: '/activity-photos' },
        ]
    },
    {
        title: 'Program', icon: 'cloud.svg', isActive: false, submenu: [
            { title: 'Program at a Galance', link: '/program-at-a-glance' },
            { title: 'Scientific Program', link: '/scientific-program' },
            { title: 'Social Program', link: '/social-program' },
            { title: 'Invited Speakers', link: '/invited-speakers' },
            { title: 'Program Book Download', link: '/program-book-download' },


        ]
    },
    {
        title: 'Registration', icon: 'calendar.svg', isActive: false, submenu: [
            { title: 'Registration Guidelines', link: '/registration-guidelines' },
            { title: 'Register Now', link: '/register-now' },

        ]
    },
    {
        title: 'Call for Abstract', icon: 'bachelor-cap.svg', isActive: false, submenu: [
            { title: 'Submission Guidelines', link: '/submission-guidelines' },
            { title: 'Abstract Submission', link: '/abstract-submission' },

        ]
    },
    {
        title: 'Sponsorship', icon: 'quill.svg', isActive: false, submenu: [
            { title: 'List of Sponsors', link: '/list-of-sponsors' },
        ]
    },
    {
        title: 'General Information', icon: 'shop.svg', isActive: false, submenu: [
            { title: 'Accommodation', link: '/accommodation' },
            { title: 'Video', link: '/video' },
            { title: 'Venue', link: '/venue' },
            { title: 'Transportation', link: '/transportation' },
            { title: 'Travel', link: 'https://www.travel.taipei/en' },
            { title: 'Contact Us', link: '/contact-us' },
        ]
    }
])
</script>
<style lang="scss" scoped>
.mobile-menu {
    background-color: #F0F0F0;
    width: 100%;
    border-top: 8px solid $main-color;

    ol {
        list-style: none;
        padding: 0;
        margin-left: 6vw;

        li {
            padding: 1rem;
            font-size: 1.5rem;
            font-weight: bold;
            color: $main-content-color;

            img {
                width: 1.5rem;
                margin-right: 0.5rem;
                position: relative;
                top: 3px;
            }

            .arrow {
                width: 1rem;
                margin-left: 1rem;
                transform: rotateZ(-90deg);
                position: relative;
                top: 1px;
            }

            .is-active {
                transform: rotateZ(0deg);
            }

            &:hover {
                cursor: pointer;
            }
        }

        .submenu {
            overflow: hidden;
            max-height: 0px;
            transition: 0.5s;
            font-size: 16px;

            a {
                font-size: 1.2rem;
                font-weight: bold;
                display: block;
                color: $main-content-color;
                padding: 0.5rem 0;
            }

            &.is-open {
                overflow: auto !important;
                max-height: none !important;
                margin-left: 15vw;
                font-size: 16px;
            }
        }
    }
}
</style>