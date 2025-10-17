<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Trivision TV</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body { margin:0; overflow:hidden; background:black; font-family: Arial, sans-serif; }
    video { width:100vw; height:100vh; object-fit:cover; background:black; }
    .topbar {
      position: fixed; top:0; left:0; width:100%; height:50px;
      background: rgba(0,0,0,0.5); display:flex; align-items:center; padding:0 12px; box-sizing:border-box; z-index:10;
    }
    .logo {
      width:40px; height:40px; background:#ffcc00; border-radius:4px;
      display:flex; align-items:center; justify-content:center;
      font-weight:bold; color:black; font-size:16px; margin-right:10px;
    }
    .title { color:white; font-size:18px; font-weight:bold; }
  </style>
  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
</head>
<body>

<div class="topbar">
  <div class="logo">TV</div>
  <div class="title">Trivision</div>
</div>

<video id="video" autoplay playsinline muted></video>

<script>
const video = document.getElementById('video');
const streamURL = "https://liveingesta318.cdnmedia.tv/trivisionlive/rtmp01-900/chunklist.m3u8?DVR";

function startPlayer() {
  if(Hls.isSupported()){
    const hls = new Hls();
    hls.loadSource(streamURL);
    hls.attachMedia(video);

    hls.on(Hls.Events.MANIFEST_PARSED, () => {
      video.muted = false;
      video.play().catch(()=>{ video.muted=true; video.play(); });
    });

    hls.on(Hls.Events.ERROR, (event, data) => {
      if(data.fatal){
        hls.destroy();
        setTimeout(startPlayer,3000);
      }
    });
  } else if(video.canPlayType('application/vnd.apple.mpegurl')){
    video.src = streamURL;
  }
}

startPlayer();
</script>

</body>
</html>
