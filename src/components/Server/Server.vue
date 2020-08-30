<template>
    <li class="list-group-item" :class="{active: isActive}" @click="onSetServer(serverIndex)">
        Server #{{ serverIndex }}
    </li>
</template>

<script>
    export default {
        props: {
            serverIndex: Number,
            onSetServer: Function,
            isActive: Boolean,
        },
    }
</script>

<style scoped>
    li {
        transition: 0.3s;
    }

    li:hover,
    li:active {
        cursor: pointer;
        background: rgba(79, 133, 198, 0.75);
    }

    .active {
        background: rgba(33, 82, 125, 0.75);
    }
</style>