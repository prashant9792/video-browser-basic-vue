<template>
    <ul class="list-group">
        <VideoListItem 
            v-for="video in videos" 
            :key="video.tag"
            :video="video"
            @selectVideo="onSelectVideo"
        >
        </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'videoList',
    components: {
        VideoListItem
    },
    props: ['videos'],
    methods: {
        onSelectVideo(video) {
            this.$emit('selectVideo', video);
        }
    }
}
</script>

<style>
.list-group {
    display: flex;
    flex-direction: column;
    padding-left: 0;
    margin-bottom: 0;
    max-width: 600px;
}
</style>