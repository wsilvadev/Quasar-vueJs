<template>
    <div class="row">
        <q-input
            filled
            class="col-md-12 col-sm-12 col-xs-12 "
            outlined
            :value="value"
            @input="$emit('input', $event)"
            :label="label"
            color="deep-purple"
            :type="type"
            :mask="maskText"
            unmasked-value
            :rules="rules"
        >
            <template v-slot:prepend>
                <q-icon :name="iconName" />
            </template>
            <template v-if="value" v-slot:append>
                <q-icon
                    name="cancel"
                    @click.stop="value = ''"
                    class="cursor-pointer"
                />
            </template>
        </q-input>
    </div>
</template>
<script>
export default {
    props: {
        label: String,
        iconName: String,
        suffix: String,
        type: String,
        maskText: String,
        rules: Array,
        value: String
    }
};
</script>
