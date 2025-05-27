# DODO-Dream-Teams
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>DODO Cricket News</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      margin: 0;
      padding: 20px;
    }
    h1, h2 {
      color: #2c3e50;
    }
    .news-section {
      margin-top: 30px;
    }
    .news-item {
      background: #fff;
      padding: 15px;
      margin-bottom: 15px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .news-item h3 {
      margin: 0 0 10px;
    }
    .news-item a {
      text-decoration: none;
      color: #2980b9;
    }
    .news-item p {
      color: #555;
    }
    iframe {
      border: none;
      width: 100%;
      height: 500px;
      margin-top: 40px;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <h1>DODO Cricket News & Analysis</h1>

  <div class="news-section">
    <h2>Live Cricket News (via NewsAPI)</h2>
    <div id="news-articles">Loading news...</div>
  </div>

  <div class="news-section">
    <h2>Live Match Analysis (via Cricbuzz)</h2>
    <iframe src="https://www.cricbuzz.com/cricket-news" title="Cricbuzz Live News"></iframe>
  </div>

  <script>
    const apiKey = '60c9474092ba4a0f9b6dc8c528321149';
    const url = https://newsapi.org/v2/everything?q=cricket&language=en&sortBy=publishedAt&pageSize=5&apiKey=${apiKey};

    fetch(url)
      .then(response => response.json())
      .then(data => {
        const container = document.getElementById('news-articles');
        container.innerHTML = '';
        data.articles.forEach(article => {
          const div = document.createElement('div');
          div.className = 'news-item';
          div.innerHTML = 
            <h3><a href="${article.url}" target="_blank">${article.title}</a></h3>
            <p>${article.description || 'No description available.'}</p>
          ;
          container.appendChild(div);
        });
      })
      .catch(error => {
        document.getElementById('news-articles').innerHTML = 'News load nahi ho paayi.';
        console.error('Error fetching news:', error);
      });
  </script>
</body>
</html>
