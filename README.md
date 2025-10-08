# Sunny.github.io
My free download website 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Free Media Downloader</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 600px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }
        
        .logo {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .logo h1 {
            color: #333;
            font-size: 28px;
            margin-bottom: 10px;
        }
        
        .logo p {
            color: #666;
            font-size: 16px;
        }
        
        .input-group {
            margin-bottom: 20px;
        }
        
        input[type="url"] {
            width: 100%;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 16px;
            margin-bottom: 15px;
        }
        
        .platform-buttons {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .platform-btn {
            padding: 12px;
            border: 2px solid #667eea;
            background: white;
            color: #667eea;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .platform-btn.active {
            background: #667eea;
            color: white;
        }
        
        .download-btn {
            width: 100%;
            padding: 15px;
            background: #4CAF50;
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .download-btn:hover {
            background: #45a049;
        }
        
        .service-links {
            margin-top: 20px;
        }
        
        .service-link {
            display: block;
            padding: 12px;
            margin: 8px 0;
            background: #f8f9fa;
            border: 2px solid #dee2e6;
            border-radius: 8px;
            text-decoration: none;
            color: #333;
            text-align: center;
            font-weight: bold;
        }
        
        .instructions {
            background: #fff3cd;
            border: 1px solid #ffeaa7;
            border-radius: 10px;
            padding: 15px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="logo">
            <h1>📥 Free Media Downloader</h1>
            <p>Download videos & audio from popular platforms</p>
        </div>
        
        <div class="input-group">
            <input type="url" id="videoUrl" placeholder="Paste YouTube, Facebook, Instagram link here..." required>
        </div>
        
        <div class="platform-buttons">
            <button class="platform-btn active" data-platform="youtube">YouTube</button>
            <button class="platform-btn" data-platform="facebook">Facebook</button>
            <button class="platform-btn" data-platform="instagram">Instagram</button>
            <button class="platform-btn" data-platform="tiktok">TikTok</button>
            <button class="platform-btn" data-platform="twitter">Twitter</button>
        </div>
        
        <button class="download-btn" onclick="processDownload()">Get Download Links</button>
        
        <div class="service-links" id="serviceLinks">
            <div style="text-align: center; color: #666; margin: 20px 0;">
                Paste link above and click the button
            </div>
        </div>
        
        <div class="instructions">
            <h3>How to Use:</h3>
            <ol style="margin-left: 20px; margin-top: 10px;">
                <li>Copy video URL from any app</li>
                <li>Paste in the box above</li>
                <li>Click "Get Download Links"</li>
                <li>Choose your preferred download service</li>
            </ol>
        </div>
    </div>

    <script>
        let currentPlatform = 'youtube';
        
        // Platform buttons functionality
        document.querySelectorAll('.platform-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                document.querySelectorAll('.platform-btn').forEach(b => b.classList.remove('active'));
                this.classList.add('active');
                currentPlatform = this.getAttribute('data-platform');
            });
        });
        
        function processDownload() {
            const url = document.getElementById('videoUrl').value.trim();
            const serviceLinks = document.getElementById('serviceLinks');
            
            if (!url) {
                alert('Please enter a video URL');
                return;
            }
            
            // Get download services based on platform
            const services = getDownloadServices(currentPlatform, url);
            
            // Display service links
            displayServiceLinks(services);
        }
        
        function getDownloadServices(platform, url) {
            const services = {
                youtube: [
                    { name: 'Y2Mate - Fast Download', url: `https://www.y2mate.com/mates/analyzeV2?url=${encodeURIComponent(url)}` },
                    { name: 'SSYouTube - HD Quality', url: `https://ssyoutube.com/en?url=${encodeURIComponent(url)}` },
                    { name: 'VideoDownloader - Easy', url: `https://videodownloader.com/?url=${encodeURIComponent(url)}` }
                ],
                facebook: [
                    { name: 'GetFBVideo - Fast', url: `https://getfbstuff.com/fb-video-downloader?url=${encodeURIComponent(url)}` },
                    { name: 'FBDown - Reliable', url: `https://fbdown.net/download.php?url=${encodeURIComponent(url)}` }
                ],
                instagram: [
                    { name: 'DownloadGram - Easy', url: `https://downloadgram.com/?url=${encodeURIComponent(url)}` },
                    { name: 'InstaDownload - Fast', url: `https://instadownload.co/en?url=${encodeURIComponent(url)}` }
                ],
                tiktok: [
                    { name: 'SnapTik - No Watermark', url: `https://snaptik.app/?url=${encodeURIComponent(url)}` },
                    { name: 'TikTokDownload - HD', url: `https://tiktokdownload.com/?url=${encodeURIComponent(url)}` }
                ],
                twitter: [
                    { name: 'TwitterVideoDownload', url: `https://twittervideodownloader.com/?url=${encodeURIComponent(url)}` },
                    { name: 'SaveTweetVid - Fast', url: `https://savetweetvid.com/?url=${encodeURIComponent(url)}` }
                ]
            };
            
            return services[platform] || services.youtube;
        }
        
        function displayServiceLinks(services) {
            const container = document.getElementById('serviceLinks');
            container.innerHTML = '<h3>Choose Download Service:</h3>';
            
            services.forEach(service => {
                const link = document.createElement('a');
                link.href = service.url;
                link.className = 'service-link';
                link.target = '_blank';
                link.textContent = service.name;
                container.appendChild(link);
            });
        }
        
        // Auto-detect platform from URL
        document.getElementById('videoUrl').addEventListener('input', function() {
            const url = this.value.toLowerCase();
            let detectedPlatform = 'youtube';
            
            if (url.includes('youtube.com') || url.includes('youtu.be')) {
                detectedPlatform = 'youtube';
            } else if (url.includes('facebook.com')) {
                detectedPlatform = 'facebook';
            } else if (url.includes('instagram.com')) {
                detectedPlatform = 'instagram';
            } else if (url.includes('tiktok.com')) {
                detectedPlatform = 'tiktok';
            } else if (url.includes('twitter.com') || url.includes('x.com')) {
                detectedPlatform = 'twitter';
            }
            
            if (detectedPlatform !== currentPlatform) {
                currentPlatform = detectedPlatform;
                document.querySelectorAll('.platform-btn').forEach(btn => {
                    btn.classList.remove('active');
                    if (btn.getAttribute('data-platform') === detectedPlatform) {
                        btn.classList.add('active');
                    }
                });
            }
        });
    </script>
</body>
</html>