#<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Trivision Proxy HLS</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body { margin: 0; overflow: hidden; background: black; }
    video { width: 100vw; height: 100vh; object-fit: cover; background: black; }
  </style>
  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
</head>
<body>

<video id="video" autoplay playsinline muted></video>

<script>
  const video = document.getElementById('video');
  const streamURL = "https://liveingesta318.cdnmedia.tv:443/trivisionlive/rtmp01-1500/chunklist.m3u8?DVR";

  function startPlayer() {
    if (Hls.isSupported()) {
      const hls = new Hls();
      hls.loadSource(streamURL);
      hls.attachMedia(video);
      hls.on(Hls.Events.ERROR, (event, data) => {
        if (data.fatal) {
          hls.destroy();
          setTimeout(startPlayer, 3000); // reconexión automática
        }
      });
    } else if (video.canPlayType('application/vnd.apple.mpegurl')) {
      video.src = streamURL;
    }
  }

  startPlayer();
</script>

</body>
</html>
 index.html
