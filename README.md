
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { 
      font-family: Arial, sans-serif; 
      margin: 0; 
      padding: 10px; 
      font-size: 16px; 
      text-align: center; 
      background-color: black; 
      color: white; 
    }
    button { 
      font-size: 18px; 
      padding: 12px; 
      width: 100%; 
      margin-top: 20px; 
    }
  </style>
</head>
<body>
  <div id="chapterSelection">
    <p>Select a chapter:</p>
    <button onclick="startChapter('Cell Biology')">Cell Biology</button>
    <button onclick="startChapter('Genetics')">Genetics</button>
    <button onclick="startChapter('Anatomy')">Anatomy</button>
  </div>

  <div id="flashcardInterface" style="display:none;">
    <div id="card">Click below to start</div>
    <button onclick="nextCard()">Next / Show Answer</button>
  </div>

  <script>
    var decks = {
      "Cell Biology": [
        { question: "What is the powerhouse of the cell?", answer: "Mitochondria" },
        { question: "What organelle contains DNA?", answer: "Nucleus" }
      ],
      "Genetics": [
        { question: "What molecule carries genetic information?", answer: "DNA" },
        { question: "Process of copying DNA to RNA?", answer: "Transcription" }
      ],
      "Anatomy": [
        { question: "Largest organ in the human body?", answer: "Skin" },
        { question: "Main muscle for breathing?", answer: "Diaphragm" }
      ]
    };

    var currentDeck = [];
    var current = 0;
    var showingAnswer = false;
    var card = document.getElementById('card');

    function startChapter(chapter) {
      currentDeck = decks[chapter];
      current = 0;
      showingAnswer = false;
      document.getElementById('chapterSelection').style.display = 'none';
      document.getElementById('flashcardInterface').style.display = 'block';
      card.innerHTML = currentDeck[current].question;
    }

    function nextCard() {
      if (!showingAnswer) {
        card.innerHTML = currentDeck[current].answer + " ";
        showingAnswer = true;
      } else {
        current = (current + 1) % currentDeck.length;
        card.innerHTML = currentDeck[current].question;
        showingAnswer = false;
      }
    }
  </script>
</body>
</html>
