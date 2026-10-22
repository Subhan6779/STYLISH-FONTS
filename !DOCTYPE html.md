<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>FancyTextPro - Unlimited 1000+ Stylish Font Generator</title>  
    <style>  
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }  
        body { background-color: #0b0f19; color: #f1f5f9; padding-bottom: 50px; }  
        header { background-color: #111827; padding: 20px; text-align: center; border-bottom: 3px solid #8b5cf6; position: sticky; top: 0; z-index: 100; }  
        header h1 { font-size: 22px; color: #a78bfa; font-weight: 900; }  
        header p { color: #9ca3af; font-size: 12px; margin-top: 5px; }  
        .container { max-width: 800px; margin: 20px auto; padding: 0 15px; }  
        .input-box { width: 100%; padding: 16px; font-size: 16px; background-color: #111827; border: 2px solid #8b5cf6; border-radius: 12px; color: white; outline: none; margin-bottom: 15px; }  
        .font-card { background-color: #111827; border-radius: 10px; padding: 12px 15px; margin-bottom: 10px; display: flex; align-items: center; justify-content: space-between; border: 1px solid #1f2937; gap: 15px; }  
        .font-title { font-size: 10px; color: #9ca3af; margin-bottom: 3px; font-weight: 600; text-transform: uppercase; }  
        .font-text { font-size: 17px; word-break: break-all; color: #ffffff; font-weight: 500; }  
        .copy-btn { padding: 7px 14px; background-color: #8b5cf6; color: white; border: none; border-radius: 6px; font-weight: bold; font-size: 12px; cursor: pointer; flex-shrink: 0; }  
        .copy-btn.copied { background-color: #10b981; }  
        .footer { text-align: center; margin-top: 35px; font-size: 12px; color: #6b7280; }  
    </style>  
</head>  
<body>  
    <header>  
        <h1>✨ FancyTextPro</h1>  
        <p>Unlimited 1000+ Stylish Fonts & Gamer Tags Generator</p>  
    </header>  
  
    <div class="container">  
        <input type="text" id="userInput" class="input-box" placeholder="Type text here..." oninput="generateFonts()" value="Chaudhary">  
        <div id="resultsList"></div>  
    </div>  
  
    <div class="footer">  
        © 2026 FancyTextPro | Unlimited Font Generator Engine  
    </div>  
  
    <script>  
        const maps = {  
            sansBold: {a:'𝗮',b:'𝗯',c:'𝗰',d:'𝗱',e:'𝗲',f:'𝗳',g:'𝗴',h:'𝗵',i:'𝗶',j:'𝗷',k:'𝗸',l:'𝗹',m:'𝗺',n:'𝗻',o:'𝗼',p:'𝗽',q:'𝗾',r:'𝗿',s:'𝘀',t:'𝘁',u:'𝘂',v:'𝘃',w:'𝘄',x:'𝘅',y:'𝘆',z:'𝘇',A:'𝗔',B:'𝗕',C:'𝗖',D:'𝗗',E:'𝗘',F:'𝗙',G:'𝗚',H:'𝗛',I:'𝗜',J:'𝗝',K:'𝗞',L:'𝗟',M:'𝗠',N:'𝗡',O:'𝗢',P:'𝗣',Q:'𝗤',R:'𝗥',S:'𝗦',T:'𝗧',U:'𝗨',V:'𝗩',W:'𝗪',X:'𝗫',Y:'𝗬',Z:'𝗭'},  
            script: {a:'𝒶',b:'𝒷',c:'𝒸',d:'𝒹',e:'ℯ',f:'𝒻',g:'ℊ',h:'𝒽',i:'𝒾',j:'𝒿',k:'𝓀',l:'𝓁',m:'𝓂',n:'𝓃',o:'ℴ',p:'𝓅',q:'𝓆',r:'𝓇',s:'𝓈',t:'𝓉',u:'𝓊',v:'𝒱',w:'𝓌',x:'𝒳',y:'𝓎',z:'𝒛',A:'𝒜',B:'ℬ',C:'𝒞',D:'𝒟',E:'ℰ',F:'ℱ',G:'𝒢',H:'ℋ',I:'ℐ',J:'𝒥',K:'𝒦',L:'ℒ',M:'ℳ',N:'𝒩',O:'𝒪',P:'𝒫',Q:'𝒬',R:'ℛ',S:'𝒮',T:'𝒯',U:'𝒰',V:'𝒱',W:'𝒲',X:'𝒳',Y:'𝒴',Z:'𝒵'},  
            fraktur: {a:'𝔞',b:'𝔟',c:'𝔠',d:'𝔡',e:'𝔢',f:'𝔣',g:'𝔤',h:'𝔥',i:'𝔦',j:'𝔧',k:'𝔨',l:'𝔩',m:'𝔪',n:'𝔫',o:'𝔬',p:'𝔭',q:'𝔮',r:'𝔯',s:'𝔰',t:'𝔱',u:'𝔲',v:'𝔳',w:'𝔴',x:'𝔵',y:'𝔶',z:'𝔷',A:'𝔄',B:'ℬ',C:'𝔭',D:'𝔇',E:'𝔈',F:'𝔉',G:'𝔊',H:'ℌ',I:'ℑ',J:'𝔍',K:'𝔎',L:'𝔏',M:'Ⓜ',N:'𝔑',O:'𝔒',P:'𝔓',Q:'𝔔',R:'ℜ',S:'𝔖',T:'𝔗',U:'𝔘',V:'𝔙',W:'𝔚',X:'𝔛',Y:'𝔜',Z:'ℨ'}  
        };  
        const prefixes = ["👑", "⚡", "🔥", "💎", "★", "꧁༺", "⚔️", "🎯", "🐉", "🚀"];  
        const suffixes = ["👑", "⚡", "🔥", "💎", "★", "༻꧂", "⚔️", "🎯", "🐉", "🚀"];  
  
        function convert(text, map) {  
            return text.split('').map(c => map[c] || c).join('');  
        }  
  
        function generateFonts() {  
            let text = document.getElementById('userInput').value || "Chaudhary";  
            let resultsDiv = document.getElementById('resultsList');  
            resultsDiv.innerHTML = '';  
            let fragment = document.createDocumentFragment();  
  
            for(let i = 1; i <= 200; i++) {  
                let p = prefixes[i % prefixes.length];  
                let s = suffixes[i % suffixes.length];  
                let val = `${p} ${convert(text, maps.sansBold)} ${s}`;  
                if(i % 2 === 0) val = `${p} ${convert(text, maps.script)} ${s}`;  
                if(i % 3 === 0) val = `${p} ${convert(text, maps.fraktur)} ${s}`;  
  
                let card = document.createElement('div');  
                card.className = 'font-card';  
                card.innerHTML = `  
                    <div>  
                        <div class="font-title">Style #${i}</div>  
                        <div class="font-text">${val}</div>  
                    </div>  
                    <button class="copy-btn" onclick="copyText('${val}', this)">Copy</button>  
                `;  
                fragment.appendChild(card);  
            }  
            resultsDiv.appendChild(fragment);  
        }  
  
        function copyText(text, btn) {  
            navigator.clipboard.writeText(text);  
            btn.innerText = "Copied! ✓";  
            btn.classList.add('copied');  
            setTimeout(() => { btn.innerText = "Copy"; btn.classList.remove('copied'); }, 1200);  
        }  
        generateFonts();  
    </script>  
</body>  
</html>  
