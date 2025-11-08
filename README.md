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
      "Chemical coordination": [
        [
  { "question": "\"You have already learnt that the neural system provides a point-to-point rapid coordination among organs.\" T/F?", "answer": "True" },
  { "question": "\"The neural coordination is fast but short-lived.\" T/F?", "answer": "True" },
  { "question": "\"As the nerve fibres do not innervate all cells of the body and the cellular functions need to be continuously regulated; a special kind of coordination and integration has to be provided.\" T/F?", "answer": "True" },
  { "question": "\"This function is carried out by hormones.\" T/F?", "answer": "True" },
  { "question": "\"The neural system and the endocrine system jointly coordinate and regulate the physiological functions in the body.\" T/F?", "answer": "True" },
  { "question": "\"Endocrine glands lack ducts and are hence, called ductless glands.\" T/F?", "answer": "True" },
  { "question": "\"Their secretions are called hormones.\" T/F?", "answer": "True" },
  { "question": "\"The classical definition of hormone as a chemical produced by endocrine glands and released into the blood and transported to a distantly located target organ has current scientific definition as follows: Hormones are non-nutrient chemicals which act as intercellular messengers and are produced in trace amounts.\" T/F?", "answer": "True" },
  { "question": "\"The new definition covers a number of new molecules in addition to the hormones secreted by the organised endocrine glands.\" T/F?", "answer": "True" },
  { "question": "\"Invertebrates possess very simple endocrine systems with few hormones whereas a large number of chemicals act as hormones and provide coordination in the vertebrates.\" T/F?", "answer": "True" },
  { "question": "\"The human endocrine system is described here.\" T/F?", "answer": "True" },
  { "question": "\"The endocrine glands and hormone producing diffused tissues/cells located in different parts of our body constitute the endocrine system.\" T/F?", "answer": "True" },
  { "question": "\"Pituitary, pineal, thyroid, adrenal, pancreas, parathyroid, thymus and gonads (testis in males and ovary in females) are the organised endocrine bodies in our body.\" T/F?", "answer": "True" },
  { "question": "\"In addition to these, some other organs, e.g., gastrointestinal tract, liver, kidney, heart also produce hormones.\" T/F?", "answer": "True" },
  { "question": "\"A brief account of the structure and functions of all major endocrine glands and hypothalamus of the human body is given in the following sections.\" T/F?", "answer": "True" },
  { "question": "\"As you know, the hypothalamus is the basal part of diencephalon, forebrain and it regulates a wide spectrum of body functions.\" T/F?", "answer": "True" },
  { "question": "\"It contains several groups of neurosecretory cells called nuclei which produce hormones.\" T/F?", "answer": "True" },
  { "question": "\"These hormones regulate the synthesis and secretion of pituitary hormones.\" T/F?", "answer": "True" },
  { "question": "\"However, the hormones produced by hypothalamus are of two types, the releasing hormones (which stimulate secretion of pituitary hormones) and the inhibiting hormones (which inhibit secretions of pituitary hormones).\" T/F?", "answer": "True" },
  { "question": "\"For example a hypothalamic hormone called Gonadotrophin releasing hormone (GnRH) stimulates the pituitary synthesis and release of gonadotrophins.\" T/F?", "answer": "True" },
  { "question": "\"On the other hand, somatostatin from the hypothalamus inhibits the release of growth hormone from the pituitary.\" T/F?", "answer": "True" },
  { "question": "\"These hormones originating in the hypothalamic neurons, pass through axons and are released from their nerve endings.\" T/F?", "answer": "True" },
  { "question": "\"These hormones reach the pituitary gland through a portal circulatory system and regulate the functions of the anterior pituitary.\" T/F?", "answer": "True" },
  { "question": "\"The posterior pituitary is under the direct neural regulation of the hypothalamus.\" T/F?", "answer": "True" },
  { "question": "\"The pituitary gland is located in a bony cavity called sella tursica and is attached to hypothalamus by a stalk.\" T/F?", "answer": "True" },
  { "question": "\"It is divided anatomically into an adenohypophysis and a neurohypophysis.\" T/F?", "answer": "True" },
  { "question": "\"Adenohypophysis consists of two portions, pars distalis and pars intermedia.\" T/F?", "answer": "True" },
  { "question": "\"The pars distalis region of pituitary, commonly called anterior pituitary, produces growth hormone (GH), prolactin (PRL), thyroid stimulating hormone (TSH), adrenocorticotrophic hormone (ACTH), luteinizing hormone (LH) and follicle stimulating hormone (FSH).\" T/F?", "answer": "True" },
  { "question": "\"Pars intermedia secretes only one hormone called melanocyte stimulating hormone (MSH).\" T/F?", "answer": "True" },
  { "question": "\"However, in humans, the pars intermedia is almost merged with pars distalis.\" T/F?", "answer": "True" },
  { "question": "\"Neurohypophysis (pars nervosa) also known as posterior pituitary, stores and releases two hormones called oxytocin and vasopressin, which are actually synthesised by the hypothalamus and are transported axonally to neurohypophysis.\" T/F?", "answer": "True" },
  { "question": "\"Over-secretion of GH stimulates abnormal growth of the body leading to gigantism and low secretion of GH results in stunted growth resulting in pituitary dwarfism.\" T/F?", "answer": "True" },
  { "question": "\"Excess secretion of growth hormone in adults especially in middle age can result in severe disfigurement (especially of the face) called Acromegaly, which may lead to serious complications, and premature death if unchecked.\" T/F?", "answer": "True" },
  { "question": "\"The disease is hard to diagnose in the early stages and often goes undetected for many years, until changes in external features become noticeable.\" T/F?", "answer": "True" },
  { "question": "\"Prolactin regulates the growth of the mammary glands and formation of milk in them.\" T/F?", "answer": "True" },
  { "question": "\"TSH stimulates the synthesis and secretion of thyroid hormones from the thyroid gland.\" T/F?", "answer": "True" },
  { "question": "\"ACTH stimulates the synthesis and secretion of steroid hormones called glucocorticoids from the adrenal cortex.\" T/F?", "answer": "True" },
  { "question": "\"LH and FSH stimulate gonadal activity and hence are called gonadotrophins.\" T/F?", "answer": "True" },
  { "question": "\"In males, LH stimulates the synthesis and secretion of hormones called androgens from testis.\" T/F?", "answer": "True" },
  { "question": "\"In males, FSH and androgens regulate spermatogenesis.\" T/F?", "answer": "True" },
  { "question": "\"In females, LH induces ovulation of fully mature follicles (graafian follicles) and maintains the corpus luteum, formed from the remnants of the graafian follicles after ovulation.\" T/F?", "answer": "True" },
  { "question": "\"FSH stimulates growth and development of the ovarian follicles in females.\" T/F?", "answer": "True" },
  { "question": "\"MSH acts on the melanocytes (melanin containing cells) and regulates pigmentation of the skin.\" T/F?", "answer": "True" },
  { "question": "\"Oxytocin acts on the smooth muscles of our body and stimulates their contraction.\" T/F?", "answer": "True" },
  { "question": "\"In females, it stimulates a vigorous contraction of uterus at the time of child birth, and milk ejection from the mammary gland.\" T/F?", "answer": "True" },
  { "question": "\"Vasopressin acts mainly at the kidney and stimulates resorption of water and electrolytes by the distal tubules and thereby reduces loss of water through urine (diuresis).\" T/F?", "answer": "True" },
  { "question": "\"Hence, it is also called as anti-diuretic hormone (ADH).\" T/F?", "answer": "True" },
  { "question": "\"An impairment affecting synthesis or release of ADH results in a diminished ability of the kidney to conserve water leading to water loss and dehydration.\" T/F?", "answer": "True" },
  { "question": "\"This condition is known as Diabetes Insipidus.\" T/F?", "answer": "True" },
  { "question": "\"The pineal gland is located on the dorsal side of forebrain.\" T/F?", "answer": "True" },
  { "question": "\"Pineal secretes a hormone called melatonin.\" T/F?", "answer": "True" },
  { "question": "\"Melatonin plays a very important role in the regulation of a 24-hour (diurnal) rhythm of our body.\" T/F?", "answer": "True" },
  { "question": "\"For example, it helps in maintaining the normal rhythms of sleep-wake cycle, body temperature.\" T/F?", "answer": "True" },
  { "question": "\"In addition, melatonin also influences metabolism, pigmentation, the menstrual cycle as well as our defense capability.\" T/F?", "answer": "True" },
  { "question": "\"The thyroid gland is composed of two lobes which are located on either side of the trachea.\" T/F?", "answer": "True" },
  { "question": "\"Both the lobes are interconnected with a thin flap of connective tissue called isthmus.\" T/F?", "answer": "True" },
  { "question": "\"The thyroid gland is composed of follicles and stromal tissues.\" T/F?", "answer": "True" },
  { "question": "\"Each thyroid follicle is composed of follicular cells, enclosing a cavity.\" T/F?", "answer": "True" },
  { "question": "\"These follicular cells synthesise two hormones, tetraiodothyronine or thyroxine (T4) and triiodothyronine (T3).\" T/F?", "answer": "True" },
  { "question": "\"Iodine is essential for the normal rate of hormone synthesis in the thyroid.\" T/F?", "answer": "True" },
  { "question": "\"Deficiency of iodine in our diet results in hypothyroidism and enlargement of the thyroid gland, commonly called goitre.\" T/F?", "answer": "True" },
  { "question": "\"Hypothyroidism during pregnancy causes defective development and maturation of the growing baby leading to stunted growth (cretinism), mental retardation, low intelligence quotient, abnormal skin, deaf-mutism, etc.\" T/F?", "answer": "True" },
  { "question": "\"In adult women, hypothyroidism may cause menstrual cycle to become irregular.\" T/F?", "answer": "True" },
  { "question": "\"Due to cancer of the thyroid gland or due to development of nodules of the thyroid glands, the rate of synthesis and secretion of the thyroid hormones is increased to abnormal high levels leading to a condition called hyperthyroidism which adversely affects the body physiology.\" T/F?", "answer": "True" },
  { "question": "\"Exopthalmic goitre is a form of hyperthyroidism, characterised by enlargement of the thyroid gland, protrusion of the eyeballs, increased basal metabolic rate, and weight loss, also called Graves’ disease.\" T/F?", "answer": "True" },
  { "question": "\"Thyroid hormones play an important role in the regulation of the basal metabolic rate.\" T/F?", "answer": "True" },
  { "question": "\"These hormones also support the process of red blood cell formation.\" T/F?", "answer": "True" },
  { "question": "\"Thyroid hormones control the metabolism of carbohydrates, proteins and fats.\" T/F?", "answer": "True" },
  { "question": "\"Maintenance of water and electrolyte balance is also influenced by thyroid hormones.\" T/F?", "answer": "True" },
  { "question": "\"Thyroid gland also secretes a protein hormone called thyrocalcitonin (TCT) which regulates the blood calcium levels.\" T/F?", "answer": "True" },
  { "question": "\"In humans, four parathyroid glands are present on the back side of the thyroid gland, one pair each in the two lobes of the thyroid gland.\" T/F?", "answer": "True" },
  { "question": "\"The parathyroid glands secrete a peptide hormone called parathyroid hormone (PTH).\" T/F?", "answer": "True" },
  { "question": "\"The secretion of PTH is regulated by the circulating levels of calcium ions.\" T/F?", "answer": "True" },
  { "question": "\"Parathyroid hormone (PTH) increases the Ca2+ levels in the blood.\" T/F?", "answer": "True" },
  { "question": "\"PTH acts on bones and stimulates the process of bone resorption (dissolution/demineralisation).\" T/F?", "answer": "True" },
  { "question": "\"PTH also stimulates reabsorption of Ca2+ by the renal tubules and increases Ca2+ absorption from the digested food.\" T/F?", "answer": "True" },
  { "question": "\"It is, thus, clear that PTH is a hypercalcemic hormone, i.e., it increases the blood Ca2+ levels.\" T/F?", "answer": "True" },
  { "question": "\"Along with TCT, it plays a significant role in calcium balance in the body.\" T/F?", "answer": "True" },
  { "question": "\"The thymus gland is a lobular structure located between lungs behind sternum on the ventral side of aorta.\" T/F?", "answer": "True" },
  { "question": "\"The thymus plays a major role in the development of the immune system.\" T/F?", "answer": "True" },
  { "question": "\"This gland secretes the peptide hormones called thymosins.\" T/F?", "answer": "True" },
  { "question": "\"Thymosins play a major role in the differentiation of T-lymphocytes, which provide cell-mediated immunity.\" T/F?", "answer": "True" },
  { "question": "\"In addition, thymosins also promote production of antibodies to provide humoral immunity.\" T/F?", "answer": "True" },
  { "question": "\"Thymus is degenerated in old individuals resulting in a decreased production of thymosins.\" T/F?", "answer": "True" },
  { "question": "\"As a result, the immune responses of old persons become weak.\" T/F?", "answer": "True" },
  { "question": "\"The adrenal medulla secretes two hormones called adrenaline or epinephrine and noradrenaline or norepinephrine.\" T/F?", "answer": "True" },
  { "question": "\"These are commonly called as catecholamines.\" T/F?", "answer": "True" },
  { "question": "\"Adrenaline and noradrenaline are rapidly secreted in response to stress of any kind and during emergency situations and are called emergency hormones or hormones of Fight or Flight.\" T/F?", "answer": "True" },
  { "question": "\"These hormones increase alertness, pupilary dilation, piloerection (raising of hairs), sweating etc.\" T/F?", "answer": "True" },
  { "question": "\"Both the hormones increase the heart beat, the strength of heart contraction and the rate of respiration.\" T/F?", "answer": "True" },
  { "question": "\"Catecholamines also stimulate the breakdown of glycogen resulting in an increased concentration of glucose in blood.\" T/F?", "answer": "True" },
  { "question": "\"In addition, they also stimulate the breakdown of lipids and proteins.\" T/F?", "answer": "True" },
  { "question": "\"The adrenal cortex can be divided into three layers, called zona reticularis (inner layer), zona fasciculata (middle layer) and zona glomerulosa (outer layer).\" T/F?", "answer": "True" },
  { "question": "\"The adrenal cortex secretes many hormones, commonly called as corticoids.\" T/F?", "answer": "True" },
  { "question": "\"The corticoids, which are involved in carbohydrate metabolism are called glucocorticoids.\" T/F?", "answer": "True" },
  { "question": "\"In our body, cortisol is the main glucocorticoid.\" T/F?", "answer": "True" },
  { "question": "\"Corticoids, which regulate the balance of water and electrolytes in our body are called mineralocorticoids.\" T/F?", "answer": "True" },
  { "question": "\"Aldosterone is the main mineralocorticoid in our body.\" T/F?", "answer": "True" },
  { "question": "\"Glucocorticoids stimulate gluconeogenesis, lipolysis and proteolysis; and inhibit cellular uptake and utilisation of amino acids.\" T/F?", "answer": "True" },
  { "question": "\"Cortisol is also involved in maintaining the cardio-vascular system as well as the kidney functions.\" T/F?", "answer": "True" },
  { "question": "\"Glucocorticoids, particularly cortisol, produces anti-inflammatory reactions and suppresses the immune response.\" T/F?", "answer": "True" },
  { "question": "\"Cortisol stimulates the RBC production.\" T/F?", "answer": "True" },
  { "question": "\"Aldosterone acts mainly at the renal tubules and stimulates the reabsorption of Na+ and water and excretion of K+ and phosphate ions.\" T/F?", "answer": "True" },
  { "question": "\"Thus, aldosterone helps in the maintenance of electrolytes, body fluid volume, osmotic pressure and blood pressure.\" T/F?", "answer": "True" },
  { "question": "\"Small amounts of androgenic steroids are also secreted by the adrenal cortex which play a role in the growth of axial hair, pubic hair and facial hair during puberty.\" T/F?", "answer": "True" },
  { "question": "\"Pancreas is a composite gland which acts as both exocrine and endocrine gland.\" T/F?", "answer": "True" },
  { "question": "\"The endocrine pancreas consists of ‘Islets of Langerhans’.\" T/F?", "answer": "True" },
  { "question": "\"There are about 1 to 2 million Islets of Langerhans in a normal human pancreas representing only 1 to 2 per cent of the pancreatic tissue.\" T/F?", "answer": "True" },
  { "question": "\"The two main types of cells in the Islet of Langerhans are called α-cells and β-cells.\" T/F?", "answer": "True" },
  { "question": "\"The α-cells secrete a hormone called glucagon, while the β-cells secrete insulin.\" T/F?", "answer": "True" },
  { "question": "\"Glucagon is a peptide hormone, and plays an important role in maintaining the normal blood glucose levels.\" T/F?", "answer": "True" },
  { "question": "\"Glucagon acts mainly on the liver cells (hepatocytes) and stimulates glycogenolysis resulting in an increased blood sugar (hyperglycemia).\" T/F?", "answer": "True" },
  { "question": "\"In addition, this hormone stimulates the process of gluconeogenesis which also contributes to hyperglycemia.\" T/F?", "answer": "True" },
  { "question": "\"Glucagon reduces the cellular glucose uptake and utilisation.\" T/F?", "answer": "True" },
  { "question": "\"Thus, glucagon is a hyperglycemic hormone.\" T/F?", "answer": "True" },
  { "question": "\"Insulin is a peptide hormone, which plays a major role in the regulation of glucose homeostasis.\" T/F?", "answer": "True" },
  { "question": "\"Insulin acts mainly on hepatocytes and adipocytes (cells of adipose tissue), and enhances cellular glucose uptake and utilisation.\" T/F?", "answer": "True" },
  { "question": "\"As a result, there is a rapid movement of glucose from blood to hepatocytes and adipocytes resulting in decreased blood glucose levels (hypoglycemia).\" T/F?", "answer": "True" },
  { "question": "\"Insulin also stimulates conversion of glucose to glycogen (glycogenesis) in the target cells.\" T/F?", "answer": "True" },
  { "question": "\"The glucose homeostasis in blood is thus maintained jointly by the two – insulin and glucagons.\" T/F?", "answer": "True" },
  { "question": "\"Prolonged hyperglycemia leads to a complex disorder called diabetes mellitus which is associated with loss of glucose through urine and formation of harmful compounds known as ketone bodies.\" T/F?", "answer": "True" },
  { "question": "\"Diabetic patients are successfully treated with insulin therapy.\" T/F?", "answer": "True" },
  { "question": "\"A pair of testis is present in the scrotal sac (outside abdomen) of male individuals.\" T/F?", "answer": "True" },
  { "question": "\"Testis performs dual functions as a primary sex organ as well as an endocrine gland.\" T/F?", "answer": "True" },
  { "question": "\"Testis is composed of seminiferous tubules and stromal or interstitial tissue.\" T/F?", "answer": "True" },
  { "question": "\"The Leydig cells or interstitial cells, which are present in the intertubular spaces produce a group of hormones called androgens mainly testosterone.\" T/F?", "answer": "True" },
  { "question": "\"Androgens regulate the development, maturation and functions of the male accessory sex organs like epididymis, vas deferens, seminal vesicles, prostate gland, urethra etc.\" T/F?", "answer": "True" },
  { "question": "\"These hormones stimulate muscular growth, growth of facial and axillary hair, aggressiveness, low pitch of voice etc.\" T/F?", "answer": "True" },
  { "question": "\"Androgens play a major stimulatory role in the process of spermatogenesis (formation of spermatozoa).\" T/F?", "answer": "True" },
  { "question": "\"Androgens act on the central neural system and influence the male sexual behaviour (libido).\" T/F?", "answer": "True" },
  { "question": "\"These hormones produce anabolic (synthetic) effects on protein and carbohydrate metabolism.\" T/F?", "answer": "True" },
  { "question": "\"Females have a pair of ovaries located in the abdomen.\" T/F?", "answer": "True" },
  { "question": "\"Ovary is the primary female sex organ which produces one ovum during each menstrual cycle.\" T/F?", "answer": "True" },
  { "question": "\"In addition, ovary also produces two groups of steroid hormones called estrogen and progesterone.\" T/F?", "answer": "True" },
  { "question": "\"Ovary is composed of ovarian follicles and stromal tissues.\" T/F?", "answer": "True" },
  { "question": "\"The estrogen is synthesised and secreted mainly by the growing ovarian follicles.\" T/F?", "answer": "True" },
  { "question": "\"After ovulation, the ruptured follicle is converted to a structure called corpus luteum, which secretes mainly progesterone.\" T/F?", "answer": "True" },
  { "question": "\"Estrogens produce wide ranging actions such as stimulation of growth and activities of female secondary sex organs, development of growing ovarian follicles, appearance of female secondary sex characters (e.g., high pitch of voice, etc.) and mammary gland development.\" T/F?", "answer": "True" },
  { "question": "\"Estrogens also regulate female sexual behaviour.\" T/F?", "answer": "True" },
  { "question": "\"Progesterone supports pregnancy.\" T/F?", "answer": "True" },
  { "question": "\"Progesterone also acts on the mammary glands and stimulates the formation of alveoli (sac-like structures which store milk) and milk secretion.\" T/F?", "answer": "True" },
  { "question": "\"Now you know about the endocrine glands and their hormones.\" T/F?", "answer": "True" },
  { "question": "\"However, as mentioned earlier, hormones are also secreted by some tissues which are not endocrine glands.\" T/F?", "answer": "True" },
  { "question": "\"For example, the atrial wall of our heart secretes a very important peptide hormone called atrial natriuretic factor (ANF), which decreases blood pressure.\" T/F?", "answer": "True" },
  { "question": "\"When blood pressure is increased, ANF is secreted which causes dilation of the blood vessels.\" T/F?", "answer": "True" },
  { "question": "\"This reduces the blood pressure.\" T/F?", "answer": "True" },
  { "question": "\"The juxtaglomerular cells of kidney produce a peptide hormone called erythropoietin which stimulates erythropoiesis (formation of RBC).\" T/F?", "answer": "True" },
  { "question": "\"Endocrine cells present in different parts of the gastro-intestinal tract secrete four major peptide hormones, namely gastrin, secretin, cholecystokinin (CCK) and gastric inhibitory peptide (GIP).\" T/F?", "answer": "True" },
  { "question": "\"Gastrin acts on the gastric glands and stimulates the secretion of hydrochloric acid and pepsinogen.\" T/F?", "answer": "True" },
  { "question": "\"Secretin acts on the exocrine pancreas and stimulates secretion of water and bicarbonate ions.\" T/F?", "answer": "True" },
  { "question": "\"CCK acts on both pancreas and gall bladder and stimulates the secretion of pancreatic enzymes and bile juice, respectively.\" T/F?", "answer": "True" },
  { "question": "\"GIP inhibits gastric secretion and motility.\" T/F?", "answer": "True" },
  { "question": "\"Several other non-endocrine tissues secrete hormones called growth factors.\" T/F?", "answer": "True" },
  { "question": "\"These factors are essential for the normal growth of tissues and their repairing/regeneration.\" T/F?", "answer": "True" },
  { "question": "\"Hormones produce their effects on target tissues by binding to specific proteins called hormone receptors located in the target tissues only.\" T/F?", "answer": "True" },
  { "question": "\"Hormone receptors present on the cell membrane of the target cells are called membrane-bound receptors and the receptors present inside the target cell are called intracellular receptors, mostly nuclear receptors (present in the nucleus).\" T/F?", "answer": "True" },
  { "question": "\"Binding of a hormone to its receptor leads to the formation of a hormone-receptor complex.\" T/F?", "answer": "True" },
  { "question": "\"Each receptor is specific to one hormone only and hence receptors are specific.\" T/F?", "answer": "True" },
  { "question": "\"Hormone-Receptor complex formation leads to certain biochemical changes in the target tissue.\" T/F?", "answer": "True" },
  { "question": "\"Target tissue metabolism and hence physiological functions are regulated by hormones.\" T/F?", "answer": "True" },
  { "question": "\"On the basis of their chemical nature, hormones can be divided into groups : (i) peptide, polypeptide, protein hormones (e.g., insulin, glucagon, pituitary hormones, hypothalamic hormones, etc.) (ii) steroids (e.g., cortisol, testosterone, estradiol and progesterone) (iii) iodothyronines (thyroid hormones) (iv) amino-acid derivatives (e.g., epinephrine).\" T/F?", "answer": "True" },
  { "question": "\"Hormones which interact with membrane-bound receptors normally do not enter the target cell, but generate second messengers (e.g., cyclic AMP, IP3, Ca++ etc) which in turn regulate cellular metabolism.\" T/F?", "answer": "True" },
  { "question": "\"Hormones which interact with intracellular receptors (e.g., steroid hormones, iodothyronines, etc.) mostly regulate gene expression or chromosome function by the interaction of hormone-receptor complex with the genome.\" T/F?", "answer": "True" },
  { "question": "\"Cumulative biochemical actions result in physiological and developmental effects.\" T/F?", "answer": "True" },
  { "question": "\"There are special chemicals which act as hormones and provide chemical coordination, integration and regulation in the human body.\" T/F?", "answer": "True" },
  { "question": "\"These hormones regulate metabolism, growth and development of our organs, the endocrine glands or certain cells.\" T/F?", "answer": "True" },
  { "question": "\"The endocrine system is composed of hypothalamus, pituitary and pineal, thyroid, adrenal, pancreas, parathyroid, thymus and gonads (testis and ovary).\" T/F?", "answer": "True" },
  { "question": "\"In addition to these, some other organs, e.g., gastrointestinal tract, kidney, heart etc., also produce hormones.\" T/F?", "answer": "True" },
  { "question": "\"The pituitary gland is divided into three major parts, which are called as pars distalis, pars intermedia and pars nervosa.\" T/F?", "answer": "True" },
  { "question": "\"Pars distalis produces six trophic hormones.\" T/F?", "answer": "True" },
  { "question": "\"Pars intermedia secretes only one hormone, while pars nervosa (neurohypophysis) secretes two hormones.\" T/F?", "answer": "True" },
  { "question": "\"The pituitary hormones regulate the growth and development of somatic tissues and activities of peripheral endocrine glands.\" T/F?", "answer": "True" },
  { "question": "\"Pineal gland secretes melatonin, which plays a very important role in the regulation of 24-hour (diurnal) rhythms of our body (e.g., rhythms of sleep and state of being awake, body temperature, etc.).\" T/F?", "answer": "True" },
  { "question": "\"The thyroid gland hormones play an important role in the regulation of the basal metabolic rate, development and maturation of the central neural system, erythropoiesis, metabolism of carbohydrates, proteins and fats, menstrual cycle.\" T/F?", "answer": "True" },
  { "question": "\"Another thyroid hormone, i.e., thyrocalcitonin regulates calcium levels in our blood by decreasing it.\" T/F?", "answer": "True" },
  { "question": "\"The parathyroid glands secrete parathyroid hormone (PTH) which increases the blood Ca2+ levels and plays a major role in calcium homeostasis.\" T/F?", "answer": "True" },
  { "question": "\"The thymus gland secretes thymosins which play a major role in the differentiation of T-lymphocytes, which provide cell-mediated immunity.\" T/F?", "answer": "True" },
  { "question": "\"In addition, thymosins also increase the production of antibodies to provide humoral immunity.\" T/F?", "answer": "True" },
  { "question": "\"The adrenal gland is composed of the centrally located adrenal medulla and the outer adrenal cortex.\" T/F?", "answer": "True" },
  { "question": "\"The adrenal medulla secretes epinephrine and norepinephrine.\" T/F?", "answer": "True" },
  { "question": "\"These hormones increase alertness, pupilary dilation, piloerection, sweating, heart beat, strength of heart contraction, rate of respiration, glycogenolysis, lipolysis, proteolysis.\" T/F?", "answer": "True" },
  { "question": "\"The adrenal cortex secretes glucocorticoids and mineralocorticoids.\" T/F?", "answer": "True" },
  { "question": "\"Glucocorticoids stimulate gluconeogenesis, lipolysis, proteolysis, erythropoiesis, cardio-vascular system, blood pressure, and glomerular filtration rate and inhibit inflammatory reactions by suppressing the immune response.\" T/F?", "answer": "True" },
  { "question": "\"Mineralocorticoids regulate water and electrolyte contents of the body.\" T/F?", "answer": "True" },
  { "question": "\"The endocrine pancreas secretes glucagon and insulin.\" T/F?", "answer": "True" },
  { "question": "\"Glucagon stimulates glycogenolysis and gluconeogenesis resulting in hyperglycemia.\" T/F?", "answer": "True" },
  { "question": "\"Insulin stimulates cellular glucose uptake and utilisation, and glycogenesis resulting in hypoglycemia.\" T/F?", "answer": "True" },
  { "question": "\"Insulin deficiency and/or insulin resistance result in a disease called diabetes mellitus.\" T/F?", "answer": "True" },
  { "question": "\"The testis secretes androgens, which stimulate the development, maturation and functions of the male accessory sex organs, appearance of the male secondary sex characters, spermatogenesis, male sexual behaviour, anabolic pathways and erythropoiesis.\" T/F?", "answer": "True" },
  { "question": "\"The ovary secretes estrogen and progesterone.\" T/F?", "answer": "True" },
  { "question": "\"Estrogen stimulates growth and development of female accessory sex organs and secondary sex characters.\" T/F?", "answer": "True" },
  { "question": "\"Progesterone plays a major role in the maintenance of pregnancy as well as in mammary gland development and lactation.\" T/F?", "answer": "True" },
  { "question": "\"The atrial wall of the heart produces atrial natriuretic factor which decreases the blood pressure.\" T/F?", "answer": "True" },
  { "question": "\"Kidney produces erythropoietin which stimulates erythropoiesis.\" T/F?", "answer": "True" },
  { "question": "\"The gastrointestinal tract secretes gastrin, secretin, cholecystokinin and gastric inhibitory peptide.\" T/F?", "answer": "True" },
  { "question": "\"These hormones regulate the secretion of digestive juices and help in digestion.\" T/F?", "answer": "True" },
  { "question": "\"Define the following: (a) Exocrine gland (b) Endocrine gland (c) Hormone\" T/F?", "answer": "True, exercise question" },
  { "question": "\"Diagrammatically indicate the location of the various endocrine glands in our body.\" T/F?", "answer": "True, exercise question" },
  { "question": "\"List the hormones secreted by the following: (a) Hypothalamus (b) Pituitary (c) Thyroid (d) Parathyroid (e) Adrenal (f) Pancreas (g) Testis (h) Ovary (i) Thymus (j) Atrium (k) Kidney (l) G-I Tract\" T/F?", "answer": "True, exercise question" },
  { "question": "\"Fill in the blanks: Hormones Target gland (a) Hypothalamic hormones __________________ (b) Thyrotrophin (TSH) __________________ (c) Corticotrophin (ACTH) __________________ (d) Gonadotrophins (LH, FSH) __________________ (e) Melanotrophin (MSH) __________________\" T/F?", "answer": "True, exercise question" },
  { "question": "\"Write short notes on the functions of the following hormones: (a) Parathyroid hormone (PTH) (b) Thyroid hormones (c) Thymosins (d) Androgens (e) Estrogens (f) Insulin and Glucagon\" T/F?", "answer": "True, exercise question" },
  { "question": "\"Give example(s) of: (a) Hyperglycemic hormone and hypoglycemic hormone (b) Hypercalcemic hormone (c) Gonadotrophic hormones (d) Progestational hormone (e) Blood pressure lowering hormone (f) Androgens and estrogens\" T/F?", "answer": "True, exercise question" },
  { "question": "\"Which hormonal deficiency is responsible for the following: (a) Diabetes mellitus (b) Goitre (c) Cretinism\" T/F?", "answer": "True, exercise question" },
  { "question": "\"Briefly mention the mechanism of action of FSH.\" T/F?", "answer": "True, exercise question" },
  { "question": "\"Match the following: Column I Column II (a) T4 (i) Hypothalamus (b) PTH (ii) Thyroid (c) GnRH (iii) Pituitary (d) LH (iv) Parathyroid\" T/F?", "answer": "True, exercise question" }
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
