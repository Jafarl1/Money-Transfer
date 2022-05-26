<template>
    <ul>
        <li>
            <span v-if="date">
               {{ date }}
            </span>
            <div>
                <span v-if="sent">
                    {{ sent }} AZN sent to
                </span>
                <span>
                    {{ name }}
                </span>
            </div>
        </li>
    </ul>
</template>

<script>
    export default {
        allHistory: [{}],
        props: ["id", "name", "sent", "date"]
    }

</script>

<style scoped>
    li {
        width: 100%;
        height: 40px;
        border-bottom: 1px solid rgba(222, 222, 222, 0.5);
        padding: 5px 10px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>