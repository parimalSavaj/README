yt-dlp -f "bestvideo+bestaudio" -o "~/Videos/yt-dl/%(playlist_index)s-%(title)s.%(ext)s" "https://youtube.com/playlist?list=PLAX41TUzaphC09B9HFfEqOkwBqCk1yE9v&si=O2xHNnbdyiXzvpwb"

yt-dlp -f "bv*[height<=720]+ba" -o "~/Videos/yt-dl/%(playlist_index)s-%(title)s.%(ext)s" "https://youtube.com/playlist?list=PLAX41TUzaphC09B9HFfEqOkwBqCk1yE9v&si=O2xHNnbdyiXzvpwb"

yt-dlp -f "best" "https://url.com"

