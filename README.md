# Watermark Telegram Bot (@imjaanvi)

Koi bhi photo/video/gif bhejo, bot uspar "@imjaanvi" ka watermark laga dega
jo **left se right move** karega.

## Local setup (step-by-step)

1. **Python 3.9+** install hona chahiye.

2. Is folder me terminal khol kar dependencies install karo:
   ```bash
   pip install -r requirements.txt
   ```

3. **ImageMagick ki zaroorat NAHI hai** — watermark text PIL se transparent
   PNG bana ke overlay kiya jata hai, isliye woh Windows wali "ImageMagick
   not installed" error ab nahi aayegi.

4. **FFmpeg** chahiye hoga (video processing ke liye) - `imageio-ffmpeg`
   package usually apne aap handle kar leta hai, alag se install nahi karna
   padta. Agar error aaye to `sudo apt-get install ffmpeg` chala do.

5. Apna Telegram bot banao — Telegram me **@BotFather** ko `/newbot` bhejo,
   bot ka naam/username set karo, tumhe ek **token** milega.

6. Token ko environment variable me set karo:
   ```bash
   # Linux / Mac
   export BOT_TOKEN="123456789:AAExampleTokenHere"

   # Windows (cmd)
   set BOT_TOKEN=123456789:AAExampleTokenHere

   # Windows (PowerShell)
   $env:BOT_TOKEN="123456789:AAExampleTokenHere"
   ```

7. Bot chalao:
   ```bash
   python bot.py
   ```

8. Ab Telegram me apne bot ko photo/video/gif bhejo — kuch second me
   watermark laga hua output wapas mil jayega.

## Notes
- Photo ek static image hoti hai, isliye watermark "move" dikhane ke liye
  bot photo ko 3-second ki chhoti video me convert kar deta hai (jisme
  watermark left se right move karta hua dikhta hai).
- Video/GIF me original content same rehta hai, sirf upar moving text
  overlay ho jata hai.
- Watermark text (`@imjaanvi`), color, font size, speed sab `bot.py` ke
  `WATERMARK_TEXT` variable aur `make_moving_textclip()` function me
  change kar sakte ho.
