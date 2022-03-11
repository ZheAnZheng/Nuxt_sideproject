<template>
    <button class="primary-btn">
        <slot></slot>
    </button>   
</template>


<style lang="scss" scoped>

.primary-btn{
    height:100%;
    width:100%;
    background-color:var(--btn-bg-color);
    border-radius:10px;
    transition:all .2s ease-in;
    color:var(--btn-text-color);
    &:hover{
        background-color:var(--btn-hover-bg-color);
        
    }
}

</style>