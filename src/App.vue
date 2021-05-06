<template>
    <s-container>
        <s-row>
            <s-col center="sm xl" span="6" class="margin-top-lg">
                <SearchBar @termChange="onTermChange"/>
            </s-col>
        </s-row>
        <s-row>
            <s-col span="7">
                <VideoDetail :video="selectedVideo" />
            </s-col>
            <s-col span="5">
                <VideoList :videos="videos" @selectVideo="onVideoSelect"></VideoList>
            </s-col>
        </s-row>
    </s-container>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoDetail from './components/VideoDetail';
import VideoList from './components/VideoList';

const API_KEY = 'AIzaSyCg1uec9gJ5VmXaaFI6siUbpFJTjbuitRg';
export default {
    name: 'App',
    components: {
        SearchBar,
        VideoDetail,
        VideoList
    },
    data() {
        return { videos: [], selectedVideo: null };
    },
    methods:{
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(responce => {
                this.videos = responce.data.items;
            });
        },
        onVideoSelect(video) {
            this.selectedVideo = video;
        }
    }
};
</script>