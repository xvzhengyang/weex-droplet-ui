<template>
    <text class="icon-font" :style="iconStyle">{{Icon[name]}}</text>
</template>
<style scoped>
    .icon-font {
        font-family: dropletUiIconfont;
        color: #4d4d4d;
        font-size: 32px;
    }
</style>
<script>
    import Icon from './alias';
    const dom = weex.requireModule('dom');

    export default {
        props: {
            name: {
                type: String,
                default: 'success'
            },
            styles: {
                type: Object,
                default: {}
            }
        },

        data () {
            return {
                iconStyle: {},
                Icon: Icon
            }
        },

        beforeCreate () {
            dom.addRule('fontFace', {
                'fontFamily': "dropletUiIconfont",
                'src': "url('http://at.alicdn.com/t/font_534309_4czzlr17zdw2vs4i.ttf')"
            })
        },

        created () {
            this.setStyle();
        },

        methods: {
            setStyle () {
                this.iconStyle = Object.assign({}, this.styles);
            }
        }
    }
</script>