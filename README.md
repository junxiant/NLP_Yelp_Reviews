# NLP_Yelp_Reviews

### Table of contents
* [Description](#description)
* [Installing Dependencies](#installing-dependencies)
* [Code Sample Outputs](#code-sample-outputs)
  * Dataset Analysis
  * Indicative Adjective Phrases
  * Application (Sentiment Analysis + Text Summarization)

### Description
NLP Project, with Tokenizing, Stemming, Phrases Extraction, POS Tagging, Sentiment Analysis, Text Summarization

### Installing Dependencies
```
!pip install -r requirements
```

Some NLTK modules needed to be downloaded

```
import nltk
nltk.download([
               'stopwords',
               'punkt',
               'averaged_perceptron_tagger',
               'tagsets'
])
```
### Code Sample Outputs
#### Dataset Analysis

##### Frequency Distributions
B1 Frequency Distribution for top 10 words before stemming
![image](https://user-images.githubusercontent.com/25401067/134932385-3bb1384e-0d1f-48ad-aab0-144e11f53554.png)

B1 Frequency Distribution for top 10 words after stemming
![image](https://user-images.githubusercontent.com/25401067/134933129-aec754ef-e283-4cd2-947e-bb4177ed78cd.png)

B2 Frequency Distribution for top 10 words before stemming
![image](https://user-images.githubusercontent.com/25401067/134933290-ae418738-933c-4ebc-b57c-cfc0785a3c94.png)

B2 Frequency Distribution for top 10 words after stemming
![image](https://user-images.githubusercontent.com/25401067/134933312-7825cc7f-6636-4fab-8de5-8e2c14f953cf.png)

##### POS Tagging
5 Random Sentences
```
12991                 and the kam poong-gi ("fried" chicken dish).
6052                                               Expensive food.
9794                                             Highly recommend.
10251                              Yummy who doesn't love pizza?!?
5243     I'm here visiting and loved this little hole in the wall.
Name: random_sentence, dtype: object
```
Using NLTK
```
	random_sentence	pos_tags_nltk
12991	and the kam poong-gi ("fried" chicken dish).	[(and, CC), (the, DT), (kam, JJ), (poong-gi, NN), ((, (), (``, ``), (fried, VBN), ('', ''), (chicken, JJ), (dish, NN), (), )), (., .)]
6052	Expensive food.	[(Expensive, JJ), (food, NN), (., .)]
9794	Highly recommend.	[(Highly, NNP), (recommend, NN), (., .)]
10251	Yummy who doesn't love pizza?!?	[(Yummy, NNS), (who, WP), (does, VBZ), (n't, RB), (love, VB), (pizza, NN), (?, .), (!, .), (?, .)]
5243	I'm here visiting and loved this little hole in the wall.	[(I, PRP), ('m, VBP), (here, RB), (visiting, VBG), (and, CC), (loved, VBD), (this, DT), (little, JJ), (hole, NN), (in, IN), (the, DT), (wall, NN), (., .)]
```

Using Flair

```
[(Token: 1 and, 'CC'),
 (Token: 2 the, 'DT'),
 (Token: 3 kam, 'NN'),
 (Token: 4 poong-gi, 'NN'),
 (Token: 5 (", '``'),
 (Token: 6 fried, 'JJ'),
 (Token: 7 ", '``'),
 (Token: 8 chicken, 'NN'),
 (Token: 9 dish, 'NN'),
 (Token: 10 ), "''"),
 (Token: 11 ., '.'),
 (Token: 1 Expensive, 'JJ'),
 (Token: 2 food, 'NN'),
 (Token: 3 ., '.'),
 (Token: 1 Highly, 'RB'),
 (Token: 2 recommend, 'VB'),
 (Token: 3 ., '.'),
 (Token: 1 Yummy, 'NNP'),
 (Token: 2 who, 'WP'),
 (Token: 3 does, 'VBZ'),
 (Token: 4 n't, 'RB'),
 (Token: 5 love, 'VB'),
 (Token: 6 pizza, 'NN'),
 (Token: 7 ?!, '.'),
 (Token: 8 ?, '.'),
 (Token: 1 I, 'PRP'),
 (Token: 2 'm, 'VBP'),
 (Token: 3 here, 'RB'),
 (Token: 4 visiting, 'VBG'),
 (Token: 5 and, 'CC'),
 (Token: 6 loved, 'VBD'),
 (Token: 7 this, 'DT'),
 (Token: 8 little, 'JJ'),
 (Token: 9 hole, 'NN'),
 (Token: 10 in, 'IN'),
 (Token: 11 the, 'DT'),
 (Token: 12 wall, 'NN'),
 (Token: 13 ., '.')]
 ```

##### Noun-Adjective pairs
Top 10 1 star Noun-Adjective pairs

```
	0	1
pairs		
food good	372	372
food bad	372	372
food other	279	279
food more	279	279
food few	248	248
food worst	248	248
manager good	240	240
manager bad	240	240
food new	186	186
food great	186	186
```

Top 10 2 star Noun-Adjective pairs

```
	0	1
pairs		
food good	78	78
manager good	72	72
place good	66	66
food few	65	65
food bad	65	65
food more	65	65
manager few	60	60
manager bad	60	60
manager more	60	60
place few	55	55
```

Top 10 3 star Noun-Adjective pairs

```
	0	1
pairs		
food good	266	266
place good	196	196
order good	154	154
food great	152	152
food other	133	133
food bad	114	114
food few	114	114
place great	112	112
place other	98	98
food new	95	95
```

Top 10 4 star Noun-Adjective pairs
```
	0	1
pairs		
food good	180	180
place good	165	165
sausage good	105	105
restaurant good	90	90
stew good	90	90
food great	84	84
place great	77	77
meal good	75	75
waffles good	75	75
day good	75	75
```

Top 10 5 star Noun-Adjective pairs
```
	0	1
pairs		
place great	150	150
food great	110	110
place good	105	105
food good	77	77
place only	75	75
food only	55	55
place best	45	45
voodoo great	40	40
reason great	40	40
star great	40	40
```

#### Indicative Adjective Phrases
```
['sunday local overweight christianchurch',
 'weekly worship brief',
 'asian shrines',
 'etc place',
 'enough seating',
 'good many items',
 'seemed fresh enough theres',
 'fresh seafood charlotte im dmv land',
 'blue crabs hibachi station',
 'several options',
 'right spot',
 'amazing american items',
 'asianized american food dont',
 'seafood hibachi',
 'enough service',
 'good ask youre',
 'lunch cheaper cant',
 'broad food menu',
 'low price regards trizzyoo',
 'best buffett bar none',
 'huge place',
 'big groups everything',
 'awesome hibachi sushi bars',
 'fried dumplings',
 'wish lowsodium soy',
 'miss somtimes',
 'unfresh lobsters',
 'cheap black market lobsters',
 'star experience',
 'usual grub call grub quantity mediocre mainstream',
 'chinese food',
 'chicken french fries',
 'decent variety seafood',
 'sashimi sushi',
 'sashimi lunch',
 'best bet buy sashimi pound',
 'sushi bit',
 'intense people',
 'real point place doesnt beat rusans',
 'sushi rusans',
 'yellowtail rusans',
 'better ok review',
 'picky place fine',
 'absolute cheapest place',
 'indian buffet',
 'sushi chinesejapaneserandom buffets',
 'garlic toast',
 'ok flavor mushy',
 'hard edges',
 'hot pocket',
 'crabsthis place',
 'go time family place',
 'chinese menu',
 'salad great fruits',
 'tasty pineapples',
 'worth price thing',
 'awesome im',
 'regular huge fan',
 'hibachi place',
 'regular buffet bars',
 'great options',
 'sushi selections',
 'great sashimi many types',
 'fresh fruits',
 'reasonable price',
 'last time',
 'chinese buffet years',
 'lunch let',
 'huge wide array options',
 'decent buffet',
 'clean hibachi section sushi section lot',
 'good place groups prices',
 'crappy enter',
 'crazy lavish buffets',
 'honest weak spot places',
 'predicament night',
 'avail tokyo',
 'interesting find',
 'impressed buffet setup amount',
 'different items',
 'thats excitement',
 'much anything',
 'admit items',
 'mediocre rest',
 'loaded msg',
 'sorriest excuse mac',
 'cheese face planet',
 'noodle soup',
 'wouldnt eat pros',
 'good layout',
 'happen frequent tokyo favor',
 'either fresh hibachi',
 'sushi section',
 'fabulous food helpful',
 'friendly staff',
 'happy sashimi',
 'enjoyable experience',
 'overall first foremost',
 'delicious food',
 'longest time',
 'ignored place',
 'another asian buffet',
 'read reviews',
 'try place',
 'right husband',
 'sushi bar',
 'crab frog legs',
 'delicious husband',
 'sushi soups',
 'good uncommon good way thing',
 'wide selection',
 'japanese hibachi choices',
 'american fare',
 'nonasian palate',
 'huuuuge number',
 'dessert offerings',
 'different flavors',
 'super busy tell wait',
 'much shorter tell valentines day',
 'best chinese buffets',
 'amazing matter style food',
 'love place buffet items',
 'sure food',
 'least warm fish rubbery egg drop soup thick',
 'iti swear hope',
 'raw eggs',
 'big clean staff',
 'another perspective buffets',
 'old raw fishes',
 'sushi talk sushi taste alli',
 'go place cause',
 'close hotel',
 'buffet restaurant',
 'lunch customer service',
 'keep drinks',
 'full table clean',
 'buffet variety sushi',
 'chinese american something everyone',
 'lo mein butterfly shrimp',
 'soft rolls',
 'great groups',
 'inclusive dinner',
 'hard beat sushi selection',
 'change items',
 'lowered prices',
 'quality staff',
 'attentive hibachi',
 'top notch buffet',
 'raw eggs',
 'great buffet money imo',
 'higher quality food',
 'true sushi restaurant',
 'better pricequality buffet',
 'usual buffet',
 'stocked everything',
 'fresh hot servers',
 'full complaints',
 'last year',
 'filthy ground',
 'another chinese buffet',
 'great buffet food awesome',
 'delicious staff kind',
 'real nice awesome',
 'love place',
 'great food',
 'great people',
 'good work promise',
 'lower food quality',
 'good food decent service',
 'please ask waitress',
 'good food',
 'fan dishonest people',
 'tip new fleece columbia jacket',
 'saturday night',
 'delicious course buffet',
 'liked hibachi',
 'great selection items',
 'sushi selection reviews',
 'huge selection rollsmakis',
 'respectable nigiri salmon tuna yellowtail clean',
 'attendant nice pleasant',
 'great meat selection seafood selection hibachi grill',
 'overall better rest',
 'nice dinner day',
 'expansive selection',
 'numerous sushi choices staff',
 'efficient keeps everything',
 'green beans',
 'delicious normal chinese buffet fare',
 'many dessert choices',
 'cream area',
 'difficult navigate',
 'awful price',
 'add gratuity',
 'hold room',
 'large parties',
 'unable control',
 'large environment returnand',
 'several others party',
 'high standards',
 'best chinese buffet',
 'ive youre',
 'profile picture ingredients',
 'large variety sushi',
 'buffet quality hibachi grill',
 'dont feel',
 'large selection food pleases everyone family daughter gorges',
 'every single time',
 'hibachi line',
 'heard people',
 'stupid remarks',
 'wait time theres',
 'busy hes',
 'hard worker waiters',
 'hibachi guy man',
 'main reason mama',
 'ive eaten ive gotten',
 'used term sushi',
 'fried creamy stuff',
 'cold order spoil service',
 'ok experience',
 'wouldnt mind',
 'riff raff',
 'clean customer service',
 'awesome food okay nothing',
 'worth second trip',
 'favorite part cold mussels',
 'sauce second hibachi',
 'first time buffet',
 'huge selection food',
 'available dont',
 'big much variety party',
 'plenty eat',
 'lunch price',
 'terrible experience understand buffet buffets',
 'nasty prices',
 'dry waiter',
 'table several times',
 'front area pay',
 'denial powerful belief',
 'best buffet charlotte',
 'nc course',
 'asian buffet sushi',
 'excellent wish use',
 'white fish inside',
 'great thing',
 'small portion steak hibachi thats',
 'great choice food plenty amount',
 'average place',
 'good amount',
 'another great thing lunch',
 'dinner weekend buffet',
 'asian buffet',
 'every single time',
 'eat end',
 'much reason deserve',
 'huge hit',
 'short period time',
 'typical asian buffet',
 'many times',
 'big lots',
 'old party city use restaurant',
 'buffet traditional chinese dishes',
 'general tsos chicken dumplings',
 'hibachi station',
 'good variety meat seafood options rice noodles',
 'assortment veggies',
 'first stop',
 'hibachi station',
 'selection sushi',
 'available price point restaurant',
 'im sure theres',
 'bigger better sushi buffet',
 'available charlotte',
 'typical chinese asian food items',
 'typical nothing',
 'many reviews',
 'american food items',
 'oriental food place',
 'many food selection waitstaff',
 'ive sushi',
 'good fresh seafood charlotte im hawaii',
 'good quality',
 'green tea ice cream',
 'next big lots home',
 'lunch time',
 'good food sushi',
 'fastmy suggestion',
 'good habachi place sort foods dad',
 'cheap get quality food',
 'pretty clean dinner',
 'give place try',
 'worst place',
 'moneythe staff understand',
 'specific food',
 'horrible main dishes',
 'sushi hard old hibachi grill',
 'wasnt clean bathrooms',
 'hard urine please',
 'new sushi spot',
 'great place',
 'entire family',
 'great time',
 'large selection buffet bar salad bar sushi bar desert bar',
 'fresh sushi mouth',
 'good cant wait',
 'interior nice lots people',
 'buffet average',
 'disappointed steam fish soy sauce',
 'dry rubbery person',
 'prepared vegetables',
 'good job',
 'server price good',
 'decent buffet',
 'opened place',
 'sure come lunchdinner',
 'many tables staff',
 'nice service',
 'good whisk',
 'old plates',
 'good food',
 'decent didnt',
 'laden sugar salt',
 'old corn ick people',
 'nuts frog legs',
 'broccoli dishes',
 'hot sour soup im',
 'picky soup soup ton pepper',
 'restaurant soup',
 'give usual suspects',
 'good companions',
 'miss im',
 'big buffets',
 'hang people',
 'busy food',
 'great variety food options',
 'meaty gripe place hibachi grill guy cook',
 'doesnt taste',
 'great try stay',
 'yea doesnt work',
 'good place eat',
 'low cost',
 'best chinese style food',
 'many optionslow cost quick',
 'huge selection food god',
 'best quality food',
 'cant get',
 'much better busy im',
 'youre area',
 'hungry give try',
 'large buffet selection food',
 'okay waitstaff',
 'table buffet inexpensive food soso',
 'hungry budget im',
 'big buffet person husband',
 'many buffets',
 'best buffet town varieties food',
 'fresh hot place eaters',
 'subjective thing',
 'good great matter',
 'ive opportunity',
 'chinese buffets',
 'tokyo grill',
 'university city area',
 'couple times',
 'sushi bar im',
 'picky sushi scale',
 'chinese buffets',
 'menu items',
 'oddball items',
 'higher chens',
 'native charlotteans',
 'overall cleanliness restaurant indication sushi bar im glad',
 'possessed owners',
 'high traffic',
 'flowhigh turnover restaurant',
 'restaurant mind nothing',
 'good place stuff pumpkin mediocre food',
 'miserable im recommend',
 'another chinese buffet',
 'least knows year itll',
 'many choices',
 'delicious many vegetables meats',
 'american food',
 'good many desserts',
 'good reason',
 'scramble food',
 'ok service',
 'nice food phenomenal',
 'less stellar enter sushi sushi guy',
 'hot sour soup',
 'id pay sit eat nothing day',
 'shrimp awesome octopus',
 'tough mac cheese',
 'sweet couldnt eat',
 'overall average id',
 'oh man hate',
 'bad experience man',
 'good see',
 'old review place',
 'front new name',
 'original review',
 'dont waste time',
 'asian buffets',
 'ive sushi buffets',
 'head shoulders',
 'buffet lunch',
 'big separate sushi thank god',
 'grill actual regular buffet',
 'bigger anywhere',
 'right closing',
 'fresh clean buffet dont feel',
 'full msg couldnt eat',
 'huge variety stuff husband',
 'much cost dont',
 'disappointed wish',
 'try tokyo buffet everyone',
 'sashimi nigiri style sushi',
 'salmon sake tuna maguro yellowtail hamachi',
 'bad news',
 'sashimi section',
 'entire time',
 'worst yellowtail',
 'raw potato',
 'actual yellowtail color flavor',
 'opaque hint pink plenty pieces',
 'fish maximize volume',
 'leaner yellowtail',
 'dont mess salmon tuna alright items',
 'typical chinesemongolianjapanese buffet',
 'typical place offers',
 'ubiquitous doughy dumplings',
 'multiple varieties',
 'deep fat',
 'chicken pepper tsos sesame',
 'chicken wings pizza',
 'prime rib',
 'prime rib',
 'good stuff display',
 'typical types places',
 'feedbag tokyo grill',
 'individual dish',
 'normal restaurant',
 'similar little variety',
 'indiscriminately shovel food face',
 'stick salmon tuna way',
 'sashimi grade sushi',
 'best food',
 'freshest restaurant',
 'little kids',
 'sanitary expectations',
 'stuff hands',
 'little things',
 'dessert section hotspot',
 'little kids',
 'favorite service',
 'good buffet',
 'overall good place',
 'cleannot expensiveand food taste',
 'great come time',
 'buffet choice buffets',
 'accompany huge family',
 'wide selection food',
 'best thing buffet amounts',
 'many chinese buffets',
 'extra crab see steers people',
 'dont crab legs',
 'much profit',
 'succulent flavor',
 'different wings buffets',
 'isnt half',
 'bad buffets',
 'fresh wouldnt',
 'different choices fruit',
 'great food',
 'great service',
 'hibachi sushi top',
 'learned lesson',
 'long time',
 'utensils chicken dishes',
 'sesame general taos',
 'good fussy quality',
 'huge variety stuff',
 'due moms',
 'didnt notice',
 'dont eat places',
 'ive times',
 'last time',
 'fasted day preparation food',
 'hesitant eat',
 'raw fish buffet',
 'bad combination havent',
 'negative effects',
 'save room complaint',
 'crab legs',
 'lower average buffet price',
 'salad salmon juicy roast beef',
 'sushi keep',
 'shrimp dish bubba',
 'forrest gump',
 'believe people',
 'friendly waitresses',
 'great try hibachi grill',
 'opening price',
 'incredible quality sushi',
 'good wish',
 'eat see',
 'big fan buffets',
 'great value money',
 'short wait',
 'nice sushi selection youre chicken',
 'asian feel look',
 'decor nice fountain water',
 'fish place',
 'cleaner food',
 'wide selection seafood meat',
 'old food items lot people',
 'old add fresh hot food',
 'mixed old food',
 'average chinese honky food sushi',
 'typical buffet fare',
 'worth oysters',
 'cold shrimp',
 'pale dead mussels',
 'dethawed watery mess place',
 'doesnt pop admire workers closing time',
 'full blown worker bee mode',
 'restaurant floors',
 'every single worker',
 'em group home im',
 'hard money tip',
 'late lunch worth',
 'long time place',
 'clean staff',
 'attentive food',
 'fresh large selection',
 'hot deliciousi',
 'lol hibachi grill',
 'great fast fruit sweet juicy',
 'pete hot sauce daughters',
 'sauce everythingi',
 'purse eat lunch',
 'futurethis typical chinese buffet',
 'ok second time',
 'first time',
 'eat place didnt',
 'japanese restaurants',
 'mexican foodssmh',
 'fantastic great variety',
 'incredible volume place',
 'clean seats',
 'timw hibachi grill',
 'good inexpensive service',
 'regular buffet',
 'sushi bar hibachi grill',
 'good asian food',
 'great price',
 'good wide variety sushi',
 'great ample selection',
 'nonfish rolls',
 'salad bar',
 'great mixed greens',
 'eggs fruit',
 'favorite choice',
 'various seafood dishes',
 'greater vegetable dish selection buffetbroccoli mix',
 'green beans',
 'dinner price excellent',
 'fellow yelpies',
 'close uncc next big lots anyone strip',
 'know lot businesses',
 'awesome buffet everything',
 'chinese japanese american options',
 'hibachi stations',
 'leave place feel',
 'worth fact',
 'leave place feeling',
 'stole thats',
 'good amazing price lots businesses',
 'university area',
 'able survive',
 'chinese food buffetsthis place',
 'bad great eitherthe',
 'good pepper steak',
 'hot sour soup sushi bbq ribs',
 'sauteed shrimp',
 'carbonated drinks',
 'chinese buffets',
 'fizz mix syrupthe',
 'bad fried rice',
 'hard get',
 'small isnt illegal catch sell miniture crabsdoesnt',
 'thisthe crawfish sauce thats problem',
 'wasnt moist drythe servers',
 'male servers',
 'typical chinese buffet',
 'favorite place',
 'mediocre place',
 'huge parking lot',
 'feel place',
 'little dirty sushi',
 'okay thing',
 'fried crab coconut shrimp',
 'lunch great selection house',
 'sushi awesome rest buffet',
 'hibachi chinese american salad bar desserts',
 'medical emergency',
 'outside ambulance ambulance',
 'ready leave staff',
 'table guy',
 'grabbed bill',
 'door ambulance bill wasnt',
 'whats wrong people',
 'pathetic restaurant',
 'authentic chinese food ok buffet',
 'good care',
 'chinese buffets',
 'great lunch deal student discount',
 'full range foods',
 'hibachi chinese goodness',
 'fast service cleanliness',
 'place nothing',
 'fresh surprise buffet',
 'normal fare',
 'chinese buffet several japanese items',
 'decent american section dont eat buffet pizza snob',
 'tempting huge compliment staples',
 'seseme gen tso',
 'cheese wantons',
 'tuesday special day',
 'several fishes',
 'premium items',
 'additional charge',
 'sushi bar rivals',
 'buffet lunches town',
 'robbed place',
 'cheap wouldve',
 'superb deal',
 'top tier kudos',
 'favorite buffet',
 'thy handle large crowds',
 'tonight place',
 'lit staff super',
 'old son',
 'many chinese american japanese dishes',
 'good huge sushi hibachi stations',
 'ice cream sundae station',
 'new goto',
 'chinese place',
 'big fan buffets',
 'best buffet ive',
 'restaurant family',
 'pretty clean buffet',
 'cheap quality food',
 'good needs',
 'dont waste time',
 'asian buffets',
 'ive sushi buffets',
 'head shoulders',
 'buffet lunch',
 'big separate sushi thank god',
 'grill actual regular buffet',
 'bigger anywhere',
 'right closing',
 'fresh clean buffet dont feel',
 'full msg couldnt eat',
 'huge variety stuff husband',
 'much cost dont',
 'disappointed wish',
 'try tokyo buffet everyone',
 'much selection',
 'good price',
 'plenty eat everything',
 'good fresh hot sushi bar',
 'good sweet tea',
 'atlanta brothers family family',
 'asian buffet',
 'cheaper variety',
 'tokyo grill',
 'saw people',
 'able walk get',
 'prompt food',
 'good flavors',
 'like desserts',
 'green tea flavor waiter',
 'dirty plates',
 'impress service',
 'next time town',
 'wide variety',
 'fresh sushi',
 'friendly staff wont',
 'better meal',
 'restaurant huge restaurant offer',
 'huge variety food',
 'excellent quality food',
 'best buffet sushi youll',
 'right place favorites',
 'crab rangoons',
 'steak thing',
 'general tsos etc style',
 'id avoid rest',
 'american options',
 'little yuck whos',
 'healthy love sushi son',
 'hibachi cook order husband',
 'fresh fruit seafood food',
 'delicious regular price',
 'closer closer',
 'miss buffet understand',
 'mixed restaurant',
 'japanese name',
 'chinese waiters food',
 'chinese american mexican japanese food',
 'average level',
 'cheap bufet',
 'super yummy dont',
 'eat foods',
 'good staff',
 'clean first food',
 'outstanding amazing selection seafood',
 'reliable source',
 'cant stand seafood mother',
 'seafood sushi hibatchi bar lines',
 'packed keep mind',
 'nervous crowds',
 'saturday im sure something',
 'several large groups people',
 'another several small parties',
 'seat testimony deliciousness food',
 'several asian families',
 'foreign food place people culture eat',
 'good excellent place',
 'worst food',
 'chinese buffet',
 'good buffet joint',
 'new favorite buffet plenty seats',
 'good clean food lot selections',
 'best sushi buffet',
 'inexpensive price sashimi',
 'favorite part',
 'blue crabs hands lot ice cream selections',
 'oreo cookies',
 'menus sweet staffs',
 'attentive recommend place',
 'picky high expectations',
 'good food decent service',
 'please ask waitress',
 'good food',
 'fan dishonest people',
 'tip new fleece columbia jacket',
 'horrible food im',
 'sure taste buds',
 'great place eat',
 'entire party',
 'overall flavor food',
 'desirable fried soft shell crab',
 'catfish jello',
 'much sauce hibachi plate',
 'huge buffet',
 'good sushi place',
 'tonight group',
 'right beside table couldnt',
 'gross staff',
 'right id',
 'sick food',
 'bomb lots options price',
 'glad place',
 'great kids',
 'fish beautiful fountain food selection everything',
 'largest delicious sushi selection',
 'real hibachi buffet',
 'best chinese buffet youve',
 'japanese hibachi place fuse',
 'dont cook food front',
 'table sit fire tricks',
 'front grill station',
 'hibachi foodbeef chicken shrimp',
 'iffy moist mouth',
 'dry idea',
 'great kabuto lunch prices',
 'reasonable hostess servers',
 'fresh enjoy look',
 'frenchi j youtube',
 'birthday experience show food establishment',
 'disappointed fresh tasty seafood',
 'good negative thing people']
 ```
 
 Another sample
 ```
 ['many many years',
 'bad meal tons',
 'vegas place',
 'favorite steak',
 'favorite server frederick love',
 'counter friends',
 'asian males',
 'white male mid',
 'new patrons',
 'nice hk cafe kind place',
 'tea free wifi food',
 'good portions',
 'decent lots room',
 'large groups',
 'couple people',
 'quick bite',
 'nice restaurant title',
 'perfect vibe theyre',
 'give classic vintage look course giant jukebox right middle restaurant',
 'choose variety songs food',
 'classic american food greasy',
 'big portions',
 'best quality',
 'best wasnt',
 'able finish mine burgers',
 'prepared bring appetite',
 'heavy price',
 'rare occasions service staff',
 'friendly efficient',
 'new waitress im gon',
 'fabulous didnt rhythm',
 'parmesan white sauce pasta',
 'white sauce',
 'pour mix',
 'white sauce',
 'alsoshe new make',
 'big deal',
 'white sauce',
 'itemized ticket',
 'itemized receipt',
 'white sauce',
 'continue patronage',
 'eat sure hope',
 'dont act',
 'entrance sence',
 'live move securityplace respect',
 'lazy daisys serves',
 'aro coffee',
 'delicious sandwiches',
 'gerrardcoxwelll area',
 'high ceilings lots tables',
 'young kids cappuccino',
 'caramel brownie',
 'good cant',
 'excellent wish cappuccino foam',
 'frothier hence',
 'smooth caramel',
 'brownie love salt',
 'ive sandwiches',
 'great place hangout grab bite chillout',
 'id drive azusa roomie',
 'west covina get beef bowl yoshinoya',
 'salad couldnt decide beef chicken perfect',
 'much taste',
 'little better little flavor lot',
 'much meat',
 'different recipes thats',
 'compare guess',
 'eat cup tea',
 'favorite places',
 'nice meal decor',
 'wonderful comfortable booths',
 'huge staff',
 'last time',
 'new waiter eddie',
 'great usual waiter',
 'special food',
 'phenominal everything tasts',
 'wonderful wine',
 'great food',
 'catfish burrito st charles',
 'carne asada ktacos hola',
 'menu nice people',
 'great food doesnt']
 ```

#### Application
View average ratings

KDE Plot

![image](https://user-images.githubusercontent.com/25401067/134936971-150c2f23-35c3-4e4a-8748-0cca5c8b6fec.png)

Histogram

![image](https://user-images.githubusercontent.com/25401067/134936978-89dc9b4d-7bf2-4020-9903-66339d909eba.png)

View average sentiment

KDE Plot

![image](https://user-images.githubusercontent.com/25401067/134937046-d9fa8048-828f-4553-8a98-03b9d80729b6.png)

Histogram

![image](https://user-images.githubusercontent.com/25401067/134937086-6f216704-b364-441f-b709-85594d9f1877.png)

Correlation
```
Correlation between ratings (stars) and sentiment analysis: 
 0.8840093245497612
 ```

Positive Word Cloud

![image](https://user-images.githubusercontent.com/25401067/134937169-17261c24-10ed-4ab0-9f9f-1d6e42a76b6f.png)

Negative Word Cloud

![image](https://user-images.githubusercontent.com/25401067/134937197-5922d706-3157-4e1b-8c82-96abe9ebf62f.png)

Text Summarization

```
0                  Lyles is a great place to have a party.
1        A fun place to eat for a date or group of frie...
2                              Reviews for Keali'i Reichel
3                                         Food: Very good.
4        I have been having problems with my swimming p...
                               ...                        
15295    I'm writing this from the parking lot of a bea...
15296                    The Pub in Las Vegas is the best!
15297    My husband and I have been going to Todd Engli...
15298    We had a wonderful breakfast at Denny's on Val...
15299    I've been to this place before and it's the be...
Name: summarized, Length: 15300, dtype: object
```
Average sentiment after Text Summarization

KDE Plot

![image](https://user-images.githubusercontent.com/25401067/134937316-b4c3b17d-9347-48bf-840f-def98a24aee4.png)

Histogram

![image](https://user-images.githubusercontent.com/25401067/134937361-caea4866-c578-480b-836b-fd5a5a1605c7.png)

Correlation
```
Correlation between ratings (stars) and sentiment analysis: 
 0.7808560762031502
 ```

Positive Word Cloud

![image](https://user-images.githubusercontent.com/25401067/134937411-867994b7-6627-47d6-90ce-530e153e81f6.png)

Negative Word Cloud

![image](https://user-images.githubusercontent.com/25401067/134937433-4c1f75ae-581e-47e1-8a80-6460a5b67157.png)
