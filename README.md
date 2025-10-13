<!DOCTYPE html>
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
    .chapter-btn { 
      margin: 10px 0; 
      width: auto; 
      display: block; 
    }
  </style>
</head>
<body>

  <div id="chapterSelection">
    <p>Select a chapter:</p>
    <button class="chapter-btn" onclick="startChapter('Morphology')">Morphology</button>
    <button class="chapter-btn" onclick="startChapter('Skeletal System')">Skeletal System</button>
    <button class="chapter-btn" onclick="startChapter('Circulation')">Circulation</button>
  </div>

  <div id="flashcardInterface" style="display:none;">
    <div id="card">Click below to start</div>
    <button onclick="nextCard()">Next / Show Answer</button>
  </div>

  <script>
    var decks = {
      "Morphology": [
        // You can add morphology flashcards here later
      ],
      "Skeletal System": [
        { question: "Chondroitin salts are present in", answer: "Cartilage" },
        { question: "Total number of bones in human body", answer: "206" },
        { question: "Number of bones in axial skeleton", answer: "80" },
        { question: "Axial skeleton comprises of", answer: "skull , vertebral column , ribs , sternum" },
        { question: "Number of bones in skull", answer: "29" },
        { question: "Number of cranial bones", answer: "8" },
        { question: "Number of facial bones", answer: "14" },
        { question: "Name all the cranial bones", answer: "Frontal , Parietal , Occipital , Temporal , ethmoid , sphenoid" },
        { question: "Name all the facial bones", answer: "—" }, // Fill later if you want
        { question: "The skull region articulates with vertebral column by", answer: "Occipital Condyle" },
        { question: "First vertebrae is", answer: "ATLAS" },
        { question: "Second vertebrae is called", answer: "AXIS" },
        { question: "Number of bones in vertebral column", answer: "26" },
        { question: "The number of bones in cervical", answer: "7" },
        { question: "Number of bones in thoracic", answer: "12" },
        { question: "A number of bones in lumbar", answer: "5" },
        { question: "Sacrum and Coccygeal", answer: "1 EACH" },
        { question: "Each vertebrae has ____ through its final chord passes", answer: "Neural canal" },
        { question: "The atlas and occipital condyle form a______ joint ,Which helps in____ Movement", answer: "Condylar , nodding" },
        { question: "The ATLAS & axis form a ___ joint which helps in___ movement", answer: "Pivot joint , rotatory (NO)" },
        { question: "No bone is", answer: "Axis" },
        { question: "Yes Bone is", answer: "Atlas" },
        { question: "Mammal which does not has 7 cervical vertebrae", answer: "Bradypus" },
        { question: "Number of cervical vertebrae in Bradypus", answer: "9" },
        { question: "Ribs have two articular surfaces on its ventral / dorsal end ,hence are called__", answer: "Dorsal , BICEPHALLIC" },
        { question: "Number of true ribs", answer: "7" },
        { question: "True ribs are connected to sternum via help of (NEET)", answer: "Hyaline cartilage" },
        { question: "What pair of ribs is called vertebrochondral ribs (NEET)", answer: "8,9,10" },
        { question: "False ribs are also called", answer: "Vertebrochondral ribs" },
        { question: "False ribs are joined with the help of hyaline cartilage to the __ rib", answer: "7th rib" },
        { question: "What pairs are floating ribs", answer: "11 , 12" },
        { question: "Number of bones in each limb", answer: "30" },
        { question: "Number of carpels(in each)", answer: "8" },
        { question: "Tarsals (in each)", answer: "7" },
        { question: "Longest bone in human body", answer: "Femur" },
        { question: "Each half of pectoral girdle consists of ___ & ___", answer: "Scapula and clavicle" },
        { question: "Scapula is situated between", answer: "2nd & 7th rib" },
        { question: "Scapula has a slightly elevated ridge called", answer: "Spine" },
        { question: "Spine projects has a flat expanded process called", answer: "Acromion process" },
        { question: "Glenoid cavities present above acromion T/F", answer: "False , below acromion" },
        { question: "Clavicle articulates with __&__", answer: "sternum and acromion" },
        { question: "_____ Articulates with the head of humorous to form shoulder joint", answer: "Glenoid cavity" },
        { question: "Other name for collarbone", answer: "Clavicle" },
        { question: "Each coxal bone is formed by the fusion of (3)", answer: "Ilium , Ischium , Pubis" },
        { question: "At the point of fusion a cavity is formed called", answer: "Acetabulum" },
        { question: "Pubic symphysis contain Hyaline/Fibrous cartilage", answer: "Fibrous" },
        { question: "3 types of joints", answer: "Fibrous , cartilaginous , Synovial" },
        { question: "Fibrous joints are present in", answer: "Cranium" },
        { question: "In cranium , bones Are connected with the help of ___ in the form of___", answer: "Dense fibrous connective tissue , suture" },
        { question: "example of cartilaginous joints(2)", answer: "sternum-ribs , pubic symphysis" },
        { question: "Example of gliding joint", answer: "Between carpals" },
        { question: "Saddle joint", answer: "between carpals and metacarpals of thumb" },
        { question: "Join between phalanges is a type of", answer: "Hinge joint" },
        { question: "Rheumatoid Arthritis Involves inflammation of", answer: "synovial membrane" },
        { question: "Rheumatoid arthritis is an autoimmune disorder T/F", answer: "True" },
        { question: "Osteoarthritis is the most common disorder of joints T/F", answer: "True" },
        { question: "Progressive erosion of articular cartilage", answer: "Osteoarthritis" },
        { question: "Gouty arthritis involves defect in aniline metabolism T/F?", answer: "False , PURINE" },
        { question: "Excessive urea is formed in gout T/F", answer: "False , Uric acid" },
        { question: "Osteoporosis is a gender related disorder T/F?", answer: "False , age related" },
        { question: "Bone mass decreases in osteoporosis T/F?", answer: "True" },
        { question: "Low level of estrogen in female may cause osteoporosis", answer: "True" },
        { question: "Sprain: excessive pulling of tendons T/F", answer: "False , ligament" }
      ],
      "Circulation": [
        // You can add circulation flashcards here later
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
