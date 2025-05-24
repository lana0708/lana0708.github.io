<!DOCTYPE html>
<html>
<head>
  <title>나만의 간단 게시판</title>
</head>
<body>
  <h2>나만 쓰는 게시판</h2>
  <textarea id="postContent" rows="4" cols="50" placeholder="여기에 글을 쓰세요"></textarea><br>
  <button onclick="addPost()">글 등록</button>
  
  <h3>게시글 목록</h3>
  <div id="posts"></div>
  
  <script>
    function loadPosts() {
      const posts = JSON.parse(localStorage.getItem('posts') || '[]');
      const postsDiv = document.getElementById('posts');
      postsDiv.innerHTML = '';
      posts.forEach((post, index) => {
        const div = document.createElement('div');
        div.style.border = '1px solid #ccc';
        div.style.margin = '5px 0';
        div.style.padding = '5px';
        div.textContent = post;
        postsDiv.appendChild(div);
      });
    }
    function addPost() {
      const content = document.getElementById('postContent').value.trim();
      if (!content) return alert('내용을 입력하세요!');
      const posts = JSON.parse(localStorage.getItem('posts') || '[]');
      posts.unshift(content);
      localStorage.setItem('posts', JSON.stringify(posts));
      document.getElementById('postContent').value = '';
      loadPosts();
    }
    loadPosts();
  </script>
</body>
</html>
