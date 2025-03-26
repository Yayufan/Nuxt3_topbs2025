<template>
    <footer class="footer-section">
        <div class="footer-box">
            <div class="logo-box">
                <img src="/img/logo.png" alt="">
            </div>
            <div class="info-box">
                <p>
                    <span>Address：33305桃園市龜山區復興街5號
                    </span>
                    <span>Phone：(03)3281200 ext.3605
                    </span>
                    <span>
                        E-Mail：topbs106@gmail.com</span>
                </p>
                <p>Copyright Reserved By 2024</p>
            </div>
        </div>
    </footer>
</template>
<style lang="scss" scoped>
.footer-section {
    background-color: #F0F0F0;
    padding:25px 15px;
    .footer-box {
        max-width: 1200px;
        margin: 0 auto;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        .logo-box {
            border-right: 1px solid white;
            img{
                width: 50%;
            }
        }
        .info-box {
            font-size: 0.8rem;
            color: $main-content-color;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            span {
                margin-right: 2vw;
            }
        }
    }

    @media screen and (max-width: 480px) {
        .footer-box {
            .logo-box {
                border-right: none;
                border-bottom: 1px solid white;
                img{
                    width: 50%;
                }
            }
            .info-box {
                margin-top: 0;
                width: 80%;
                text-align: center;
                span {
                    display: block;
                    margin-right: 0;
                }
            }
        }
        
    }
}
</style>