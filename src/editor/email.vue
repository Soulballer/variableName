<template>
    <div class="email-wrapper">
        <div class="email-input-section">
            <or-textbox v-model="displayValue" class="email-input"
                        :label="label"
                        :placeholder="placeholder"
                        :disabled="readonly"
                        @input="$v.schema.email.$touch()"
                        :invalid="$v.schema.email.$error"
                        error="Email is required">
            </or-textbox>
        </div>
    </div>
</template>
<script>
    import * as _ from 'lodash'

    export default {
        props    : ['schema', 'label', 'placeholder', 'readonly', '$v', 'variableName'],
        computed : {
            displayValue : {
                get () {
                    return _.get(this.schema, this.variableName, '');
                },
                set (newValue) {
                    this.schema[this.variableName] = newValue;
                }
            }
        }
    }
</script>


<style scoped lang="scss" rel="stylesheet/scss">
    @import '../scss/colors.scss';
    @import '../scss/fonts.scss';

    .email-wrapper {
        .email-input-section {
            .email-input {

            }
        }
    }

</style>

<style lang="scss" rel="stylesheet/scss">
    @import '../scss/colors.scss';

</style>
