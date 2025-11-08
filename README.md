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
    <button class="chapter-btn" onclick="startChapter('Chemical coordination')">Chemical coordination</button>
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
      
  { question: "Neural system provides", answer: "Point-to-point coordination" },
  { question: "Neural coordination is", answer: "Rapid but short-lived" },
  { question: "Nerve fibres do not innervate", answer: "All cells" },
  { question: "Cellular functions need", answer: "Continuous regulation" },
  { question: "Special coordination by", answer: "Hormones" },
  { question: "Neural + endocrine regulate", answer: "Physiological functions" },
  { question: "Endocrine glands are", answer: "Ductless" },
  { question: "Endocrine secretions called", answer: "Hormones" },
  { question: "Classical hormone definition", answer: "Blood-transported to target" },
  { question: "Modern hormone definition", answer: "Non-nutrient messengers" },
  { question: "Hormones produced in", answer: "Trace amounts" },
  { question: "New definition covers", answer: "New molecules" },
  { question: "Invertebrate endocrine system", answer: "Simple, few hormones" },
  { question: "Vertebrate endocrine system", answer: "Complex, many hormones" },
  { question: "Human endocrine system described", answer: "In chapter" },
  { question: "Endocrine system constitutes", answer: "Glands + diffused tissues" },
  { question: "Organized endocrine glands", answer: "Pituitary, pineal, thyroid, etc." },
  { question: "Other hormone-producing organs", answer: "GI tract, liver, kidney, heart" },
  { question: "Hypothalamus is basal part of", answer: "Diencephalon" },
  { question: "Hypothalamus regulates", answer: "Wide body functions" },
  { question: "Hypothalamic neurosecretory cells", answer: "Nuclei" },
  { question: "Hypothalamic hormones regulate", answer: "Pituitary synthesis/secretion" },
  { question: "Hypothalamic hormone types", answer: "Releasing + inhibiting" },
  { question: "GnRH stimulates", answer: "Gonadotrophins" },
  { question: "Somatostatin inhibits", answer: "GH release" },
  { question: "Hypothalamic hormones travel via", answer: "Axons to nerve endings" },
  { question: "To anterior pituitary via", answer: "Portal circulation" },
  { question: "Posterior pituitary regulation", answer: "Direct neural" },
  { question: "Pituitary location", answer: "Sella turcica" },
  { question: "Pituitary attached to hypothalamus by", answer: "Stalk" },
  { question: "Pituitary divisions", answer: "Adenohypophysis + neurohypophysis" },
  { question: "Adenohypophysis portions", answer: "Pars distalis + intermedia" },
  { question: "Anterior pituitary hormones", answer: "GH, PRL, TSH, ACTH, LH, FSH" },
  { question: "Pars intermedia hormone", answer: "MSH" },
  { question: "In humans, pars intermedia", answer: "Merged with distalis" },
  { question: "Posterior pituitary hormones", answer: "Oxytocin + vasopressin" },
  { question: "Oxytocin + vasopressin synthesized in", answer: "Hypothalamus" },
  { question: "GH over-secretion in body", answer: "Gigantism" },
  { question: "GH low secretion", answer: "Pituitary dwarfism" },
  { question: "GH excess in adults", answer: "Acromegaly" },
  { question: "Acromegaly causes", answer: "Facial disfigurement" },
  { question: "Acromegaly diagnosis", answer: "Hard in early stages" },
  { question: "PRL regulates", answer: "Mammary growth + milk" },
  { question: "TSH stimulates", answer: "Thyroid hormones" },
  { question: "ACTH stimulates", answer: "Glucocorticoids" },
  { question: "LH + FSH are", answer: "Gonadotrophins" },
  { question: "LH in males stimulates", answer: "Androgens from testis" },
  { question: "FSH in males regulates", answer: "Spermatogenesis" },
  { question: "LH in females induces", answer: "Ovulation" },
  { question: "LH maintains in females", answer: "Corpus luteum" },
  { question: "FSH in females stimulates", answer: "Ovarian follicles" },
  { question: "MSH regulates", answer: "Skin pigmentation" },
  { question: "MSH acts on", answer: "Melanocytes" },
  { question: "Oxytocin stimulates", answer: "Smooth muscle contraction" },
  { question: "Oxytocin in females", answer: "Uterus contraction + milk ejection" },
  { question: "Vasopressin acts on", answer: "Kidney distal tubules" },
  { question: "Vasopressin stimulates", answer: "Water reabsorption" },
  { question: "Vasopressin reduces", answer: "Diuresis" },
  { question: "Vasopressin also called", answer: "ADH" },
  { question: "ADH impairment causes", answer: "Diabetes Insipidus" },
  { question: "Pineal gland location", answer: "Dorsal forebrain" },
  { question: "Pineal hormone", answer: "Melatonin" },
  { question: "Melatonin regulates", answer: "24-hour rhythm" },
  { question: "Melatonin maintains", answer: "Sleep-wake, temperature" },
  { question: "Melatonin influences", answer: "Metabolism, pigmentation, menstrual cycle" },
  { question: "Thyroid lobes location", answer: "Either side of trachea" },
  { question: "Thyroid lobes connected by", answer: "Isthmus" },
  { question: "Thyroid composed of", answer: "Follicles + stromal tissue" },
  { question: "Thyroid follicular cells synthesize", answer: "T4 + T3" },
  { question: "Iodine essential for", answer: "Thyroid hormone synthesis" },
  { question: "Iodine deficiency causes", answer: "Hypothyroidism + goitre" },
  { question: "Hypothyroidism in pregnancy", answer: "Cretinism" },
  { question: "Cretinism features", answer: "Stunted growth, mental retardation" },
  { question: "Hypothyroidism in adult women", answer: "Irregular menstrual cycle" },
  { question: "Hyperthyroidism causes", answer: "Thyroid cancer/nodules" },
  { question: "Exophthalmic goitre is", answer: "Hyperthyroidism" },
  { question: "Graves’ disease features", answer: "Eye protrusion, high BMR, weight loss" },
  { question: "Thyroid hormones regulate", answer: "Basal metabolic rate" },
  { question: "Thyroid hormones support", answer: "RBC formation" },
  { question: "Thyroid hormones control metabolism of", answer: "Carbs, proteins, fats" },
  { question: "Thyroid hormones influence", answer: "Water + electrolyte balance" },
  { question: "Thyroid also secretes", answer: "TCT" },
  { question: "TCT regulates", answer: "Blood calcium" },
  { question: "Parathyroid glands number", answer: "4" },
  { question: "Parathyroid location", answer: "Back of thyroid" },
  { question: "PTH secretion regulated by", answer: "Ca²⁺ levels" },
  { question: "PTH increases", answer: "Blood Ca²⁺" },
  { question: "PTH stimulates bone", answer: "Resorption" },
  { question: "PTH stimulates renal", answer: "Ca²⁺ reabsorption" },
  { question: "PTH increases gut", answer: "Ca²⁺ absorption" },
  { question: "PTH is", answer: "Hypercalcemic hormone" },
  { question: "PTH + TCT role", answer: "Calcium balance" },
  { question: "Thymus structure", answer: "Lobular" },
  { question: "Thymus location", answer: "Between lungs, behind sternum" },
  { question: "Thymus role in", answer: "Immune system development" },
  { question: "Thymus secretes", answer: "Thymosins" },
  { question: "Thymosins role in", answer: "T-lymphocyte differentiation" },
  { question: "Thymosins provide", answer: "Cell-mediated immunity" },
  { question: "Thymosins promote", answer: "Antibody production" },
  { question: "Thymus in old age", answer: "Degenerates" },
  { question: "Thymus degeneration results in", answer: "Weak immunity" },
  { question: "Adrenal glands location", answer: "Above each kidney" },
  { question: "Adrenal tissues", answer: "Medulla (central) + cortex (outer)" },
  { question: "Adrenal cortex underproduction causes", answer: "Addison’s disease" },
  { question: "Addison’s symptoms", answer: "Weakness, fatigue" },
  { question: "Adrenal medulla hormones", answer: "Adrenaline, noradrenaline" },
  { question: "Adrenaline + noradrenaline are", answer: "Catecholamines" },
  { question: "Catecholamines secreted in", answer: "Stress/emergency" },
  { question: "Fight or flight hormones", answer: "Adrenaline, noradrenaline" },
  { question: "Catecholamines increase", answer: "Alertness, pupil dilation" },
  { question: "Catecholamines cause", answer: "Piloerection, sweating" },
  { question: "Catecholamines increase heart", answer: "Beat + contraction strength" },
  { question: "Catecholamines increase", answer: "Respiration rate" },
  { question: "Catecholamines stimulate", answer: "Glycogen breakdown" },
  { question: "Catecholamines increase blood", answer: "Glucose" },
  { question: "Catecholamines also stimulate breakdown of", answer: "Lipids + proteins" },
  { question: "Adrenal cortex layers", answer: "3: Glomerulosa, fasciculata, reticularis" },
  { question: "Adrenal cortex hormones", answer: "Corticoids" },
  { question: "Glucocorticoids involved in", answer: "Carb metabolism" },
  { question: "Main glucocorticoid", answer: "Cortisol" },
  { question: "Mineralocorticoids regulate", answer: "Water + electrolytes" },
  { question: "Main mineralocorticoid", answer: "Aldosterone" },
  { question: "Glucocorticoids stimulate", answer: "Gluconeogenesis, lipolysis, proteolysis" },
  { question: "Glucocorticoids inhibit", answer: "Amino acid uptake" },
  { question: "Cortisol maintains", answer: "CV system + kidney function" },
  { question: "Cortisol produces", answer: "Anti-inflammatory reactions" },
  { question: "Cortisol suppresses", answer: "Immune response" },
  { question: "Cortisol stimulates", answer: "RBC production" },
  { question: "Aldosterone acts on", answer: "Renal tubules" },
  { question: "Aldosterone reabsorbs", answer: "Na⁺ + water" },
  { question: "Aldosterone excretes", answer: "K⁺ + phosphate" },
  { question: "Aldosterone maintains", answer: "Electrolytes, fluid volume, BP" },
  { question: "Adrenal cortex secretes small", answer: "Androgenic steroids" },
  { question: "Androgenic steroids role", answer: "Axial/pubic/facial hair growth" },
  { question: "Pancreas acts as", answer: "Exocrine + endocrine" },
  { question: "Endocrine pancreas", answer: "Islets of Langerhans" },
  { question: "Islets number", answer: "1-2 million" },
  { question: "Islets % of pancreas", answer: "1-2%" },
  { question: "Islet cell types", answer: "α + β" },
  { question: "α-cells secrete", answer: "Glucagon" },
  { question: "β-cells secrete", answer: "Insulin" },
  { question: "Glucagon maintains", answer: "Blood glucose" },
  { question: "Glucagon acts on", answer: "Hepatocytes" },
  { question: "Glucagon stimulates", answer: "Glycogenolysis" },
  { question: "Glucagon causes", answer: "Hyperglycemia" },
  { question: "Glucagon stimulates", answer: "Gluconeogenesis" },
  { question: "Glucagon reduces", answer: "Glucose uptake" },
  { question: "Glucagon is", answer: "Hyperglycemic hormone" },
  { question: "Insulin regulates", answer: "Glucose homeostasis" },
  { question: "Insulin acts on", answer: "Hepatocytes + adipocytes" },
  { question: "Insulin enhances", answer: "Glucose uptake" },
  { question: "Insulin causes", answer: "Hypoglycemia" },
  { question: "Insulin stimulates", answer: "Glycogenesis" },
  { question: "Glucose homeostasis by", answer: "Insulin + glucagon" },
  { question: "Prolonged hyperglycemia causes", answer: "Diabetes mellitus" },
  { question: "Diabetes mellitus associated with", answer: "Glucosuria + ketonemia" },
  { question: "Diabetes treatment", answer: "Insulin therapy" },
  { question: "Testis location", answer: "Scrotal sac" },
  { question: "Testis functions", answer: "Sex organ + endocrine" },
  { question: "Testis composed of", answer: "Seminiferous tubules + interstitial tissue" },
  { question: "Testis hormone-producing cells", answer: "Leydig cells" },
  { question: "Leydig cells produce", answer: "Androgens (testosterone)" },
  { question: "Androgens regulate male", answer: "Accessory sex organs" },
  { question: "Androgens stimulate", answer: "Muscular growth" },
  { question: "Androgens cause", answer: "Facial/axillary hair, low voice" },
  { question: "Androgens role in", answer: "Spermatogenesis" },
  { question: "Androgens influence", answer: "Male libido" },
  { question: "Androgens produce", answer: "Anabolic effects" },
  { question: "Ovary location", answer: "Abdomen" },
  { question: "Ovary produces per cycle", answer: "One ovum" },
  { question: "Ovary hormones", answer: "Estrogen + progesterone" },
  { question: "Ovary composed of", answer: "Follicles + stromal tissue" },
  { question: "Estrogen from", answer: "Growing follicles" },
  { question: "Progesterone from", answer: "Corpus luteum" },
  { question: "Estrogens stimulate", answer: "Female secondary organs" },
  { question: "Estrogens develop", answer: "Ovarian follicles" },
  { question: "Estrogens cause", answer: "Female secondary characters" },
  { question: "Estrogens regulate", answer: "Female behavior" },
  { question: "Progesterone supports", answer: "Pregnancy" },
  { question: "Progesterone stimulates", answer: "Mammary alveoli + milk" },
  { question: "Heart hormone", answer: "ANF" },
  { question: "ANF from", answer: "Atrial wall" },
  { question: "ANF decreases", answer: "Blood pressure" },
  { question: "ANF causes", answer: "Vessel dilation" },
  { question: "Kidney hormone", answer: "Erythropoietin" },
  { question: "Erythropoietin from", answer: "Juxtaglomerular cells" },
  { question: "Erythropoietin stimulates", answer: "Erythropoiesis" },
  { question: "GI tract major hormones", answer: "Gastrin, secretin, CCK, GIP" },
  { question: "Gastrin acts on", answer: "Gastric glands" },
  { question: "Gastrin stimulates", answer: "HCl + pepsinogen" },
  { question: "Secretin acts on", answer: "Exocrine pancreas" },
  { question: "Secretin stimulates", answer: "Water + HCO₃⁻" },
  { question: "CCK acts on", answer: "Pancreas + gall bladder" },
  { question: "CCK stimulates", answer: "Enzymes + bile" },
  { question: "GIP inhibits", answer: "Gastric secretion/motility" },
  { question: "Non-endocrine hormones called", answer: "Growth factors" },
  { question: "Growth factors essential for", answer: "Tissue growth/repair" },
  { question: "Hormones bind to", answer: "Specific receptors" },
  { question: "Receptors location", answer: "Target tissues only" },
  { question: "Membrane-bound receptors for", answer: "Peptide hormones" },
  { question: "Intracellular receptors are", answer: "Mostly nuclear" },
  { question: "Hormone-receptor forms", answer: "Complex" },
  { question: "Receptors are", answer: "Hormone-specific" },
  { question: "Complex leads to", answer: "Biochemical changes" },
  { question: "Hormone chemical groups", answer: "4" },
  { question: "Peptide hormones examples", answer: "Insulin, glucagon, pituitary" },
  { question: "Steroid hormones examples", answer: "Cortisol, testosterone" },
  { question: "Iodothyronines", answer: "Thyroid hormones" },
  { question: "Amino-acid derivatives example", answer: "Epinephrine" },
  { question: "Peptide hormones generate", answer: "Second messengers" },
  { question: "Second messengers examples", answer: "cAMP, IP3, Ca²⁺" },
  { question: "Steroid hormones regulate", answer: "Gene expression" },
  { question: "Cumulative actions result in", answer: "Physiological effects" },
  { question: "Special chemicals act as", answer: "Hormones" },
  { question: "Hormones regulate", answer: "Metabolism, growth" },
  { question: "Endocrine system composed of", answer: "Hypothalamus to gonads" },
  { question: "Pituitary divided into", answer: "3 parts" },
  { question: "Pars distalis produces", answer: "6 trophic hormones" },
  { question: "Pars intermedia secretes", answer: "1 hormone" },
  { question: "Pars nervosa secretes", answer: "2 hormones" },
  { question: "Pituitary regulates", answer: "Somatic tissues + peripheral glands" },
  { question: "Melatonin regulates", answer: "Diurnal rhythms" },
  { question: "Thyroid hormones role in", answer: "BMR, CNS maturation, erythropoiesis" },
  { question: "TCT decreases", answer: "Blood Ca²⁺" },
  { question: "PTH increases", answer: "Blood Ca²⁺" },
  { question: "Thymosins differentiate", answer: "T-lymphocytes" },
  { question: "Adrenal medulla secretes", answer: "Epinephrine, norepinephrine" },
  { question: "Adrenal cortex secretes", answer: "Glucocorticoids, mineralocorticoids" },
  { question: "Glucocorticoids stimulate", answer: "Gluconeogenesis, lipolysis" },
  { question: "Mineralocorticoids regulate", answer: "Water + electrolytes" },
  { question: "Glucagon results in", answer: "Hyperglycemia" },
  { question: "Insulin results in", answer: "Hypoglycemia" },
  { question: "Diabetes mellitus from", answer: "Insulin deficiency/resistance" },
  { question: "Androgens stimulate", answer: "Male accessory organs" },
  { question: "Estrogen stimulates", answer: "Female secondary characters" },
  { question: "Progesterone in", answer: "Pregnancy maintenance" },
  { question: "ANF from", answer: "Heart atrium" },
  { question: "Erythropoietin from", answer: "Kidney" },
  { question: "GI hormones regulate", answer: "Digestive juices" },
  { question: "Exocrine gland", answer: "Has ducts" },
  { question: "Endocrine gland", answer: "Ductless" },
  { question: "Hormone", answer: "Chemical messenger" },
  { question: "Hypothalamic hormones target", answer: "Pituitary" },
  { question: "TSH targets", answer: "Thyroid" },
  { question: "ACTH targets", answer: "Adrenal cortex" },
  { question: "LH/FSH target", answer: "Gonads" },
  { question: "MSH targets", answer: "Melanocytes" },
  { question: "PTH function", answer: "Increases Ca²⁺" },
  { question: "Thyroid hormones", answer: "Regulate BMR" },
  { question: "Thymosins", answer: "T-cell immunity" },
  { question: "Androgens", answer: "Male characters" },
  { question: "Estrogens", answer: "Female characters" },
  { question: "Insulin + glucagon", answer: "Glucose homeostasis" },
  { question: "Hyperglycemic", answer: "Glucagon" },
  { question: "Hypoglycemic", answer: "Insulin" },
  { question: "Hypercalcemic", answer: "PTH" },
  { question: "Gonadotrophic", answer: "LH, FSH" },
  { question: "Progestational", answer: "Progesterone" },
  { question: "BP lowering", answer: "ANF" },
  { question: "Androgens", answer: "Testosterone" },
  { question: "Estrogens", answer: "Estradiol" },
  { question: "Diabetes mellitus deficiency", answer: "Insulin" },
  { question: "Goitre deficiency", answer: "Iodine" },
  { question: "Cretinism deficiency", answer: "Thyroid hormones" },
  { question: "FSH mechanism", answer: "Binds membrane receptor" }
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
