<template>
    <div>
        <q-page class="column q-pa-md" style="max-width: 50rem" padding>
            <p class="text-h4 text-weight-light text-center">Formulário</p>
            <q-form
                @submit="onSubmit"
                class="q-gutter-xs"
                @reset="onReset"
                ref="myForm"
            >
                <Input
                    label="Nome"
                    iconName="person"
                    type="text"
                    v-model="form.name"
                    :rules="[
                        val => val != '' || 'Campo precisa ser preenchido'
                    ]"
                />
                <Input
                    label="Idade"
                    v-model="form.age"
                    iconName="person"
                    type="number"
                    :rules="[
                        val => (val >= 7 && val < 101) || 'Idade inválida'
                    ]"
                />
                <Input
                    label="Email"
                    v-model="form.email"
                    iconName="email"
                    type="email"
                    :rules="[
                        val =>
                            val.includes('@gmail.com') ||
                            val.includes('@email.com') ||
                            'Email precisa estar no formato ( exemplo@gmai.com)'
                    ]"
                />
                <Input
                    label="Telefone"
                    v-model="form.phone"
                    iconName="phone"
                    maskText="(##) ####-###-##"
                    :rules="[
                        val => val.length == 11 || 'Telefone precisa ser válido'
                    ]"
                />
                <div class="row justify-end ">
                    <q-btn
                        label="Resetar"
                        type="reset"
                        color="primary"
                        outline=""
                        class="q-mr-md"
                    />
                    <q-btn color="primary" type="submit" label="Cadastrar" />
                </div>
            </q-form>
        </q-page>
    </div>
</template>

<script>
import Input from '../components/Input.vue';
export default {
    props: {},
    watch: {},
    name: 'PageIndex',
    components: {
        Input
    },
    data() {
        return {
            form: {
                name: '',
                age: '',
                email: '',
                phone: ''
            }
        };
    },

    methods: {
        onSubmit() {
            this.$q.notify({
                type: 'positive',
                message: 'Enviado com Sucesso'
            });
            this.onReset();
        },
        async onReset() {
            await this.resetForm();
            this.$refs.myForm.resetValidation();
        },
        async resetForm() {
            this.form = {
                name: '',
                age: '',
                email: '',
                phone: ''
            };
        }
    }
};
</script>
