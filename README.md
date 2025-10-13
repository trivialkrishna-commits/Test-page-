<!DOCTYPE html>
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
    const flashcards = [
      { question: "What is the powerhouse of the cell?", answer: "Mitochondria" },
      { question: "What molecule carries genetic information?", answer: "DNA" },
      { question: "What is the process of cell division in somatic cells called?", answer: "Mitosis" }
    ];

    let current = 0;
    let showingAnswer = false;

    function nextCard() {
      const card = document.getElementById('card');
      if (!showingAnswer) {
        // Show answer
        card.innerText = flashcards[current].answer;
        showingAnswer = true;
      } else {
        // Move to next question
        current = (current + 1) % flashcards.length;
        card.innerText = flashcards[current].question;
        showingAnswer = false;
      }
    }

    // Initialize first card
    document.getElementById('card').innerText = flashcards[current].question;
  </script>
</body>
</html>
