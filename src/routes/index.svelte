

<script>

  import AuthorCard from '$lib/AuthorCard.svelte'
  import PostsGrid from '$lib/PostsGrid.svelte'


  export let posts
  export let videos
  export let authors
  
  import Map from '$lib/Map.svelte';
  
  
</script>



<svelte:head>
  <title>2AM TV</title>
  <script src="https://unpkg.com/@mux/mux-player"></script>
  <script type="text/javascript" src="https://maps.googleapis.com/maps/api/js"></script>
  
</svelte:head>



{#each videos as video, i}
<div style="position: relative">
<h2>{video.title}</h2>
<div class="info">
<p>{video._createdAt}</p>
{#if video.location} 
<p>{video.location.lng}, {video.location.lat}</p>
{/if}
</div>
{#if video.location} 
<Map location={video.location} count={i}  />

{/if}


<mux-player
  stream-type="on-demand"
  playback-id="{video.data.playback_ids[0].id}"
  metadata-video-title="Test video title"
  metadata-viewer-user-id="user-id-007"
  controls="false"
></mux-player>




</div>
{/each}

<style>

mux-player {
width: 100%;
}

mux-player::part(button), mux-player::part(range), mux-player::part(time),  mux-player::part(poster-layer), mux-player::part(vertical-layer) {
  display: none;
}

h2 {
margin-bottom: 0
}

.info {
display: flex;
justify-content: space-between;
width: 100%;
}
</style>