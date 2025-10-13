<!DOCTYPE html>
<html>
<head>
  <title>Biology Flashcards</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; font-size: 16px; text-align: center; background-color: black; color: white; }
    .card { border: 2px solid #28a745; padding: 20px; margin: 20px 10px; min-height: 60px; }
    button { font-size: 18px; padding: 12px; width: 100%; margin-top: 10px; }
    .chapter-btn { margin: 5px 10px; padding: 12px; width: auto; display: block; }
  </style>
</head>
<body>
  <h2>Biology Flashcards</h2>

  <div id="chapterSelection">
    <p>Select a chapter:</p>
    <button class="chapter-btn" onclick="startChapter('Cell Biology')">Cell Biology</button>
    <button class="chapter-btn" onclick="startChapter('Genetics')">Genetics</button>
    <button class="chapter-btn" onclick="startChapter('Anatomy')">Anatomy</button>
  </div>

  <div id="flashcardInterface" style="display:none;">
    <div class="card" id="card">Click below to start</div>
    <button onclick="nextCard()">Next / Show Answer</button>
    <p id="progress"></p>
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
    var progress = document.getElementById('progress');

    function startChapter(chapter) {
      currentDeck = decks[chapter];
      current = 0;
      showingAnswer = false;
      document.getElementById('chapterSelection').style.display = 'none';
      document.getElementById('flashcardInterface').style.display = 'block';
      card.innerHTML = currentDeck[current].question;
      progress.innerHTML = "Card 1 of " + currentDeck.length;
    }

    function nextCard() {
      if (!showingAnswer) {
        card.innerHTML = currentDeck[current].answer + " ";
        showingAnswer = true;
      } else {
        current = (current + 1) % currentDeck.length;
        card.innerHTML = currentDeck[current].question;
        showingAnswer = false;
        progress.innerHTML = "Card " + (current + 1) + " of " + currentDeck.length;
      }
    }
  </script>
</body>
</html>

