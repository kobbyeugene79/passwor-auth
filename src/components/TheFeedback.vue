<script setup>
const props = defineProps({
    name: String,
    content: String
})


</script>

<template>
    <p v-if="(content !== '')" class="feedback">
        <span class="feedback__info">{{name}}</span> 
        {{content}}
    </p>
</template>

<style lang="scss" scoped>
$bg-color: #F5F5F5;

$text-primary-color: #C3DEEF;
$text-secondary-color: #1B4965;
.feedback{
    position: relative;
    display: flex;
    width: 100%;
    height: 42px;
    border-radius: 32px;
    margin: 1rem 0;
    align-items: center;
    background-color: $text-primary-color;
    font-style: italic;
    box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.06), 0px 1px 3px rgba(0, 0, 0, 0.1);
    animation: move-up .5s ease-in-out;

    &__info{
        background-color: $text-secondary-color;
        border-radius: 32px;
        align-items: center;
        text-align: center;
        font-size: small;
        font-style: normal;
        font-weight: 600;
        padding: 0.5rem;
        margin-left: 0.2rem;
        margin-right: 1rem;
        color: $bg-color;
    }
}
</style>