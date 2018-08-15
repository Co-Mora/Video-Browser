
<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"/>
        <VideoDetail :video="selectVideo" />
        <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
    </div>
</template>

<script>
    import SearchBar from './components/SearchBar';
    import VideoList from './components/VideoList';
    import VideoDetail from './components/VideoDetail';
    import axios from 'axios';

    const API_KEY = 'AIzaSyCzXmxLlafobuHUo01Jr9XdlX4VnB2qVtE'; 

    export default {
        name: 'App',
        components: {
            SearchBar,
            VideoList,
            VideoDetail
        },
        data() {
            return {
                videos: [],
                selectVideo: null
            }
        },
        methods: {
            onTermChange(searchItem) {
               axios.get('https://www.googleapis.com/youtube/v3/search', {
                   params: {
                       key: API_KEY,
                       type: 'video',
                       part: 'snippet',
                       q: searchItem

                   }
               }).then(response => {
                   this.videos = response.data.items
               })
            },
            onVideoSelect(video) {
               this.selectVideo = video;
            }
        }
    }
</script>

