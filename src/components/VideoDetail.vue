<template>
    <div v-if="video">
        <div>
            <iframe 
                width="100%" 
                height="450" 
                :src="videoURL" 
                title="{{videoTitle}}" 
                frameborder="1" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
            </iframe>
        </div>
        <div class="details"> 
            <h3>{{ video.snippet.title }}</h3>
            <p>{{ video.snippet.description }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
        videoURL() {
            const id = this.video.id.videoId;
            return `https://www.youtube.com/embed/${id}`;
        },
        videoTitle() {
            return this.video.snippet.title;
        }
    }
}
</script>

<style scoped>
.details {
    padding: .75rem 1.25rem;
    margin-bottom: -1px;
    background-color: #fff;
    border: 1px solid rgba(0,0,0,.125);
}
</style>