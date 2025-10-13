<!DOCTYPE html>
<html>
<head>
  <title>Biology Flashcards</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { font-family: Arial, sans-serif; margin: 10px; font-size: 16px; }
    .card { border: 2px solid #28a745; padding: 15px; margin: 10px 0; text-align: center; }
    button { font-size: 16px; padding: 8px; margin: 5px; width: 100%; }
  </style>
</head>
<body>
  <h2>Biology Flashcards</h2>
  <div class="card" id="card">Click "Show Answer" to start</div>
  <button onclick="showAnswer()">Show Answer</button>
  <button onclick="nextCard()">Next</button>
  <button onclick="prevCard()">Previous</button>

  <script>
    // === Add your flashcards here ===
    const flashcards = [
      { question: "What is the powerhouse of the cell?", answer: "Mitochondria" },
      { question: "What molecule carries genetic information?", answer: "DNA" },
      { question: "What is the process of cell division in somatic cells called?", answer: "Mitosis" }
    ];

    let current = 0;
    let showingAnswer = false;

    function showAnswer() {
      const card = document.getElementById('card');
      if (!showingAnswer) {
        card.innerText = flashcards[current].answer;
        showingAnswer = true;
      } else {
        card.innerText = flashcards[current].question;
        showingAnswer = false;
      }
    }

    function nextCard() {
      current = (current + 1) % flashcards.length;
      document.getElementById('card').innerText = flashcards[current].question;
      showingAnswer = false;
    }

    function prevCard() {
      current = (current - 1 + flashcards.length) % flashcards.length;
      document.getElementById('card').innerText = flashcards[current].question;
      showingAnswer = false;
    }
  </script>
</body>
</html>
