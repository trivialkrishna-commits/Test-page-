
<html>
<head>
  <title>Biology Flashcards</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { font-family: Arial, sans-serif; margin: 10px; font-size: 16px; text-align: center; }
    .card { border: 2px solid #28a745; padding: 20px; margin: 20px 0; min-height: 60px; }
    button { font-size: 18px; padding: 12px; width: 100%; }
  </style>
</head>
<body>
  <h2>Biology Flashcards</h2>
  <div class="card" id="card">Click below to start</div>
  <button onclick="nextCard()">Next / Show Answer</button>

  <script>
    var flashcards = [
      { question: "What is the powerhouse of the cell?", answer: "Mitochondria" },
      { question: "What molecule carries genetic information?", answer: "DNA" },
      { question: "What is the process of cell division in somatic cells called?", answer: "Mitosis" }
    ];

    var current = 0;
    var showingAnswer = false;
    var card = document.getElementById('card');

    // Initialize first card
    card.innerHTML = flashcards[current].question;

    function nextCard() {
      if (!showingAnswer) {
        card.innerHTML = flashcards[current].answer + " "; // extra space forces repaint
        showingAnswer = true;
      } else {
        current = (current + 1) % flashcards.length;
        card.innerHTML = flashcards[current].question;
        showingAnswer = false;
      }
    }
  </script>
</body>
</html>
