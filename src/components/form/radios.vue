<template>
    <v-box :label="label" class="vm-form-radios">
        <span 
            @click="onClick(option.value)" 
            v-for="(option, index) in options" 
            :class="{
                'vm-form-tag-selected': val == option.value,
                'vm-form-tag': true
            }"
        >
        {{option.label}}
        </span>

        <template slot="msg">
            <slot name="msg"></slot>
        </template> 
    </v-box>
</template>

<script>
    import vBox from "./box";
    import {Single} from './abstract';
    require('./common.css');

    export default{
        name: 'radios',

        mixins: [vBox, Single],

        props: {
            options: {
                type: Array,
                required: true
            }
        },

        components: {
            vBox
        },

        methods:{
            onClick(v){
                this.val = v;
            }
        }
    }
</script>
