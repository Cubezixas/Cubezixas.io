# Cubezixas.io
<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>VAS Batch 4 Reviewer</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    min-height: 100vh;
    background: #0d0d14;
    font-family: Georgia, 'Times New Roman', serif;
    color: #e8e0d0;
    overscroll-behavior: none;
  }

/* HEADER */
#header {
background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
border-bottom: 1px solid #2a2a4a;
padding: 18px 16px 14px;
position: sticky;
top: 0;
z-index: 100;
}
.header-top {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 12px;
}
.header-label {
font-size: 10px;
letter-spacing: 0.3em;
color: #7b8cde;
text-transform: uppercase;
margin-bottom: 2px;
}
.header-title { font-size: 20px; font-weight: bold; color: #f0e8d8; }
.header-badge {
background: #1e2a5a;
border: 1px solid #3a4a8a;
border-radius: 12px;
padding: 6px 14px;
text-align: center;
}
.badge-num { font-size: 18px; font-weight: bold; color: #7b8cde; }
.badge-lbl { font-size: 9px; letter-spacing: 0.1em; color: #aab8f5; }

/* TABS */
.tabs { display: flex; gap: 6px; margin-bottom: 10px; }
.tab {
flex: 1; padding: 7px 0; border: none; border-radius: 8px;
font-size: 13px; font-family: inherit; cursor: pointer;
background: #1a1a2e; color: #7888cc;
transition: all 0.2s; letter-spacing: 0.05em;
}
.tab.active { background: #3a4a9a; color: #fff; font-weight: bold; }

/* FILTERS */
.filters { display: flex; gap: 6px; }
.filter-btn {
flex: 1; padding: 5px 0;
border: 1px solid #2a2a4a; border-radius: 6px;
font-size: 11px; font-family: inherit; cursor: pointer;
background: transparent; color: #556080;
letter-spacing: 0.05em; transition: all 0.2s;
}
.filter-btn.active { background: #252545; border-color: #5a6aaa; color: #aab8f5; }

/* MAIN */
#main { padding: 20px 16px; max-width: 480px; margin: 0 auto; }

/* PROGRESS BAR */
.prog-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; font-size: 12px; }
.prog-bar { height: 3px; background: #1a1a2e; border-radius: 2px; margin-bottom: 18px; overflow: hidden; }
.prog-fill { height: 100%; border-radius: 2px; transition: width 0.3s; }
.prog-fill.blue { background: linear-gradient(90deg, #3a4a9a, #7b8cde); }
.prog-fill.green { background: linear-gradient(90deg, #3a9a4a, #88dd88); }

/* CARD */
.card {
border-radius: 20px; padding: 36px 24px;
min-height: 210px; cursor: pointer;
display: flex; flex-direction: column;
justify-content: center; align-items: center;
text-align: center; transition: all 0.25s;
margin-bottom: 18px;
}
.card.front {
background: linear-gradient(135deg, #12122a 0%, #1a1a3a 100%);
border: 1px solid #2a2a4a;
box-shadow: 0 4px 16px rgba(0,0,0,0.4);
}
.card.back {
background: linear-gradient(135deg, #1e2a5a 0%, #252545 100%);
border: 1px solid #4a5a9a;
box-shadow: 0 8px 32px rgba(90,110,200,0.2);
}
.card-word { font-size: 28px; font-weight: bold; color: #f0e8d8; margin-bottom: 10px; line-height: 1.2; }
.card-ipa { font-size: 16px; color: #7b8cde; font-style: italic; margin-bottom: 14px; }
.card-hint { font-size: 11px; color: #445060; letter-spacing: 0.15em; text-transform: uppercase; }
.card-word-sm { font-size: 13px; color: #7b8cde; margin-bottom: 10px; letter-spacing: 0.1em; text-transform: uppercase; }
.card-meaning { font-size: 17px; color: #d8d0e8; line-height: 1.6; margin-bottom: 8px; }
.card-ipa-sm { font-size: 12px; color: #556080; font-style: italic; }

/* KNOW BUTTONS */
.know-row { display: flex; gap: 10px; margin-bottom: 14px; }
.know-btn {
flex: 1; padding: 12px 0; border-radius: 12px;
font-size: 14px; font-family: inherit; font-weight: bold; cursor: pointer;
transition: opacity 0.2s;
}
.know-btn.no  { border: 1px solid #5a2a2a; background: #2a1212; color: #ff8888; }
.know-btn.yes { border: 1px solid #2a5a2a; background: #122a12; color: #88cc88; }

/* NAV ROW */
.nav-row { display: flex; gap: 10px; }
.nav-btn {
padding: 12px 0; border: 1px solid #2a2a4a; border-radius: 12px;
background: #12121a; cursor: pointer; font-size: 18px;
color: #7888cc; transition: background 0.2s;
}
.nav-btn:active { background: #1e1e3a; }
.nav-btn.wide { flex: 1; }
.nav-btn.shuffle {
padding: 12px 18px; font-size: 11px; font-family: inherit;
color: #556080; letter-spacing: 0.1em; text-transform: uppercase;
}

/* QUIZ */
.quiz-question {
background: linear-gradient(135deg, #12122a 0%, #1a1a3a 100%);
border: 1px solid #2a2a4a; border-radius: 20px;
padding: 28px 22px; margin-bottom: 18px; text-align: center;
}
.quiz-q-label { font-size: 10px; color: #556080; letter-spacing: 0.2em; text-transform: uppercase; margin-bottom: 10px; }
.quiz-q-text { font-size: 17px; color: #d8d0e8; line-height: 1.6; }
.quiz-choices { display: flex; flex-direction: column; gap: 10px; margin-bottom: 18px; }
.choice-btn {
padding: 14px 18px; border-radius: 12px;
font-size: 16px; font-family: inherit; font-weight: bold;
cursor: pointer; text-align: left;
display: flex; justify-content: space-between; align-items: center;
transition: all 0.2s;
background: #12121a; border: 1px solid #2a2a4a; color: #c0b8d0;
}
.choice-btn.correct { background: #122a12; border-color: #3a7a3a; color: #88cc88; }
.choice-btn.wrong   { background: #2a1212; border-color: #7a3a3a; color: #ff8888; }
.next-btn {
width: 100%; padding: 14px 0; border: 1px solid #3a4a9a; border-radius: 12px;
background: #1e2a5a; color: #aab8f5; font-size: 15px; font-family: inherit;
font-weight: bold; cursor: pointer; letter-spacing: 0.05em;
}

/* BROWSE */
#browse-search {
width: 100%; padding: 12px 16px;
background: #12121a; border: 1px solid #2a2a4a; border-radius: 12px;
color: #e8e0d0; font-size: 14px; font-family: inherit;
margin-bottom: 14px; outline: none;
}
.browse-count { font-size: 11px; color: #445060; margin-bottom: 12px; letter-spacing: 0.1em; }
.browse-list { display: flex; flex-direction: column; gap: 8px; }
.browse-item {
background: #12121a; border: 1px solid #1e1e3a;
border-radius: 12px; padding: 13px 15px;
}
.browse-item-top { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 3px; }
.browse-word { font-size: 17px; font-weight: bold; color: #e8e0d0; }
.browse-tag {
font-size: 9px; letter-spacing: 0.15em; text-transform: uppercase;
padding: 2px 8px; border-radius: 10px;
}
.browse-tag.word  { background: #1a2a4a; color: #88bbff; }
.browse-tag.idiom { background: #2a1a4a; color: #bb88ff; }
.browse-ipa   { font-size: 13px; color: #6a78cc; font-style: italic; margin-bottom: 3px; }
.browse-def   { font-size: 14px; color: #9090b0; line-height: 1.5; }

/* TYPE TAG on card */
.type-tag {
font-size: 9px; letter-spacing: 0.1em; text-transform: uppercase;
padding: 3px 10px; border-radius: 20px;
}
.type-tag.word  { background: #1a2a4a; color: #88bbff; }
.type-tag.idiom { background: #2a1a4a; color: #bb88ff; }

.known-info { font-size: 12px; color: #7b9e7b; }
.score-info { font-size: 13px; color: #88cc88; }
</style>

</head>
<body>

<div id="header">
  <div class="header-top">
    <div>
      <div class="header-label">VAS Vocabulary</div>
      <div class="header-title">Batch 4 Reviewer</div>
    </div>
    <div class="header-badge">
      <div class="badge-num">100</div>
      <div class="badge-lbl">TERMS</div>
    </div>
  </div>
  <div class="tabs">
    <button class="tab active" onclick="setMode('flashcard')">Flashcard</button>
    <button class="tab" onclick="setMode('quiz')">Quiz</button>
    <button class="tab" onclick="setMode('browse')">Browse</button>
  </div>
  <div class="filters">
    <button class="filter-btn active" onclick="setFilter('all')">All (100)</button>
    <button class="filter-btn" onclick="setFilter('word')">Vocabulary</button>
    <button class="filter-btn" onclick="setFilter('idiom')">Idioms</button>
  </div>
</div>

<div id="main"></div>

<script>
const ALL_WORDS = [
  {id:1,  word:"Wraith",                     ipa:"/reɪθ/",                               meaning:"A ghost or spirit, especially one seen as a pale figure.",                                                           type:"word"},
  {id:2,  word:"Viscount",                   ipa:"/ˈvaɪkaʊnt/",                          meaning:"A British noble rank below earl and above baron.",                                                                    type:"word"},
  {id:3,  word:"Pharaoh",                    ipa:"/ˈfeəroʊ/",                             meaning:"Ancient Egyptian ruler.",                                                                                             type:"word"},
  {id:4,  word:"Minutiae",                   ipa:"/mɪˈnjuːʃi.iː/",                       meaning:"Small and precise details, often overlooked but important.",                                                          type:"word"},
  {id:5,  word:"Desiccated",                 ipa:"/ˈdesɪkeɪtɪd/",                        meaning:"Completely dried out; dehydrated.",                                                                                   type:"word"},
  {id:6,  word:"Acquiesce",                  ipa:"/ˌækwɪˈes/",                           meaning:"To accept something reluctantly but without protest.",                                                                type:"word"},
  {id:7,  word:"Worcestershire",             ipa:"/ˈwʊstərʃər/",                         meaning:"A county in England; also used in Worcestershire sauce.",                                                             type:"word"},
  {id:8,  word:"Sioux",                      ipa:"/suː/",                                meaning:"A group of Native American tribes.",                                                                                  type:"word"},
  {id:9,  word:"Segue",                      ipa:"/ˈseɡweɪ/",                            meaning:"A smooth transition from one topic or section to another.",                                                           type:"word"},
  {id:10, word:"Otorhinolaryngologist",      ipa:"/ˌoʊtoʊˌraɪnoʊˌlærɪŋˈɡɒlədʒɪst/",   meaning:"Doctor specializing in ear, nose, and throat conditions.",                                                            type:"word"},
  {id:11, word:"Hors d'oeuvre",              ipa:"/ɔːr ˈdɜːrv/",                         meaning:"A small appetizer served before a meal.",                                                                             type:"word"},
  {id:12, word:"Gauge",                      ipa:"/ɡeɪdʒ/",                              meaning:"To measure or estimate; also a measuring instrument.",                                                                type:"word"},
  {id:13, word:"Bourgeois",                  ipa:"/ˈbʊrʒwɑː/",                           meaning:"Middle-class, often materialistic values.",                                                                           type:"word"},
  {id:14, word:"Anemone",                    ipa:"/əˈneməni/",                            meaning:"A flowering plant or sea animal related to jellyfish.",                                                               type:"word"},
  {id:15, word:"Rendezvous",                 ipa:"/ˈrɒndeɪvuː/",                         meaning:"A planned meeting at a specific time and place.",                                                                     type:"word"},
  {id:16, word:"Victuals",                   ipa:"/ˈvɪtəlz/",                            meaning:"Food supplies or provisions.",                                                                                        type:"word"},
  {id:17, word:"Isthmus",                    ipa:"/ˈɪsməs/",                             meaning:"A narrow strip of land connecting two larger land areas.",                                                            type:"word"},
  {id:18, word:"Euphemism",                  ipa:"/ˈjuːfəmɪzəm/",                        meaning:"A mild or indirect word used instead of a harsh one.",                                                                type:"word"},
  {id:19, word:"Quay",                       ipa:"/kiː/",                                meaning:"A platform along water for loading/unloading ships.",                                                                 type:"word"},
  {id:20, word:"Chthonic",                   ipa:"/ˈθɒnɪk/",                             meaning:"Relating to the underworld or beneath the earth (mythology).",                                                        type:"word"},
  {id:21, word:"Credulity",                  ipa:"/krɪˈduːlɪti/",                        meaning:"Tendency to believe things too easily.",                                                                              type:"word"},
  {id:22, word:"Attenuate",                  ipa:"/əˈtɛnjueɪt/",                         meaning:"To reduce in force, effect, or value.",                                                                               type:"word"},
  {id:23, word:"Mantle",                     ipa:"/ˈmæntəl/",                            meaning:"A cloak or covering; symbolic role or responsibility.",                                                               type:"word"},
  {id:24, word:"Tapestry",                   ipa:"/ˈtæpɪstri/",                          meaning:"A decorative woven fabric.",                                                                                          type:"word"},
  {id:25, word:"Sepulcher",                  ipa:"/ˈsɛpəlkər/",                          meaning:"A tomb or burial chamber.",                                                                                           type:"word"},
  {id:26, word:"Pedestal",                   ipa:"/ˈpɛdəstəl/",                          meaning:"Base/support for a statue; figurative admiration position.",                                                          type:"word"},
  {id:27, word:"Detritus",                   ipa:"/dɪˈtraɪtəs/",                         meaning:"Waste or debris.",                                                                                                    type:"word"},
  {id:28, word:"Armament",                   ipa:"/ˈɑːrməmənt/",                         meaning:"Weapons and military equipment.",                                                                                     type:"word"},
  {id:29, word:"Marginal",                   ipa:"/ˈmɑːrdʒɪnəl/",                        meaning:"Minor or at the edge.",                                                                                               type:"word"},
  {id:30, word:"Definitive",                 ipa:"/dɪˈfɪnɪtɪv/",                         meaning:"Final and conclusive.",                                                                                               type:"word"},
  {id:31, word:"Capitulation",               ipa:"/kəˌpɪtʃəˈleɪʃən/",                   meaning:"Surrender or giving up resistance.",                                                                                  type:"word"},
  {id:32, word:"Albeit",                     ipa:"/ɔːlˈbiːɪt/",                          meaning:"Although; even though.",                                                                                              type:"word"},
  {id:33, word:"Antagonize",                 ipa:"/ænˈtæɡənaɪz/",                        meaning:"To provoke hostility or anger.",                                                                                      type:"word"},
  {id:34, word:"Elusive",                    ipa:"/ɪˈluːsɪv/",                           meaning:"Hard to find or understand.",                                                                                         type:"word"},
  {id:35, word:"Annotate",                   ipa:"/ˈænəteɪt/",                           meaning:"To add notes to text.",                                                                                               type:"word"},
  {id:36, word:"Penchant",                   ipa:"/ˈpɛntʃənt/",                          meaning:"Strong liking for something.",                                                                                        type:"word"},
  {id:37, word:"Retinue",                    ipa:"/ˈrɛtɪnjuː/",                          meaning:"Group of attendants.",                                                                                                type:"word"},
  {id:38, word:"Reprobate",                  ipa:"/ˈrɛprəbeɪt/",                         meaning:"Morally unprincipled person.",                                                                                        type:"word"},
  {id:39, word:"Sybarite",                   ipa:"/ˈsɪbərʌɪt/",                          meaning:"Person devoted to luxury and pleasure.",                                                                              type:"word"},
  {id:40, word:"Quell",                      ipa:"/kwɛl/",                               meaning:"To suppress or put an end to something.",                                                                             type:"word"},
  {id:41, word:"Frappé",                     ipa:"/fræˈpeɪ/",                            meaning:"A beverage chilled or beaten to a frothy texture; from French 'struck' or 'chilled'.",                              type:"word"},
  {id:42, word:"Chancre",                    ipa:"/ˈʃæŋkər/",                            meaning:"A painless ulcer or sore, especially the initial lesion of syphilis.",                                               type:"word"},
  {id:43, word:"Prerequisite",               ipa:"/ˌpriːˈrɛkwɪzɪt/",                    meaning:"Something required as a prior condition before proceeding.",                                                          type:"word"},
  {id:44, word:"Capstone",                   ipa:"/ˈkæpstoʊn/",                          meaning:"The final, crowning achievement or concluding project integrating accumulated knowledge.",                            type:"word"},
  {id:45, word:"Accreditation",              ipa:"/əˌkrɛdɪˈteɪʃən/",                    meaning:"Official recognition by an authoritative body that standards are met.",                                               type:"word"},
  {id:46, word:"Paradigm",                   ipa:"/ˈpærəˌdaɪm/",                         meaning:"A typical example or model; a framework of ideas shaping understanding or practice.",                                type:"word"},
  {id:47, word:"Genome",                     ipa:"/ˈdʒiːnoʊm/",                          meaning:"The complete set of genetic material in an organism or cell.",                                                        type:"word"},
  {id:48, word:"Algorithm",                  ipa:"/ˈælɡəˌrɪðəm/",                        meaning:"A defined sequence of logical steps used to solve a problem, especially in computing.",                              type:"word"},
  {id:49, word:"Parameter",                  ipa:"/pəˈræmɪtər/",                         meaning:"A measurable factor or variable that defines limits or conditions in a system.",                                      type:"word"},
  {id:50, word:"Criterion",                  ipa:"/kraɪˈtɪəriən/",                       meaning:"A standard, rule, or principle by which something is judged or evaluated.",                                          type:"word"},
  {id:51, word:"Extrapolate",                ipa:"/ɪkˈstræpəˌleɪt/",                     meaning:"To infer unknown values by extending from known data or observations.",                                               type:"word"},
  {id:52, word:"Polymath",                   ipa:"/ˈpɒliˌmæθ/",                          meaning:"A person with extensive knowledge across multiple fields, excelling in both arts and sciences.",                     type:"word"},
  {id:53, word:"Revere",                     ipa:"/rɪˈvɪr/",                             meaning:"To feel deep respect, admiration, or veneration for someone or something.",                                          type:"word"},
  {id:54, word:"Vindication",                ipa:"/ˌvɪndɪˈkeɪʃən/",                      meaning:"The act of clearing someone of blame; proof that justifies a belief or action.",                                     type:"word"},
  {id:55, word:"Ameliorate",                 ipa:"/əˈmiːliəˌreɪt/",                      meaning:"To make something better or more tolerable, especially by improving conditions.",                                    type:"word"},
  {id:56, word:"Anachronism",                ipa:"/əˈnækrəˌnɪzəm/",                      meaning:"Something placed out of its proper historical time, appearing inappropriate.",                                        type:"word"},
  {id:57, word:"Erratic",                    ipa:"/ɪˈrætɪk/",                            meaning:"Unpredictable, inconsistent, or lacking a regular pattern in behavior or occurrence.",                               type:"word"},
  {id:58, word:"Garner",                     ipa:"/ˈɡɑːrnər/",                           meaning:"To gather, collect, or accumulate something, especially information or support.",                                    type:"word"},
  {id:59, word:"Accrue",                     ipa:"/əˈkruː/",                             meaning:"To accumulate or increase gradually over time, often referring to benefits or interest.",                            type:"word"},
  {id:60, word:"Anathema",                   ipa:"/əˈnæθəmə/",                           meaning:"Something intensely disliked or loathed; a formal curse or strong denunciation.",                                    type:"word"},
  {id:61, word:"Chimerical",                 ipa:"/kaɪˈmɛrɪkəl/",                        meaning:"Unrealistic or wildly fanciful; based on imagination rather than reality.",                                         type:"word"},
  {id:62, word:"Conflagration",              ipa:"/ˌkɒnfləˈɡreɪʃən/",                   meaning:"A large, destructive fire; figuratively, a violent conflict or turmoil.",                                            type:"word"},
  {id:63, word:"Diaphanous",                 ipa:"/daɪˈæfənəs/",                         meaning:"Light, delicate, and translucent; often used to describe fabric or textures.",                                       type:"word"},
  {id:64, word:"Excoriate",                  ipa:"/ɪkˈskɔːrieɪt/",                       meaning:"To criticize severely or harshly; literally, to strip or damage skin.",                                             type:"word"},
  {id:65, word:"Perspicacious",              ipa:"/ˌpɜːrspɪˈkeɪʃəs/",                   meaning:"Having keen insight and understanding; perceptive and discerning.",                                                  type:"word"},
  {id:66, word:"Fortitude",                  ipa:"/ˈfɔːrtɪtuːd/",                        meaning:"Mental and emotional strength in facing adversity or difficulty.",                                                   type:"word"},
  {id:67, word:"Mandate",                    ipa:"/ˈmændeɪt/",                           meaning:"An official order or command; authority granted to carry out a policy.",                                             type:"word"},
  {id:68, word:"Sampling",                   ipa:"/ˈsæmplɪŋ/",                           meaning:"The process of selecting a subset from a larger group for analysis or representation.",                              type:"word"},
  {id:69, word:"Inadvertent",                ipa:"/ˌɪnədˈvɜːrtənt/",                     meaning:"Unintentional; done without deliberate thought or awareness.",                                                       type:"word"},
  {id:70, word:"Erudition",                  ipa:"/ˌɛrjuːˈdɪʃən/",                       meaning:"Deep, extensive knowledge acquired through study or scholarship.",                                                   type:"word"},
  {id:71, word:"Detrimental",                ipa:"/ˌdɛtrɪˈmɛntl/",                       meaning:"Causing harm or damage; having a negative effect.",                                                                  type:"word"},
  {id:72, word:"Affinity",                   ipa:"/əˈfɪnɪti/",                           meaning:"A natural liking or connection; similarity or relationship between things.",                                         type:"word"},
  {id:73, word:"Distill",                    ipa:"/dɪˈstɪl/",                            meaning:"To purify a liquid through heating and condensation; to extract essential meaning.",                                type:"word"},
  {id:74, word:"Contend",                    ipa:"/kənˈtɛnd/",                           meaning:"To struggle or compete; to assert or argue a point.",                                                                type:"word"},
  {id:75, word:"Transience",                 ipa:"/ˈtrænziəns/",                          meaning:"The state of being temporary or short-lived.",                                                                       type:"word"},
  {id:76, word:"Diverge",                    ipa:"/daɪˈvɜːrdʒ/",                         meaning:"To move or extend in different directions; to differ in opinion or course.",                                         type:"word"},
  {id:77, word:"Arbitrary",                  ipa:"/ˈɑːrbɪtrəri/",                        meaning:"Based on random choice or personal whim, rather than reason or system.",                                             type:"word"},
  {id:78, word:"Custodian",                  ipa:"/kʌˈstoʊdiən/",                        meaning:"A person responsible for the care or protection of something.",                                                      type:"word"},
  {id:79, word:"Erudition",                  ipa:"/ˌɛrjuːˈdɪʃən/",                       meaning:"Deep knowledge acquired through study; the quality of being learned or scholarly.",                                 type:"word"},
  {id:80, word:"Custodian",                  ipa:"/kʌˈstoʊdiən/",                        meaning:"One who has responsibility for taking care of or protecting something.",                                             type:"word"},
  {id:81,  word:"Zero in on",                ipa:"/ˈzɪəroʊ ɪn ɒn/",                     meaning:"To focus attention, effort, or resources very precisely on a specific subject or target, often eliminating distractions.", type:"idiom"},
  {id:82,  word:"Learn the ropes",           ipa:"/lɜːrn ðə roʊps/",                    meaning:"To become familiar with how something is done, especially a job or task, through practical experience.",               type:"idiom"},
  {id:83,  word:"Behind closed doors",       ipa:"/bɪˈhaɪnd kloʊzd dɔːrz/",            meaning:"Done in private without public knowledge, often implying secrecy or confidentiality.",                                 type:"idiom"},
  {id:84,  word:"Ride the wave",             ipa:"/raɪd ðə weɪv/",                      meaning:"To take advantage of a successful trend or momentum and benefit from it while it lasts.",                             type:"idiom"},
  {id:85,  word:"Economic bubble",           ipa:"/ˌiːkəˈnɒmɪk ˈbʌbəl/",               meaning:"A market condition where prices rise far above real value due to speculation, often followed by a crash.",              type:"idiom"},
  {id:86,  word:"Go against the grain",      ipa:"/ɡoʊ əˈɡɛnst ðə ɡreɪn/",             meaning:"To act or think differently from what is usual, expected, or accepted.",                                               type:"idiom"},
  {id:87,  word:"A moot point",              ipa:"/ə muːt pɔɪnt/",                      meaning:"A topic that is either debatable or no longer relevant and has no practical importance.",                             type:"idiom"},
  {id:88,  word:"A far cry from",            ipa:"/ə fɑːr kraɪ frɒm/",                  meaning:"Something that is very different from another thing, often much worse or less desirable.",                            type:"idiom"},
  {id:89,  word:"Pull your weight",          ipa:"/pʊl jɔːr weɪt/",                     meaning:"To do your fair share of work or responsibility in a group.",                                                          type:"idiom"},
  {id:90,  word:"Cut corners",               ipa:"/kʌt ˈkɔːrnərz/",                     meaning:"To do something cheaply or quickly by skipping important steps, often reducing quality.",                             type:"idiom"},
  {id:91,  word:"Social butterfly",          ipa:"/ˈsoʊʃəl ˈbʌtərflaɪ/",               meaning:"A very sociable person who enjoys interacting with many people.",                                                      type:"idiom"},
  {id:92,  word:"A bitter pill to swallow",  ipa:"/ə ˈbɪtər pɪl tə ˈswɒloʊ/",          meaning:"An unpleasant fact or situation that is difficult but necessary to accept.",                                          type:"idiom"},
  {id:93,  word:"Get to the heart of the matter", ipa:"/ɡɛt tə ðə hɑːrt əv ðə ˈmætər/", meaning:"To focus on the most important or central issue.",                                                                  type:"idiom"},
  {id:94,  word:"Spell it out",              ipa:"/spɛl ɪt aʊt/",                       meaning:"To explain something very clearly and in detail so it cannot be misunderstood.",                                      type:"idiom"},
  {id:95,  word:"Put into perspective",      ipa:"/pʊt ˈɪntuː pərˈspɛktɪv/",           meaning:"To show the true importance of something by comparing it with other things.",                                         type:"idiom"},
  {id:96,  word:"Bring to the table",        ipa:"/brɪŋ tə ðə ˈteɪbəl/",               meaning:"To contribute useful ideas, skills, or resources to a situation or discussion.",                                      type:"idiom"},
  {id:97,  word:"In the loop",               ipa:"/ɪn ðə luːp/",                        meaning:"To be informed and included in decisions or ongoing developments.",                                                    type:"idiom"},
  {id:98,  word:"Call it a day",             ipa:"/kɔːl ɪt ə deɪ/",                     meaning:"To stop working on something for the rest of the day.",                                                               type:"idiom"},
  {id:99,  word:"Walk someone through",      ipa:"/wɔːk ˈsʌmwʌn θruː/",                meaning:"To guide someone step-by-step through a process.",                                                                    type:"idiom"},
  {id:100, word:"Zero in on",                ipa:"/ˈzɪəroʊ ɪn ɒn/",                     meaning:"To direct complete attention toward a specific goal or detail for deeper understanding or action.",                    type:"idiom"},
];

// ── State ──────────────────────────────────────────────
let mode = 'flashcard';
let filter = 'all';
let deck = [];
let idx = 0;
let flipped = false;
let quizChoices = [];
let quizAnswered = null; // word string or null
let score = {correct:0, total:0};
let known = {};
let browseSearch = '';

function getFiltered() {
  if (filter === 'all') return ALL_WORDS;
  return ALL_WORDS.filter(w => w.type === filter);
}

function shuffle(arr) {
  const a = [...arr];
  for (let i = a.length-1; i>0; i--) {
    const j = Math.floor(Math.random()*(i+1));
    [a[i],a[j]]=[a[j],a[i]];
  }
  return a;
}

function getChoices(correct, pool) {
  const others = shuffle(pool.filter(w=>w.id!==correct.id)).slice(0,3);
  return shuffle([correct,...others]);
}

function resetDeck() {
  const filtered = getFiltered();
  deck = shuffle(filtered);
  idx = 0; flipped = false;
  quizAnswered = null; score = {correct:0,total:0};
  if (mode==='quiz') quizChoices = getChoices(deck[0], filtered);
}

function setMode(m) {
  mode = m;
  document.querySelectorAll('.tab').forEach((t,i)=>{
    t.classList.toggle('active', ['flashcard','quiz','browse'][i]===m);
  });
  resetDeck();
  render();
}

function setFilter(f) {
  filter = f;
  document.querySelectorAll('.filter-btn').forEach((b,i)=>{
    b.classList.toggle('active', ['all','word','idiom'][i]===f);
  });
  resetDeck();
  render();
}

function goNext() {
  idx = (idx+1) % deck.length;
  flipped = false; quizAnswered = null;
  if (mode==='quiz') quizChoices = getChoices(deck[idx], getFiltered());
  render();
}

function goPrev() {
  idx = (idx-1+deck.length) % deck.length;
  flipped = false; quizAnswered = null;
  if (mode==='quiz') quizChoices = getChoices(deck[idx], getFiltered());
  render();
}

function flipCard() { flipped = !flipped; render(); }

function markKnown(val) {
  known[deck[idx].id] = val;
  goNext();
}

function answerQuiz(word) {
  if (quizAnswered !== null) return;
  quizAnswered = word;
  if (word === deck[idx].word) score.correct++;
  score.total++;
  render();
}

function doShuffle() {
  known = {};
  resetDeck();
  render();
}

// ── Render ─────────────────────────────────────────────
function render() {
  const main = document.getElementById('main');
  const cur = deck[idx];
  const knownCount = Object.values(known).filter(Boolean).length;
  const totalStudied = Object.keys(known).length;

  if (mode === 'flashcard') {
    const progPct = Math.round(((idx+1)/deck.length)*100);
    main.innerHTML = `
      <div class="prog-row">
        <span style="color:#556080;font-size:12px">${idx+1} / ${deck.length}</span>
        ${totalStudied>0 ? <span class="known-info">✓ ${knownCount}/${totalStudied} known</span> : ''}
        <span class="type-tag ${cur.type}">${cur.type}</span>
      </div>
      <div class="prog-bar"><div class="prog-fill blue" style="width:${progPct}%"></div></div>

      <div class="card ${flipped?'back':'front'}" onclick="flipCard()">
        ${!flipped ? `
          <div class="card-word">${cur.word}</div>
          <div class="card-ipa">${cur.ipa}</div>
          <div class="card-hint">Tap to reveal meaning</div>
         : 
          <div class="card-word-sm">${cur.word}</div>
          <div class="card-meaning">${cur.meaning}</div>
          <div class="card-ipa-sm">${cur.ipa}</div>
        `}
      </div>

      ${flipped ? `
        <div class="know-row">
          <button class="know-btn no" onclick="markKnown(false)">✗ Still learning</button>
          <button class="know-btn yes" onclick="markKnown(true)">✓ I know this</button>
        </div>
      ` : ''}

      <div class="nav-row">
        <button class="nav-btn wide" onclick="goPrev()">←</button>
        <button class="nav-btn shuffle" onclick="doShuffle()">Shuffle</button>
        <button class="nav-btn wide" onclick="goNext()">→</button>
      </div>
    `;

  } else if (mode === 'quiz') {
    const progPct = Math.round(((idx+1)/deck.length)*100);
    const scoreLabel = score.total>0
      ? <span class="score-info">${score.correct}/${score.total} correct</span>
      : <span style="color:#556080;font-size:13px">Select the right word</span>;

    const choicesHTML = quizChoices.map(c => {
      let cls = '';
      if (quizAnswered !== null) {
        if (c.word === cur.word) cls = 'correct';
        else if (c.word === quizAnswered) cls = 'wrong';
      }
      const mark = quizAnswered!==null
        ? (c.word===cur.word ? ' <span>✓</span>' : (c.word===quizAnswered ? ' <span>✗</span>' : ''))
        : '';
      return <button class="choice-btn ${cls}" onclick="answerQuiz('${c.word.replace(/'/g,"&#39;")}')">${c.word}${mark}</button>;
    }).join('');

    main.innerHTML = `
      <div class="prog-row">
        <span style="color:#556080;font-size:12px">${idx+1} / ${deck.length}</span>
        ${scoreLabel}
      </div>
      <div class="prog-bar"><div class="prog-fill green" style="width:${progPct}%"></div></div>

      <div class="quiz-question">
        <div class="quiz-q-label">Which word matches this meaning?</div>
        <div class="quiz-q-text">${cur.meaning}</div>
      </div>

      <div class="quiz-choices">${choicesHTML}</div>

      ${quizAnswered!==null ? <button class="next-btn" onclick="goNext()">Next →</button> : ''}
    `;

  } else {
    // BROWSE
    const filtered = getFiltered();
    const q = browseSearch.toLowerCase();
    const results = filtered.filter(w =>
      w.word.toLowerCase().includes(q) || w.meaning.toLowerCase().includes(q)
    );

    const itemsHTML = results.map(w => `
      <div class="browse-item">
        <div class="browse-item-top">
          <div class="browse-word">${w.word}</div>
          <span class="browse-tag ${w.type}">${w.type}</span>
        </div>
        <div class="browse-ipa">${w.ipa}</div>
        <div class="browse-def">${w.meaning}</div>
      </div>
    `).join('');

    main.innerHTML = `
      <input id="browse-search" type="text" placeholder="Search words or meanings…"
        value="${browseSearch.replace(/"/g,'&quot;')}"
        oninput="browseSearch=this.value;render()" />
      <div class="browse-count">${results.length} RESULT${results.length!==1?'S':''}</div>
      <div class="browse-list">${itemsHTML}</div>
    `;
  }
}

// ── Init ───────────────────────────────────────────────
resetDeck();
render();
</script>

</body>
</html>
