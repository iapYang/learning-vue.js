<template lang="html">
    <div class='globalControl'>
        <div class='content-wrapper'>
            <div
                class='choose choose-person'
                :class="{active: ifPersonActive}"
                @click="personClickHandler"
                >
                <span class='text'>person</span>
                <span class='symbol show-desktop'>y</span>
            </div>
            <div
                class='choose choose-trait'
                :class="{active: ifTraitActive}"
                @click="traitClickHandler"
                >
                <span class='text'>
                    {{ trait_text }}
                </span>
                <span class='symbol show-desktop'>y</span>
            </div>
            <div class='divide-line'></div>
        </div>
    </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
    computed: {
        ...mapGetters({
            ifProductsLoaded: 'getifProductsLoaded',
        }),
        ifPersonActive() {
            return this.$route.name === 'Who';
        },
        ifTraitActive() {
            return this.$route.name === 'Trait'
        },
        trait_text() {
            return this.$route.name === 'Showcase' ? 'traits' : 'personalities';
        }
    },
    methods: {
        personClickHandler() {
            this.ifPersonActive = !this.ifPersonActive;

            if (this.$route.name === 'Who') {
                this.$router.push({
                    name: 'Showcase',
                    query: this.$route.query,
                });
            } else {
                this.$router.push({
                    name: 'Who',
                    query: this.$route.query,
                });
            }
        },
        traitClickHandler() {
            this.ifTraitActive = !this.ifTraitActive;

            if (this.$route.name === 'Trait') {
                this.$router.push({
                    name: 'Showcase',
                    query: this.$route.query,
                });
            } else {
                this.$router.push({
                    name: 'Trait',
                    query: this.$route.query,
                });
            }
        }
    }
}
</script>

<style lang="scss">
#refinery .globalControl {
    position: absolute;
    z-index: 2;
    bottom: 0;
    left: 0;
    width: 100%;
    min-width: 768px;

    .content-wrapper {
        position: relative;
        max-width: 1520px;
        margin: 0 auto;

        .choose {
            position: relative;
            display: inline-block;
            width: 50%;
            padding: 20px 0;
            cursor: pointer;
            transition: background-color 0.3s ease;
            text-align: center;
            background-color: #ce912c;

            span {
                display: inline-block;
                transition: color 0.3s ease;
                vertical-align: middle;
                color: #fff;
                font-family: BrownStd-Bold;
                font-size: 14px;
            }

            .text {
                margin-right: 30px;
                letter-spacing: 2px;
                text-transform: uppercase;
            }

            .symbol {
                font-family: refinery29;
            }

            &:hover, &.active {
                background-color: #fff;

                span {
                    color: #ce912c;
                }
            }

            &.active {
                .symbol {
                    transform: rotate(180deg);
                }
            }
        }

        .divide-line {
            position: absolute;
            top: 0;
            left: 50%;
            width: 1px;
            height: 100%;
            background-color: #fff;
        }
    }
}
</style>
