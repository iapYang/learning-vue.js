<template lang="html">
    <div class='refinery-header'>
        <div class='refinery-header-wrapper'>
            <a
                @click='clickHandler'
                >
                <div class='logo'>
                    <img src='images/logo.svg' />
                </div>
            </a>

            <div class='social-wrapper'>
                <div class='facebook share'>f</div>
                <div class='twitter share'>t</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        clickHandler: function() {
            this.$router.push({
                name: 'tutorial',
            });
        },
    },
}
</script>

<style lang="scss">
#refinery .refinery-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 50px;
    background-color: #fff;
    z-index: 999999;

    &:before {
        display: inline-block;
        width: 0;
        height: 100%;
        content: "";
        vertical-align: middle;
    }

    .refinery-header-wrapper {
        position: relative;
        display: inline-block;
        width: 100%;
        vertical-align: middle;

        a {
            position: relative;
            display: inline-block;
            margin-left: 30px;
            cursor: pointer;

            .logo {
                position: relative;
                display: inline-block;
                width: 150px;
            }
        }

        .social-wrapper {
            position: absolute;
            top: 50%;
            right: 30px;
            transform: translateY(-50%);
            $color1: #b1b1b2;
            $color2: white;

            .share {
                display: inline-block;
                width: 29px;
                height: 29px;
                margin: 0 5px;
                cursor: pointer;
                transition: background-color 0.3s ease, color 0.3s ease;
                text-align: center;
                color: $color1;
                border: 2px solid $color1;
                border-radius: 100%;
                background-color: $color2;
                font-family: "refinery29";
                font-size: 14px;
                line-height: 25px;

                .no-touch &:hover {
                    color: $color2;
                    background-color: $color1;
                }
            }
        }
    }
}
</style>
