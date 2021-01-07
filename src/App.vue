<template>
    <div class="content">

        <div class="footer">
            <cube-tab-bar v-model="selectedLabelDefault" @click="changeHandler">
                <cube-tab v-for="item in tabs" :icon="item.icon" :label="item.label" :value="item.path"
                          :key="item.path">
                </cube-tab>
            </cube-tab-bar>
        </div>
        <router-view class="container"/>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                selectedLabelDefault: '/',
                tabs: [{
                    label: 'Home',
                    icon: 'cubeic-home',
                    path: "/"
                }, {
                    label: 'Like',
                    icon: 'cubeic-like',
                    path: "/like"

                }, {
                    label: 'Vip',
                    icon: 'cubeic-vip',
                    path: "/vip"
                }, {
                    label: 'Me',
                    icon: 'cubeic-person',
                    path: "/about"
                }]
            }
        },
        methods: {
            changeHandler(path) {
                if (this.selectedLabelDefault !== path) {
                    this.$router.push(path)
                }
            }
        }
    }
</script>

<style lang="scss">
    .content {
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
        display:flex;
        flex-flow:column nowrap;
        overflow:hidden;
        .container{
            flex: 1;
        }
        .footer {
            position: fixed;
            bottom: 0;
            z-index: 32;
            width: 100%;
            border-top: 1px solid rgba(0, 0, 0, 0.1)
        }
    }
</style>
