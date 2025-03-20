<template>
    <section class="menu-section">
        <el-menu class="menu" mode="horizontal" :ellipsis="false" :popper-offset="0" popper-class="popper" :popper-append-to-body="false">
            <el-sub-menu index="1" popper-class="noSub popper">
                <template #title>
                    <nuxt-link to="/"><img class="home-logo" src="/img/logo.png" alt=""></nuxt-link>
                </template>
            </el-sub-menu>
            <el-sub-menu index="2" >
                <template #title>TOPBS & IOPBS</template>
                <nuxt-link to="/message-from-president"> <el-menu-item index="2-1">Message from President</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/conference-information"> <el-menu-item index="2-2">Conference Information</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/organizing-committee"> <el-menu-item index="2-3">Organizing Committee</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/board-member"> <el-menu-item index="2-4">Board Member</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/download-center"> <el-menu-item index="2-5">Download Center</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/activity-photos"> <el-menu-item index="2-6">Activity Photos</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/venue"> <el-menu-item index="7-3">Venue</el-menu-item>
                </nuxt-link>
            </el-sub-menu>
            <el-sub-menu index="3" popper-class="noSub popper">
                <template #title>News</template>
            </el-sub-menu>
            <el-sub-menu index="4">
                <template #title>Program</template>
                <nuxt-link to="/program-at-a-glance"> <el-menu-item index="3-1">Program at a Glance</el-menu-item>
                </nuxt-link>
                <!-- <nuxt-link to="/scientific-program"> <el-menu-item index="3-2">Scientific Progrem</el-menu-item>
                </nuxt-link> -->
                <nuxt-link to="/invited-speakers"> <el-menu-item index="3-3">Invited Speakers</el-menu-item>
                </nuxt-link>
                <!-- <nuxt-link to="/social-program"> <el-menu-item index="3-4">Social Program</el-menu-item>
                </nuxt-link> -->
                <nuxt-link to="/program-book-download"> <el-menu-item index="3-5">Program Book Download</el-menu-item>
                </nuxt-link>
            </el-sub-menu>
            <el-sub-menu index="5">
                <template #title>Registration</template>
                <nuxt-link to="/registration-guidelines"> <el-menu-item index="4-1">Registration
                        Guidelines</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/demo-register"> <el-menu-item index="4-2">Register Now</el-menu-item>
                </nuxt-link>
            </el-sub-menu>
            <el-sub-menu index="6">
                <template #title>Abstracts</template>
                <nuxt-link to="/submission-guidelines"> <el-menu-item index="5-1">Submission Guidelines</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/abstract-submission"> <el-menu-item index="5-2">Abstract Submission</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/award"> <el-menu-item index="5-3">Award</el-menu-item>
                </nuxt-link>
            </el-sub-menu>
            <el-sub-menu index="7">
                <template #title>Sponsorship & Exhibition</template>
                <nuxt-link to="/list-of-sponsors"> <el-menu-item index="6-1">List of Sponsors</el-menu-item>
                </nuxt-link>
            </el-sub-menu>
            <el-sub-menu index="8">
                <template #title>General Infomation</template>
                <nuxt-link to="/accommodation"> <el-menu-item index="7-1">Accommodation</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/video"> <el-menu-item index="7-2">Video</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/transportation"> <el-menu-item index="7-4">Transportation</el-menu-item>
                </nuxt-link>
                <nuxt-link to="https://www.travel.taipei/en" target="_blank"> <el-menu-item index="7-5">Travel</el-menu-item>
                </nuxt-link>
                <nuxt-link to="/contact-us"> <el-menu-item index="7-6">Contact Us</el-menu-item>
                </nuxt-link>
            </el-sub-menu>
            <el-sub-menu index="9" popper-class="noSub popper">
                <template #title>Login</template>
            </el-sub-menu>
        </el-menu>
    </section>
</template>
<style lang="scss" scoped>
.menu-section {
    display: flex;
    justify-content: center;
    margin-top: 2vw;

    @media screen and (max-width: 850px) {
        display: none;
    }

    .menu {
        width: 100%;
        max-width: 100%;
        background-color: hsla(0, 100%, 100%, 0);
        border: none;
        display: flex;
        // justify-content: space-around;
        font-weight: bold;
        font-size: 1rem;
        text-wrap: wrap;
        text-align: center;
        color: black;
        box-sizing: border-box;

        .el-sub-menu {
            height: 100%;
            width: calc(100% / 9);;
            box-sizing: border-box;

            .home-logo {
                width: 7vw;
            }


            a {
                color: black;
            }


            :deep(.el-sub-menu__title) {
                width: 100%;
                // padding: 0 1%;
                padding: 0;
                display: flex;
                justify-content: center;
                align-items: center;
                white-space: pre-wrap;
                border-bottom: none;

                line-height: normal;
                color: black;
                height: 100%;

                i {
                    display: none;
                }


                &.is-active {
                    border-bottom: none;
                    background-color: $main-color;
                    color: white;
                }

            }

        }

        .el-sub-menu:not(:first-of-type) {
            // :deep(.el-sub-menu__title) {
                &:hover {
                    background-color: $main-color;
                    color: white;
                    
                    a {
                        color: white;
                    }
                    :deep(.el-sub-menu__title) {
                        background-color: $main-color;
                        color: white;

                        a {
                            color: white;
                        }
                    }
                }
            // }
        }

        .el-sub-menu:not(:first-of-type):not(:last-of-type) {
            border-right: 1px solid gainsboro;

        }

        :deep(.el-menu-item) {
            height: 100%;
            width: 100%;
            line-height: normal;
            // padding: 0 0.5rem;
            margin: 0 0.5rem;
            

            // &:hover {
            //     background-color: $main-color;
            //     color: white;
            // }
        }
    }

}
</style>