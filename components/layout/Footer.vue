<template>
    <footer class="footer-section">
        <div class="footer-box">
            <div class="logo-box">
                <img class="logo-img" src="/img/logo.png" alt="">
                <img class="tourism-logo" src="/img/department_of_information_and_tourism.png" alt="">
            </div>
            <div class="info-box">
                <p>
                    <span>Address：33305桃園市龜山區復興街5號
                    </span>

                </p>
                <p> <span>Phone：(03)3281200 ext.3605
                    </span></p>
                <p> <span>
                        E-Mail：iopbs2025@gmail.com</span></p>
                <p>Copyright Reserved By 2025</p>
            </div>
        </div>
    </footer>
</template>
<style lang="scss" scoped>
.footer-section {
    background-color: #F0F0F0;
    padding: 25px 15px;

    .footer-box {
        // max-width: 1200px;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        gap: 10rem;
        // border: 1px solid black;

        .logo-box {
            // width: 60%;
            flex: 1;
            border-right: 1px solid white;
            display: flex;
            align-items: center;
            justify-content: flex-start;
            gap: 5rem;
            padding: 0.5rem 2rem;
            // border: 1px solid black;

            .logo-img {
                width: 16%;
            }

            .tourism-logo {
                width: 40%;
            }
        }

        .info-box {
            // width: 40%;
            flex: 0.5;
            padding: 1rem;
            font-size: 1rem;
            color: $main-content-color;
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            justify-content: center;
            text-align: center;

            span {
                margin-right: 2vw;
            }
        }
    }

    @media screen and (max-width: 1024px) {
        .footer-box {
            gap: 10rem;

            .logo-box {
                border-right: none;
                border-bottom: 1px solid white;
                // width: 30%;
                gap: 2rem;

                .logo-img {
                    width: 30%;
                }

                .tourism-logo {
                    width: 70%;
                }
            }

            .info-box {
                margin-top: 0;
                // width: 70%;
                text-align: center;

                span {
                    display: block;
                    margin-right: 0;
                }
            }
        }

    }

    @media screen and (max-width: 480px) {
        .footer-box {
            gap: 6rem;

            .logo-box {
                border-right: none;
                border-bottom: 1px solid white;
                flex-direction: column;

                .logo-img {
                    width: 50%;
                }

                .tourism-logo {
                    width: 100%;
                }
            }

            .info-box {
                margin-top: 0;
                text-align: center;
                font-size: 0.8rem;
                span {
                    display: block;
                    margin-right: 0;
                }
            }
        }

    }
}
</style>