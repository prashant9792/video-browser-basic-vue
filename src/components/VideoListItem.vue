<template>
    <li class="list-group-item" @click="onSelectVideo">
        <img :src="thumbnailUrl" class="margin-right-sm"/>
        <div class="item-content">
            {{ video.snippet.title }}
        </div>
    </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['video'],
    computed: {
        thumbnailUrl(){
            return this.video.snippet.thumbnails.default.url;
        }
    },
    methods: {
        onSelectVideo() {
            this.$emit('selectVideo', this.video);
        }
    }
}
</script>

<style scoped>
li {
    display: flex;
    cursor: pointer;
}
.list-group-item {
    padding: .75rem 1.25rem;
    margin-bottom: -1px;
    background-color: #fff;
    border: 1px solid rgba(0,0,0,.125);
}
li:hover {
    background: #eee;
}
</style>
