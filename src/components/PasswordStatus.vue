<template>

    <div class="status">
        <p v-if="zxcvbn(passwordProp).score === 0" class="status__name">Weak 
            <span class="status__color status__color--weak"></span>
            <span class="status__color status__color__circle status__color__circle--weak-light"></span>
            <span class="status__color status__color__circle status__color__circle--weak-light"></span>
            <span class="status__color status__color__circle status__color__circle--weak-light"></span>
        </p>
        <p v-else-if="zxcvbn(passwordProp).score === 1" class="status__name">Meduim 
            <span class="status__color status__color--meduim"></span>
            <span class="status__color status__color--meduim"></span>
            <span class="status__color status__color__circle status__color__circle--meduim-light"></span>
            <span class="status__color status__color__circle status__color__circle--meduim-light"></span>
        </p>
        <p v-else-if="zxcvbn(passwordProp).score === 2" class="status__name">Strong 
            <span class="status__color status__color--strong"></span>
            <span class="status__color status__color--strong"></span>
            <span class="status__color status__color--strong"></span>
            <span class="status__color status__color__circle status__color__circle--strong-light"></span>
        </p>
        <p v-else-if="zxcvbn(passwordProp).score >= 3" class="status__name">Strongest 
            <span class="status__color status__color--strong"></span>
            <span class="status__color status__color--strong"></span>
            <span class="status__color status__color--strong"></span>
            <span class="status__color status__color--strong"></span>
        </p>
    </div>
 
</template>

<script setup>
import zxcvbn from 'zxcvbn';

const propValue = defineProps(['passwordProp'])
//delete test functions when you are done testing
const stuusd = () =>{
    console.log(propValue.passwordProp);
}

</script>

<style lang="scss" scoped>
$weak-passowrd-color: #ff5f55;
$weak-passowrd-color-light: #FFBEBA;

$medium-password-color: #EDB458;
$medium-password-color-light: #F7DDB4;

$strong-password-color-light: #95D6A3;
$strong-password-color: #4CB963;

.status{
    display: flex;
    align-items: center;
    font-style: italic;
    margin: 1.5rem 0;

    &__name{
        display: flex;
        animation: horizontal-shaking .5s ease-in-out;
    }

    &__color{
        height: 28px;
        width: 44px;
        border-radius: 32px;
        margin-left: 1rem;
        // never create an element of an element (only blocks can have elements)
        &__circle{
            width: 28px;
            height: 28px;
            border-radius: 50%;
            margin-left: 0.6rem;

            &--weak-light{
                background-color: $weak-passowrd-color-light;
            }

            &--meduim-light{
                background-color: $medium-password-color-light;
            }

            &--strong-light{
                background-color: $strong-password-color-light;
            }
        }

        &--weak{
            background-color: $weak-passowrd-color;
        }

        &--meduim{
            background-color: $medium-password-color;
        }

        &--strong{
            background-color: $strong-password-color;
        }
    }
}


</style>
