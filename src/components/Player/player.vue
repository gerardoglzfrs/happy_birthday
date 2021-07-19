<template>
    <div class="player">
        <div class="player-size">
            <video controls>
                <source type="video/mp4" src="@/assets/video.mp4"/>
            </video>
        </div>
    </div>
</template>

<script>
import "./player.scss"
export default {
    name: 'player'
}
</script>