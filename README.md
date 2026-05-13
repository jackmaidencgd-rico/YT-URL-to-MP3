# 🎵 YouTube to MP3 Converter

A web application that allows users to convert YouTube videos to MP3 format with metadata extraction (title, artist, album, filename, duration).

## ⚠️ Legal Disclaimer

**IMPORTANT:** This tool should **ONLY** be used for:
- Music that is royalty-free or Creative Commons licensed
- Music you own or have explicit permission to download
- Music where the copyright holder has granted permission
- Content in the public domain

**Downloading copyrighted music without permission is illegal in many countries.** Users are solely responsible for ensuring their use complies with applicable laws in their jurisdiction.

---

## Features

✨ **Core Features:**
- 🔗 Paste YouTube URL into text box
- 📊 Extract video metadata (title, artist, album, duration)
- 🎼 Generate proper filename
- ⬇️ Download as MP3 file
- ⚠️ Legal disclaimer on first use
- 📱 Responsive design (mobile & desktop)
- 🎨 Modern UI with gradient design

---

## Installation & Setup

### Frontend Only (Static HTML/CSS/JS)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/jackmaidencgd-rico/YT-URL-to-MP3.git
   cd YT-URL-to-MP3
   ```

2. **Open in browser:**
   - Simply open `index.html` in your web browser
   - Or serve via a local web server:
     ```bash
     python -m http.server 8000
     # Then visit http://localhost:8000
     ```

### With Backend (Production Setup)

For a fully functional application, you'll need a backend API. Here's what's required:

#### Option 1: Python Backend with Flask

**Requirements:**
```bash
pip install flask yt-dlp pydub python-dotenv
```

**Backend Structure:**
```python
from flask import Flask, request, jsonify
import yt_dlp
import os

app = Flask(__name__)

@app.route('/api/video-metadata', methods=['POST'])
def get_metadata(video_id):
    # Extract metadata using yt-dlp
    # Return JSON with title, artist, album, duration
    pass

@app.route('/api/convert', methods=['POST'])
def convert_to_mp3(video_id, url):
    # Download audio from YouTube
    # Convert to MP3
    # Extract and embed metadata
    # Return file info
    pass

@app.route('/api/download', methods=['POST'])
def download_mp3(video_id):
    # Return MP3 file for download
    pass
```

#### Option 2: Node.js Backend with Express

**Requirements:**
```bash
npm install express youtube-dl-exec fluent-ffmpeg dotenv
```

---

## Project Structure

```
YT-URL-to-MP3/
├── index.html          # Main HTML file
├── styles.css          # Styling
├── script.js           # Frontend logic
├── README.md           # This file
├── backend/            # (Optional)
│   ├── app.py         # Flask backend
│   └── requirements.txt
└── .gitignore
```

---

## How to Use

1. **Open the website** in your browser
2. **Read and accept** the legal disclaimer on first visit
3. **Paste a YouTube URL** into the text box
4. **Click "Convert to MP3"**
5. **View extracted metadata:**
   - Video title
   - Artist name
   - Album name
   - Song duration
   - Generated filename
6. **Click "Download MP3"** to save the file

---

## Supported URL Formats

The converter supports multiple YouTube URL formats:
- `https://www.youtube.com/watch?v=VIDEO_ID`
- `https://youtu.be/VIDEO_ID`
- `https://www.youtube.com/embed/VIDEO_ID`
- `https://www.youtube.com/v/VIDEO_ID`

---

## Technical Details

### Frontend Technologies
- **HTML5** - Structure
- **CSS3** - Styling with gradients and animations
- **Vanilla JavaScript** - No dependencies

### Frontend Features
- URL validation using regex
- Video ID extraction from multiple URL formats
- Persistent disclaimer acceptance (localStorage)
- Responsive design (mobile-first)
- Loading states and error handling
- Metadata display with formatted duration
- Accessible modal dialogs

### Backend Requirements (for production)
- **yt-dlp** - Download video information from YouTube
- **FFmpeg** - Audio conversion and encoding
- **Python/Node.js** - Server runtime
- **ID3 tagging** - Metadata embedding in MP3

---

## API Endpoints (Backend Implementation)

### POST `/api/video-metadata`
**Request:**
```json
{
    "videoId": "dQw4w9WgXcQ"
}
```

**Response:**
```json
{
    "title": "Video Title",
    "artist": "Artist Name",
    "album": "Album Name",
    "duration": 212,
    "fileName": "video-title.mp3",
    "videoId": "dQw4w9WgXcQ"
}
```

### POST `/api/convert`
**Request:**
```json
{
    "videoId": "dQw4w9WgXcQ",
    "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
}
```

**Response:**
```json
{
    "success": true,
    "message": "Conversion successful",
    "fileId": "file-123-abc",
    "fileName": "video-title.mp3"
}
```

### POST `/api/download`
**Request:**
```json
{
    "videoId": "dQw4w9WgXcQ"
}
```

**Response:** Binary MP3 file with proper headers

---

## Disclaimer & Legal Notice

⚠️ **This tool is provided as-is.** Users must:
1. Only use for legally authorized content
2. Respect copyright and intellectual property laws
3. Comply with YouTube's Terms of Service
4. Take responsibility for their own usage
5. Not use to download copyrighted material without permission

**The creator assumes NO liability** for misuse, legal consequences, or damages resulting from the use of this tool.

---

## Troubleshooting

### "Invalid YouTube URL"
- Ensure the URL is from youtube.com or youtu.be
- Try copying the full URL from the address bar

### "Failed to fetch metadata"
- Check your internet connection
- Verify the video is publicly available
- Some videos may have restrictions preventing download

### Download not working
- Ensure backend API is running (if using production setup)
- Check browser console for errors
- Try a different video

---

## Performance Considerations

- ⏱️ Conversion time: 30-120 seconds depending on video length
- 💾 Typical MP3 file size: 1-10MB per minute of audio
- 🔄 Rate limiting: Implement to avoid YouTube blocking
- 🔐 API keys: Keep sensitive credentials in environment variables

---

## Security Recommendations

1. **Rate Limiting** - Limit requests per IP/user
2. **Input Validation** - Validate all YouTube URLs server-side
3. **HTTPS Only** - Use SSL/TLS in production
4. **Environment Variables** - Store API keys securely
5. **CORS Policy** - Restrict to your domain
6. **File Size Limits** - Limit maximum video duration

---

## Contributing

Contributions are welcome! Please ensure:
- Code follows project style
- Features include proper error handling
- Legal disclaimers are prominent
- Mobile responsiveness is maintained

---

## Future Enhancements

- [ ] Batch conversion support
- [ ] Playlist support
- [ ] Custom metadata editing
- [ ] Audio quality selection
- [ ] Cloud storage integration
- [ ] Conversion history
- [ ] Advanced ID3 tag editing
- [ ] Multiple format support (WAV, FLAC, AAC)

---

## License

This project is provided as-is for educational purposes. Users are responsible for complying with all applicable laws.

---

## Support

For issues or questions:
1. Check the Troubleshooting section
2. Review the code comments
3. Check browser console for errors
4. Verify YouTube URLs are correct

---

## Version History

**v1.0.0** - Initial release
- Frontend UI complete
- Metadata extraction ready
- Download functionality structure
- Legal disclaimer modal
- Responsive design

---

**Made with ❤️ | Use responsibly and legally**
