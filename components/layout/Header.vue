<template>
    <header class="header">
        <div class="hamburger-icon">
            <div class="container">
                <div class="hamburger" :class="{ 'is-active': isActive }" id="hamburger-1" @click="openMenu">
                    <span class="line"></span>
                    <span class="line"></span>
                    <span class="line"></span>
                </div>

            </div>
        </div>
        <!-- <div class="logo-section">
            <nuxt-link to="/"><img src="/img/logo.png" alt="" @click="closeMenu"></nuxt-link>
        </div> -->
        <div class="user-icon" @click="headToMemberCenter">
            <img src="/img/user.svg" alt="" >
        </div>
    </header>
</template>
<script lang="ts" setup>


const router = useRouter();

const isActive = ref(false);
const props = defineProps<{
    isActive: boolean;
}>();

watch(() => props.isActive, (value) => {
    isActive.value = value;
});


const openMenu = () => {
    isActive.value = !isActive.value;
    emits('openMenu', isActive.value);
}

const closeMenu = () => {
    isActive.value = false;
    emits('openMenu', isActive.value);
}

const emits = defineEmits(['openMenu']);

const headToMemberCenter = () => {
    console.log('headToMemberCenter');
    router.push('/member-center');
}


</script>
<style lang="scss" scoped>
.header {
    display: flex;
    justify-content: center;

    .logo-section {
        width: 7vw;
        min-width: 100px;

        img {
            width: 100%;
        }
    }
    
    .hamburger-icon {
        position: absolute;
        left: 0;
        top: 0.8vw;
        display: none;
        padding: 20px;
        z-index: 9999;

        .hamburger .line {
            width: 1.5rem;
            height: 3px;
            background-color: #000;
            margin-top: 5px;
            display: block;
            -webkit-transition: all 0.3s ease-in-out;
            -o-transition: all 0.3s ease-in-out;
            transition: all 0.3s ease-in-out;

            &:hover {
                cursor: pointer;
            }
        }

        #hamburger-1.is-active .line:nth-child(2) {
            opacity: 0;
        }

        #hamburger-1.is-active .line:nth-child(1) {
            -webkit-transform: translateY(7.9px) rotate(47deg);
            -ms-transform: translateY(7.9px) rotate(47deg);
            -o-transform: translateY(7.9px) rotate(47deg);
            transform: translateY(7.9px) rotate(47deg);
            border-radius: 3px;
        }

        #hamburger-1.is-active .line:nth-child(3) {
            -webkit-transform: translateY(-8.4px) rotate(-47deg);
            -ms-transform: translateY(-8.4px) rotate(-47deg);
            -o-transform: translateY(-8.4px) rotate(-47deg);
            transform: translateY(-8.4px) rotate(-47deg);
            border-radius: 3px;
        }

    }

    .user-icon {
        width: 2rem;
        position: absolute;
        display: none;
        right: 4rem;
        top: 2.1rem;
        z-index: 10;

        img {
            width: 100%;
        }
    }



    @media screen and (max-width: 850px) {
        .hamburger-icon {
            display: block;
        }

        .user-icon {
            display: block;
        }

    }
}
</style>