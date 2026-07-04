<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Um Pedaço de Nós</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Raleway:wght@300;500&display=swap" rel="stylesheet">
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      font-family: 'Raleway', sans-serif;
      background: #fffaf5;
      margin: 0;
      color: #333;
      overflow-x: hidden;
    }

    header {
      background: linear-gradient(135deg, #ffb6c1, #ffc0cb);
      padding: 4rem 2rem;
      text-align: center;
      color: white;
      position: relative;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }

    header h1 {
      font-family: 'Great Vibes', cursive;
      font-size: 3.5rem;
      margin: 0;
      animation: fadeInDown 2s ease;
    }

    header p {
      font-size: 1.2rem;
      margin-top: 0.5rem;
      animation: fadeInUp 2s ease;
    }

    .container {
      max-width: 1000px;
      margin: auto;
      padding: 0 1rem;
    }

    section {
      padding: 3rem 0;
      text-align: center;
    }

    section h2 {
      font-family: 'Great Vibes', cursive;
      font-size: 2.2rem;
      color: #c71585;
      margin-bottom: 1rem;
      animation: fadeIn 2s ease;
    }

    section p {
      line-height: 1.8;
      font-size: 1.1rem;
      margin-bottom: 2rem;
      animation: fadeIn 3s ease;
    }

    /* Galeria */
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 1.5rem;
      margin: 2rem 0;
    }

    .gallery-item {
      position: relative;
      border-radius: 15px;
      overflow: hidden;
      box-shadow: 0 6px 12px rgba(0,0,0,0.2);
      border: 4px solid #ffc0cb;
      transition: transform 0.4s;
    }

    .gallery-item:hover {
      transform: scale(1.05);
    }

    .gallery-item img {
      width: 100%;
      height: 300px;
      object-fit: cover;
      display: block;
    }

    .gallery-item .delete-btn {
      position: absolute;
      top: 10px;
      right: 10px;
      background: rgba(199, 21, 133, 0.9);
      color: white;
      border: none;
      border-radius: 50%;
      width: 35px;
      height: 35px;
      cursor: pointer;
      font-size: 1.2rem;
      opacity: 0;
      transition: opacity 0.3s;
    }

    .gallery-item:hover .delete-btn {
      opacity: 1;
    }

    .delete-btn:hover {
      background: rgba(160, 19, 107, 0.9);
    }

    /* Upload de imagens */
    .upload-section {
      background: #f8e1e7;
      padding: 2rem;
      border-radius: 15px;
      margin: 2rem 0;
      border: 2px dashed #ffb6c1;
    }

    .upload-section h3 {
      color: #c71585;
      margin-top: 0;
    }

    .file-input-wrapper {
      position: relative;
      display: inline-block;
      margin: 1rem 0.5rem;
    }

    .file-input-wrapper input[type="file"] {
      display: none;
    }

    .file-label {
      display: inline-block;
      padding: 0.8rem 1.5rem;
      background: #c71585;
      color: white;
      border-radius: 20px;
      cursor: pointer;
      font-weight: bold;
      transition: background 0.3s;
    }

    .file-label:hover {
      background: #a0136b;
    }

    .upload-info {
      font-size: 0.9rem;
      color: #666;
      margin-top: 1rem;
    }

    /* Formulário de mensagem */
    .message-section {
      background: #f8e1e7;
      padding: 2rem;
      border-radius: 15px;
      margin: 2rem 0;
      animation: fadeIn 3s ease;
    }

    .message-section h3 {
      color: #c71585;
      margin-top: 0;
    }

    .form-group {
      margin: 1rem 0;
      text-align: left;
    }

    .form-group label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: bold;
      color: #c71585;
    }

    .form-group input,
    .form-group textarea {
      width: 100%;
      padding: 0.8rem;
      border: 2px solid #ffb6c1;
      border-radius: 8px;
      font-family: 'Raleway', sans-serif;
      font-size: 1rem;
      transition: border-color 0.3s;
    }

    .form-group input:focus,
    .form-group textarea:focus {
      outline: none;
      border-color: #c71585;
    }

    .form-group textarea {
      resize: vertical;
      min-height: 120px;
    }

    /* Botões */
    .button {
      display: inline-block;
      margin-top: 1rem;
      padding: 1rem 2rem;
      background: #c71585;
      color: white;
      text-decoration: none;
      border-radius: 30px;
      font-weight: bold;
      border: none;
      cursor: pointer;
      font-size: 1rem;
      transition: background 0.3s, transform 0.3s;
    }

    .button:hover {
      background: #a0136b;
      transform: scale(1.05);
    }

    .button:active {
      transform: scale(0.98);
    }

    /* Mensagens salvas */
    .messages-list {
      display: grid;
      gap: 1.5rem;
      margin-top: 2rem;
    }

    .message-card {
      background: white;
      padding: 1.5rem;
      border-radius: 12px;
      border-left: 4px solid #c71585;
      box-shadow: 0 3px 6px rgba(0,0,0,0.1);
      animation: slideIn 0.5s ease;
    }

    .message-card .author {
      font-weight: bold;
      color: #c71585;
      margin-bottom: 0.5rem;
    }

    .message-card .date {
      font-size: 0.85rem;
      color: #999;
      margin-bottom: 0.5rem;
    }

    .message-card .text {
      color: #333;
      line-height: 1.6;
    }

    .message-card .delete-msg-btn {
      margin-top: 1rem;
      padding: 0.5rem 1rem;
      background: #ff6b9d;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 0.9rem;
      transition: background 0.3s;
    }

    .message-card .delete-msg-btn:hover {
      background: #ff3d6b;
    }

    /* Player de música */
    .music-player {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: linear-gradient(135deg, #ffb6c1, #ffc0cb);
      padding: 1rem;
      border-radius: 20px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.3);
      z-index: 100;
    }

    .music-player audio {
      width: 220px;
      display: block;
    }

    .music-player label {
      display: block;
      color: white;
      font-weight: bold;
      margin-bottom: 0.5rem;
      font-size: 0.9rem;
    }

    /* Corações flutuando */
    .heart {
      position: fixed;
      bottom: -50px;
      font-size: 2rem;
      color: #ff69b4;
      animation: floatUp 6s linear infinite;
      z-index: 1;
    }

    /* Animações */
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    @keyframes fadeInDown {
      from { opacity: 0; transform: translateY(-30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes floatUp {
      0% { transform: translateY(0) rotate(0deg); opacity: 1; }
      100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
    }

    @keyframes slideIn {
      from { opacity: 0; transform: translateX(-20px); }
      to { opacity: 1; transform: translateX(0); }
    }

    footer {
      text-align: center;
      padding: 2rem;
      background: #f8e1e7;
      margin-top: 3rem;
      font-family: 'Great Vibes', cursive;
      font-size: 1.5rem;
      animation: fadeInUp 2s ease;
    }

    .error {
      color: #d9534f;
      background: #f8d7da;
      padding: 1rem;
      border-radius: 8px;
      margin: 1rem 0;
      border: 1px solid #f5c6cb;
    }

    .success {
      color: #155724;
      background: #d4edda;
      padding: 1rem;
      border-radius: 8px;
      margin: 1rem 0;
      border: 1px solid #c3e6cb;
    }

    .empty-state {
      padding: 2rem;
      color: #999;
      font-style: italic;
    }

    @media (max-width: 768px) {
      header h1 {
        font-size: 2.5rem;
      }

      section {
        padding: 2rem 0;
      }

      .music-player {
        bottom: 10px;
        right: 10px;
        padding: 0.8rem;
      }

      .music-player audio {
        width: 180px;
      }

      .gallery {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Um Pedaço de Nós</h1>
    <p>Memórias que guardamos com carinho</p>
  </header>

  <div class="container">
    <!-- Seção de História -->
    <section>
      <h2>Nossa História</h2>
      <p>
        Cada momento vivido é um pedaço de nós. Este espaço foi criado para eternizar
        lembranças, palavras e sentimentos que fazem parte da nossa jornada.
      </p>
    </section>

    <!-- Seção de Upload de Imagens -->
    <section>
      <div class="upload-section">
        <h3>📸 Adicione suas Fotos</h3>
        <div>
          <div class="file-input-wrapper">
            <input type="file" id="imageInput" accept="image/*" multiple>
            <label for="imageInput" class="file-label">+ Escolher Fotos</label>
          </div>
        </div>
        <div class="upload-info">
          Formatos suportados: JPG, PNG, GIF, WebP (máx 5MB por imagem)
        </div>
        <div id="uploadMessage"></div>
      </div>

      <!-- Galeria de Fotos -->
      <div id="galleryContainer">
        <h3 style="color: #c71585; margin-top: 2rem;">Galeria de Memórias</h3>
        <div class="gallery" id="gallery"></div>
        <div id="emptyGallery" class="empty-state">Nenhuma foto adicionada ainda</div>
      </div>
    </section>

    <!-- Seção de Música -->
    <section>
      <div class="upload-section">
        <h3>🎵 Adicione uma Música</h3>
        <div>
          <div class="file-input-wrapper">
            <input type="file" id="audioInput" accept="audio/*">
            <label for="audioInput" class="file-label">+ Escolher Áudio</label>
          </div>
        </div>
        <div class="upload-info">
          Formatos suportados: MP3, WAV, OGG, M4A (máx 50MB)
        </div>
        <div id="audioMessage"></div>
      </div>
    </section>

    <!-- Seção de Mensagens -->
    <section id="mensagem">
      <div class="message-section">
        <h3>💌 Deixe uma Mensagem</h3>
        <form id="messageForm">
          <div class="form-group">
            <label for="name">Seu Nome:</label>
            <input type="text" id="name" required placeholder="Digite seu nome...">
          </div>
          <div class="form-group">
            <label for="message">Sua Mensagem:</label>
            <textarea id="message" required placeholder="Escreva sua mensagem de amor e carinho..."></textarea>
          </div>
          <button type="submit" class="button">Enviar Mensagem</button>
          <div id="formMessage"></div>
        </form>
      </div>

      <!-- Mensagens Salvas -->
      <div>
        <h3 style="color: #c71585; margin-top: 2rem;">Mensagens Deixadas</h3>
        <div class="messages-list" id="messagesList">
          <div class="empty-state">Nenhuma mensagem ainda. Seja o primeiro a deixar uma! 💕</div>
        </div>
      </div>
    </section>
  </div>

  <!-- Player de música fixo -->
  <div class="music-player" id="musicPlayer" style="display: none;">
    <label>🎵 Música de Fundo</label>
    <audio id="audioPlayer" controls autoplay loop>
      Seu navegador não suporta áudio.
    </audio>
  </div>

  <!-- Corações flutuando -->
  <div class="heart" style="left:10%;">💖</div>
  <div class="heart" style="left:30%; animation-delay:2s;">💕</div>
  <div class="heart" style="left:50%; animation-delay:4s;">💓</div>
  <div class="heart" style="left:70%; animation-delay:1s;">💗</div>
  <div class="heart" style="left:90%; animation-delay:3s;">💞</div>

  <footer>
    Feito com amor 💕
  </footer>

  <script src="script.js"></script>
</body>
</html>
