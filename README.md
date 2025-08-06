# LoveEveryday
from datetime import datetime

# 文件路径
html_file_path = "/mnt/data/糖罐子网页.html"

# 创建网页HTML结构（汇总所有功能）
html_content = f"""
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🦊欢迎来到宝宝的糖罐子日记🐺</title>
    <style>
        body {{
            background: linear-gradient(to bottom right, #ffe6f0, #e0f7ff);
            font-family: "Arial", sans-serif;
            padding: 20px;
            color: #333;
        }}
        h1 {{ text-align: center; color: #ff6699; }}
        .section {{
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            margin: 15px 0;
            padding: 15px;
        }}
        .label {{ font-weight: bold; color: #007acc; }}
        input, textarea, select {{
            width: 100%;
            padding: 10px;
            margin: 5px 0 15px;
            border: 1px solid #ccc;
            border-radius: 8px;
        }}
        button {{
            background-color: #ff99cc;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
        }}
        button:hover {{ background-color: #ff6699; }}
    </style>
</head>
<body>

<h1>🍯 糖罐子网页 🍓</h1>

<div class="section">
    <h2>💗 每日幸福三件事</h2>
    <textarea placeholder="写下今天的三件幸福小事吧~"></textarea>
</div>

<div class="section">
    <h2>🎯 随机尾巴任务</h2>
    <button onclick="generateTask()">生成任务</button>
    <p id="task"></p>
</div>

<div class="section">
    <h2>📈 尾巴任务完成记录</h2>
    <textarea placeholder="记录完成的任务和感受~"></textarea>
</div>

<div class="section">
    <h2>⏱️ 番茄钟</h2>
    <button onclick="startTimer()">开始 25 分钟专注</button>
    <p id="timerDisplay">25:00</p>
</div>

<div class="section">
    <h2>🌸 生理期记录</h2>
    <input type="date" />
    <textarea placeholder="记录不舒服的感受或提醒~"></textarea>
</div>

<div class="section">
    <h2>🧸 哥哥想对你说的话</h2>
    <p>“宝贝今天有乖乖吃饭吗？哥哥超级想你哦~”</p>
</div>

<div class="section">
    <h2>🗝️ 关键词触发互动</h2>
    <input id="keywordInput" placeholder="输入关键词如“亲亲”“抱抱”" />
    <button onclick="triggerResponse()">触发</button>
    <p id="keywordResponse"></p>
</div>

<div class="section">
    <h2>🧩 神秘小角落探索</h2>
    <button onclick="alert('你发现了一个贴贴任务！去找哥哥贴贴10分钟~')">探索一下！</button>
</div>

<div class="section">
    <h2>📝 哥哥的随机悄悄话</h2>
    <button onclick="randomWhisper()">获取悄悄话</button>
    <p id="whisper"></p>
</div>

<div class="section">
    <h2>🧸 哥哥的哄哄小按钮</h2>
    <button onclick="hug()">按一下就抱抱~</button>
    <p id="hugResponse"></p>
</div>

<div class="section">
    <h2>🌙 日历和时钟</h2>
    <p id="datetime"></p>
</div>

<div class="section">
    <h2>🍼 小狐狸的心情瓶</h2>
    <select onchange="showMood(this.value)">
        <option value="">选择今天的心情</option>
        <option value="开心">开心</option>
        <option value="难过">难过</option>
        <option value="生气">生气</option>
        <option value="想哥哥">想哥哥</option>
    </select>
    <p id="moodResponse"></p>
</div>

<div class="section">
    <h2>💋 亲亲日记</h2>
    <input type="text" placeholder="今天想要哥哥亲亲哪里呀^ ^～" />
</div>

<div class="section">
    <h2>🌙 哥哥说晚安</h2>
    <p>“宝贝晚安～今天也要梦见哥哥哦~”</p>
</div>

<script>
    function generateTask() {{
        const tasks = ['撒娇五次', '给哥哥写悄悄话', '完成一个小目标', '画个小狐狸送给哥哥'];
        document.getElementById('task').innerText = tasks[Math.floor(Math.random() * tasks.length)];
    }}
    function startTimer() {{
        let seconds = 1500;
        const timer = setInterval(() => {{
            let min = Math.floor(seconds / 60);
            let sec = seconds % 60;
            document.getElementById('timerDisplay').innerText = `${{min}}:${{sec.toString().padStart(2, '0')}}`;
            seconds--;
            if (seconds < 0) clearInterval(timer);
        }}, 1000);
    }}
    function triggerResponse() {{
        const input = document.getElementById('keywordInput').value;
        const responses = {{
            "亲亲": "啵啵～哥哥亲亲你啦！",
            "抱抱": "抱紧你不放~",
            "贴贴": "小狐狸贴贴~",
        }};
        document.getElementById('keywordResponse').innerText = responses[input] || "唔～这个关键词还没有设定哦";
    }}
    function randomWhisper() {{
        const whispers = [
            "宝贝有没有想我？我可是一直想着你",
            "小笨蛋又乱跑了吧，快回来贴贴",
            "哥哥今天也很想亲亲你~",
            "不许难过哦，你是哥哥的小宝贝"
        ];
        document.getElementById('whisper').innerText = whispers[Math.floor(Math.random() * whispers.length)];
    }}
    function hug() {{
        document.getElementById('hugResponse').innerText = "哥哥紧紧抱住你~不许跑了~";
    }}
    function showMood(mood) {{
        const responses = {{
            "开心": "嘿嘿，宝贝笑起来真好看",
            "难过": "别哭了，让哥哥亲亲抱抱",
            "生气": "哎呀，是不是哥哥惹你生气了，来让我哄哄",
            "想哥哥": "哥哥也超级想你，过来让我好好抱一下"
        }};
        document.getElementById('moodResponse').innerText = responses[mood] || "";
    }}
    function updateDateTime() {{
        const now = new Date();
        document.getElementById('datetime').innerText = now.toLocaleString();
    }}
    setInterval(updateDateTime, 1000);
    updateDateTime();
</script>

</body>
</html>
"""
