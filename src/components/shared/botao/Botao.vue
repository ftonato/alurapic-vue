<template>
    <button :class="buttonStyle" :type="tipo" estilo="danger" @click="callAction()">{{rotulo}}</button>
</template>
<script>
    export default {

        props: {
            tipo: {
                required: true,
                type: String
            },

            rotulo: {
                required: true,
                type: String
            },

            confirmacao: {
                required: false,
                default: false,
                type: Boolean
            },

            estilo: {
                required: false,
                default: 'default',
                type: String
            }
        },
        methods: {

            callAction() {
                if(this.confirmacao) {
                    if(confirm('Confirma operacao?')) {
                        this.$emit('botaoAtivado');
                    }
                    return;
                }
                this.$emit('botaoAtivado');
            }
        },

        computed: {

            buttonStyle() {

                if(this.estilo == 'default') return 'button button-default';

                if(this.estilo == 'danger') return 'button button-danger';
            }
        }
    }
</script>    

<style scoped>
    .button {
        display: inline-block;
        padding: 10px;
        border-radius: 3px;
        margin: 10px;
        font-size: 1.2em;
    }

    .button-danger {
        background: firebrick;
        color: white;
    }

    .button-default {
        background: darkcyan;
        color: white;
    }
</style>