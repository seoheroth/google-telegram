# บอทเทเลแกรม ใช้ค้นหาอันดับบน Google
เทเลแกรมบอท แสดงผลการค้นหาบน Google ทั้งข้อความและรูปภาพ

## วิธีใช้
แนะให้ใช้โฮสต์เว็บไซต์ ของเราเองเนื่องจาก Google ได้กำหนดการค้นหา ** 100 ครั้ง
ต่อวัน ** จำกัด สำหรับ API เว้นแต่เราจะเสียตังครับ 
https://t.me/tgseoteamth_bot ติดปัญหาสอบถามได้ที่เฟสบุ๊ค https://www.facebook.com/surapan2?

## Run instruction
```
git clone https://github.com/seoheroth/google-search-telegram-bot
cd google-search-telegram-bot
pip install -e .
PYTHONPATH=src python3 src/app/__init__.py

หรือรันแบบ BG
PYTHONPATH=src python3 src/app/__init__.py .&
```
เราจำเป็นต้องติดตั้งไว้ใน venv env

After setting up these you'll have to fill in your API keys in config.json

### Hosting on pythonanywhere ใช้ฟรีจำกัดการใช้งาน
เป็นอีกทางเลือกที่ง่ายต่อการโฮสต์บอทอย่างอิสระคือการใช้ PAW ในเว็บคอนโซลของคุณคุณควร
ตั้งค่าไดเรกทอรีต้นทางเป็น src และแก้ไขไฟล์กำหนดค่า WSGI ตาม
ตัวอย่างที่ระบุใน repo นี้ (misc/pythonanywhere_com_wsgi.py)

## config.json
This file holds constants like API keys that should be kept outside of the repo.
config.json should be a text file of valid serialized JSON. The following fields
must be present:
- telegram_bot_token
  - Your telegram bot token. You need to obtain it via @BotFather following the
  instructions outlined at https://core.telegram.org/bots
- google_api_key
  - Your Google API key used to authenticate the Custom Search API. You need to
  obtain it using the setup tool here:
  https://console.developers.google.com/start/api?id=customsearch&credential=client_key
- search_engine_id
  - Your Search Engine ID. Create a new engine at https://cse.google.com/cse/all.
  When creating a new engine, input a random site in "Sites to search". After
  creation, click modify, then change "Search only included sites" to "Search
  the entire web" and remove the random site you just added
- allow_only_users
  - You could limit who could use the bot hosted by you. You can either
  whitelist a user by id or username. Example: [999999,"fancy_user"] would allow
  the 2 users to use your hosted bot. An empty list would allow all
- paw_app
  - Useful only when you are hosting on PAW (See
  [Hosting on pythonanywhere](#hosting-on-pythonanywhere) for more details)
  - url
    - The URL of your web app
  - webhook_secret
    - Any string, must be valid URL character

## Dependency
- Python 3 (developed and tested on 3.5)
- Telepot (https://github.com/nickoala/telepot)
