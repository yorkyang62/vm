<template>
    <vm-mask v-if="mask" :visible="visibility">
        <overlay :class="'vm-toast ' + className" position="center" :visible="true">
            <i :class="'vm-toast-icon ' + iconClass" v-if="iconClass"></i>
            <slot>{{content}}</slot>
        </overlay>
    </vm-mask>
    <overlay v-else :visible="visibility" :class="'vm-toast ' + className" position="center">
        <i :class="'vm-toast-icon ' + iconClass" v-if="iconClass"></i>
        <slot>{{content}}</slot>
    </overlay>
</template>

<style>
    .vm-toast.vm-overlay{
        font-size: 0.16rem;
        color: #FFFFFF;
        line-height: 0.28rem;
        padding: 0.08rem 0.2rem;
        max-width: 90%;
        background: rgba(0, 0, 0, 0.7);
        border-radius: 4px;
        text-align: center;
    }

    .vm-toast-icon{
        width: .36rem;
        height: .36rem;
        display: block;
        margin: .05rem auto 0.07rem auto;
        background-size: 100% 100%;
        background-repeat: no-repeat;
        background-position: center center;
    }

    .vm-toast-success{
        background-image: url(./success@3x.png?__inline);
    }

    .vm-toast-loading{
        background-image: url(./loading.gif?__inline);
    }
</style>

<script>
    import vmMask from '../mask';
    import Overlay from '../overlay';

    export default{
        name: 'toast',

        mixins: [Overlay],

        props: {
            iconClass: {
                type: String,
                default: null
            },

            content: {
                type: String,
                default: null
            },

            mask: {
                type: Boolean,
                default: false
            }
        },

        data(){
            return {
                visibility: true
            }
        },

        components: {
            Overlay,
            vmMask
        }
    };
</script>