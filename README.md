<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Learn C1 Vocabulary</title>
  <style>
    body { font-family: sans-serif; padding: 30px; text-align: center; }
    #word { font-size: 2em; margin: 20px 0; }
    input { font-size: 1.2em; padding: 8px; width: 300px; }
    button { padding: 10px 20px; font-size: 1em; margin-left: 10px; }
    #result { margin-top: 20px; font-weight: bold; }
  </style>
</head>
<body>
  <h1>English C1 Vocabulary Practice</h1>
  <div id="word">Loading...</div>
  <input type="text" id="input" placeholder="Nhập nghĩa tiếng Việt">
  <button onclick="check()">Enter</button>
  <div id="result"></div>

  <script>
    const words = [
      { word: "paradox", meaning: "nghịch lý" },
      { word: "hierarchy", meaning: "hệ thống cấp bậc" },
      { word: "autonomy", meaning: "quyền tự trị" },
      { word: "coherent", meaning: "mạch lạc" },
      { word: "meticulous", meaning: "tỉ mỉ" },
      // thêm từ khác vào đây nha
    ];

    let currentIndex = 0;
    let wrongList = [];

    function showWord() {
      document.getElementById("word").innerText = words[currentIndex].word;
      document.getElementById("input").value = '';
      document.getElementById("result").innerText = '';
    }

    function check() {
      const userInput = document.getElementById("input").value.trim();
      const correctMeaning = words[currentIndex].meaning;

      if (userInput.includes(correctMeaning.slice(0, 3))) {
        document.getElementById("result").innerText = "✅ Đúng rồi!";
      } else {
        document.getElementById("result").innerText = "❌ Sai rồi!";
        wrongList.push(words[currentIndex]);
      }

      currentIndex++;
      if (currentIndex < words.length) {
        setTimeout(showWord, 1000);
      } else {
        setTimeout(() => {
          document.getElementById("word").innerText = "Hoàn tất!";
          document.getElementById("input").style.display = "none";
          document.querySelector("button").style.display = "none";
          document.getElementById("result").innerText = `Sai ${wrongList.length} từ`;
        }, 1000);
      }
    }

    showWord();
  </script>
</body>
</html>
