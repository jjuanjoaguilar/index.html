<const fetch = require('node-fetch');

exports.handler = async (event, context) => {
  // URL del stream HLS (900 kbps)
  const target = 'https://liveingesta318.cdnmedia.tv/trivisionlive/rtmp01-900/chunklist.m3u8?DVR';

  try {
    const response = await fetch(target, {
      headers: {
        'Referer': 'https://trivisioncr.com/tv-en-vivo/', // simula que viene del sitio oficial
        'Origin': 'https://trivisioncr.com',
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64)',
      }
    });
    const body = await response.text();

    return {
      statusCode: 200,
      headers: {
        'Content-Type': 'application/vnd.apple.mpegurl',
        'Access-Control-Allow-Origin': '*', // para que WebView / HLS.js funcione
      },
      body,
    };
  } catch (error) {
    return {
      statusCode: 500,
      body: 'Error fetching stream: ' + error.message,
    };
  }
};

