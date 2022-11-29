<template>
    <div class="card">
        <div>
            <p class="title">
                <strong>
                    Название:
                </strong>
                {{ title }}
            </p>
            <p class="subtitle">
                <strong>
                    Описание:
                </strong>
                {{ body }}
            </p>
        </div>
        <div>
            <button @click="removePost(item.id)" class="btn">Удалить</button>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        item: {
            type: Object,
            required: true
        }
    }
}
</script>