<html>
	<head>
	<style>
		body{
		background-color: #159957;
background-image: linear-gradient(120deg, #155799, #159957);
		}
		</style>
	</head>
	<div class="">
	</div>
	<h3>Music provided by NoCopyrightSounds.</h3>
	<hr>
	<h6>Watch: https://youtu.be/lG6HVrrXup8</h6>
<div id="player"></div>
<script>
var playlistId = "PLRBp0Fe2GpgmsW46rJyudVFlY6IYjFBIK";
var tag = document.createElement('script');
tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);
var player;
var hasShuffled = false;
var lastplayed = 0;
var counter = 0;

function onYouTubeIframeAPIReady() {
	player = new YT.Player('player', {
		height: '179',
		width: '300',
		playerVars: {
			autoplay: 1,
			mute: 0,
			showinfo: 1,
			modestbranding: 1
		},
		events: {
			'onReady': onPlayerReady,
			'onStateChange': onPlayerStateChange
		}
	});
}

function onPlayerReady(event) {
	player.loadPlaylist({
		'listType': 'playlist',
		'list': playlistId
	});
}

function onPlayerStateChange(event) {
	const player = event.target;
	var playlistArray = player.getPlaylist();
	var playListArrayLength = playlistArray.length;
	if (!hasShuffled) {
		player.setShuffle(true);
		player.playVideoAt(0);
		hasShuffled = true;
	}
	if (event.data == YT.PlayerState.ENDED) {
		counter++;
		if (counter == playListArrayLength - 1) {
			player.setLoop(true);
			lastplayed = player.getPlaylistIndex();
			counter = 0;
			if (lastplayed == playListArrayLength) {
				player.previousVideo();
			} else if (lastplayed == 0) {
				player.nextVideo();
			}
			hasShuffled = false;
		}
	}
}
	</script>
</html>
