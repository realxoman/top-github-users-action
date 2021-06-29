# Top GitHub Users Action
Check your rank in GitHub! Get the list of active users in GitHub by country using GitHub Graph API. Go to [gayanvoice/top-github-users](https://github.com/gayanvoice/top-github-users).
[![Top GitHub Users by Country](https://github.com/gayanvoice/top-github-users-action/raw/master/public/images/readme/index.PNG)](https://github.com/gayanvoice/top-github-users)
## Setup
**1 —** Create an empty repository and name the rpository as `top-github-users`

**2 —** 🔒 Create a new personal access token with `repo` `workflow` `admin:org` `user` options

Go to Personal Access Tokens and click on Generate new token button. Give it any name and select `repo` `workflow` `admin:org` `user` options and click on Generate token button. ✂️ Copy the token.

**3 —** 🔑 Go to your top-github-users repository and go to **Settings**, and select **Secrets** option from left side bar. Click on **New repository secret** button and enter **name** as **CUSTOM_TOKEN** and 📋 paste the **personal access token** under **value**. Click on **Add secret** button.

**4 —** Go to your top-github-users repository and click on Actions tab. Click on **set up a workflow yourself** link to create a new workflow and paste the below content into yml file. Commit changes and click on **Run workflow** button.

```yml
name: Top GitHub Users
on:
  schedule:
    - cron: '0 * * * *'
  workflow_dispatch:
jobs:
  release:
    name: GitHub Active Users
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2.3.4
        with:
          ref: ${{ github.head_ref }}
          token: ${{ secrets.CUSTOM_TOKEN }}
      - uses: actions/setup-node@v2.1.5
        with:
          node-version: 14.17.0
      - uses: gayanvoice/top-github-users-action@master
        env:
          CUSTOM_TOKEN: ${{ secrets.CUSTOM_TOKEN }}

```
**5 —** 📄 Go to your top-github-users repository. Create a JSON file **config.json**. Copy the content and paste to the config.json.

```json
{
  "devMode": "false",
  "locations":[
    { "country":  "afghanistan", "geoName": "Afghanistan", "cities": ["kabul", "kandahar", "herat", "Kunduz", "lashkargah", "ghazni", "khost", "zaranj"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/9a/Flag_of_Afghanistan.svg" },
    { "country":  "albania", "geoName": "Albania", "cities": ["tirana", "durrës", "vlorë", "elbasan", "shkodër", "kamëz", "fier", "korçë"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/3/36/Flag_of_Albania.svg" },
    { "country":  "algeria", "geoName": "Algeria", "cities": ["algiers", "oran", "constantine", "batna", "djelfa", "sétif", "annaba", "sidibelabbès", "biskra", "tiaret"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/7/77/Flag_of_Algeria.svg" },
    { "country":  "andorra", "geoName": "Andorra", "cities": ["andorra-la-vella", "santa-coloma", "la-margineda", "engolasters"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/1/19/Flag_of_Andorra.svg" },
    { "country":  "angola", "geoName": "Angola", "cities": ["luanda", "cabinda ", "huambo", "lubango ", "kuito", "malanje ", "lobito", "benguela"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/9d/Flag_of_Angola.svg" },
    { "country":  "argentina","geoName": "Argentina", "cities": ["buenos-aires", "cordoba", "rosario", "la-plata", "tucumán", "mar-del-plata", "salta", "santa-fe"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/1/1a/Flag_of_Argentina.svg" },
    { "country":  "armenia", "geoName": "Armenia", "cities": ["yerevan", "gyumri", "vanadzor", "vagharshapat", "abovyan "], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/2/2f/Flag_of_Armenia.svg" },
    { "country":  "australia", "geoName": "Australia", "cities": ["sydney", "melbourne", "perth", "adelaide", "brisbane", "canberra", "hobart", "gold-coast", "darwin"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/88/Flag_of_Australia_%28converted%29.svg" },
    { "country":  "austria", "geoName": "Austria", "cities": ["vienna", "salzburg", "innsbruck", "linz", "graz", "klagenfurt", "bregenz", "villach"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/41/Flag_of_Austria.svg" },
    { "country":  "azerbaijan", "geoName": "Azerbaijan","cities": ["baku", "ganja", "sumqayit", "mingecevir"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/dd/Flag_of_Azerbaijan.svg" },
    { "country":  "bahrain","geoName": "Bahrain", "cities": ["nassau", "riffa", "muharraq"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/2/2c/Flag_of_Bahrain.svg" },
    { "country":  "bangladesh", "geoName": "Bangladesh", "cities": ["dhaka", "mymensingh", "rajshahi", "rangpur", "chittagong", "khulna"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Flag_of_Bangladesh.svg/800px-Flag_of_Bangladesh.svg.png" },
    { "country":  "belarus", "geoName": "Belarus", "cities": ["minsk", "gomel", "grodno", "mogilev", "brest"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/85/Flag_of_Belarus.svg" },
    { "country":  "belgium", "geoName": "Belgium", "cities": ["antwerp", "brussels", "ghent", "bruges", "leuven", "liège", "namur"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/6/65/Flag_of_Belgium.svg" },
    { "country":  "benin", "geoName": "Benin", "cities": ["cotonou", "porto-novo", "parakou", "kandi", "abomey-calavi"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/0a/Flag_of_Benin.svg" },
    { "country":  "bhutan", "geoName": "Bhutan", "cities": ["thimphu", "phuntsholing", "phuntsholing", "gelephu"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/91/Flag_of_Bhutan.svg" },
    { "country":  "bolivia", "geoName": "Bolivia", "cities": ["la-paz", "cochabamba", "santa-cruz-de-la-sierra", "sucre", "el-alto"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/b/b3/Bandera_de_Bolivia_%28Estado%29.svg" },
    { "country":  "bosnia and herzegovina", "geoName": "Bosnia and Herz.", "cities": ["sarajevo", "mostar", "tuzla", "zenica", "brčko"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/b/bf/Flag_of_Bosnia_and_Herzegovina.svg" },
    { "country":  "botswana", "geoName": "Botswana", "cities": ["gaborone", "francistown", "maun", "serowe", "molepolole"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/fa/Flag_of_Botswana.svg" },
    { "country":  "brazil", "geoName": "Brazil", "cities": ["rio-de-janeiro", "são-paulo", "manaus", "brasilia", "fortaleza", "belém", "goiânia", "belo-horizonte", "Curitiba"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/0/05/Flag_of_Brazil.svg" },
    { "country":  "bulgaria", "geoName": "Bulgaria", "cities": ["sofia", "varna", "plovdiv", "ruse", "stara-zagora"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/9a/Flag_of_Bulgaria.svg" },
    { "country":  "burkina faso", "geoName": "Burkina Faso", "cities": ["ouagadougou", "bobo-dioulasso", "koudougou", "banfora", "ouahigouya"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/3/31/Flag_of_Burkina_Faso.svg" },
    { "country":  "burundi","geoName": "Burundi", "cities": ["bujumbura", "gitega", "muyinga", "ruyigi", "ngozi"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/5/50/Flag_of_Burundi.svg" },
    { "country":  "cambodia", "geoName": "Cambodia", "cities": ["phnom-penh", "siem-reap", "preah-sihanouk", "krong-battambang", "krong-ta-khmau"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/83/Flag_of_Cambodia.svg" },
    { "country":  "cameroon", "geoName": "Cameroon", "cities": ["yaoundé", "douala", "kumba", "bamenda", "garoua", "ngaoundere"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/4f/Flag_of_Cameroon.svg" },
    { "country":  "canada","geoName": "Canada", "cities": ["toronto", "montreal", "vancouver", "calgary", "edmonton", "quebec-city", "winnipeg", "saskatoon", "regina"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/d9/Flag_of_Canada_%28Pantone%29.svg" },
    { "country":  "chad", "geoName": "Chad", "cities": ["n'djamena", "moundou", "sarh", "abeche"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/4b/Flag_of_Chad.svg" },
    { "country":  "chile", "geoName": "Chile", "cities": ["santiago", "valparaíso", "viña-del-mar", "arica", "temuco", "concepcion", "puerto-montt"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/7/78/Flag_of_Chile.svg" },
    { "country":  "china", "geoName": "China", "cities": ["beijing", "shanghai", "guangzhou", "shenzhen", "chongqing", "chengdu", "harbin", "tianjin"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/fa/Flag_of_the_People%27s_Republic_of_China.svg" },
    { "country":  "hong kong", "geoName": "Hong Kong", "cities": ["hong-kong", "kowloon"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/5/5b/Flag_of_Hong_Kong.svg" },
    { "country":  "taiwan", "geoName": "Taiwan", "cities": ["taipei", "kaohsiung", "tainan", "taichung "], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/7/72/Flag_of_the_Republic_of_China.svg" },
    { "country":  "colombia", "geoName": "Colombia", "cities": ["bogotá", "medellín", "cali", "cartagena", "barranquilla"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/2/21/Flag_of_Colombia.svg" },
    { "country":  "congo", "geoName": "Congo", "cities": ["brazzaville", "pointe-noire"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/92/Flag_of_the_Republic_of_the_Congo.svg" },
    { "country":  "croatia", "geoName": "Croatia", "cities": ["zagreb", "split", "dubrovnik", "rijeka", "osijek", "zadar"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/1/1b/Flag_of_Croatia.svg" },
    { "country":  "cyprus", "geoName": "Cyprus", "cities": ["nicosia", "limassol", "larnaca", "paphos", "paralimni", "famagusta"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/d4/Flag_of_Cyprus.svg" },
    { "country":  "czechia", "geoName": "Czechia", "cities": ["prague", "brno", "ostrava", "pilsen", "olomouc"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/c/cb/Flag_of_the_Czech_Republic.svg" },
    { "country":  "denmark", "geoName": "Denmark", "cities": ["copenhagen", "aarhus", "aalborg", "odense", "esbjerg", "kolding"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/9c/Flag_of_Denmark.svg" },
    { "country":  "dominican republic", "geoName": "Dominican Rep.", "cities": ["santo-domingo", "puerto-plata", "san-pedro-de-macoris", "santiago-de-los-caballeros", "higuey"], "imageUrl": "https://en.wikipedia.org/wiki/File:Flag_of_the_Dominican_Republic.svg" },
    { "country":  "ecuador", "geoName": "Ecuador", "cities": ["quito", "guayaquil", "cuenca", "ambato", "manta"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/e/e8/Flag_of_Ecuador.svg" },
    { "country":  "egypt", "geoName": "Egypt", "cities": ["cairo", "luxor", "alexandria", "giza", "aswan"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/fe/Flag_of_Egypt.svg" },
    { "country":  "el salvador", "geoName": "El Salvador", "cities": ["san-salvador", "san-miguel", "santa-ana", "santa-tecla", "san-martin"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/3/34/Flag_of_El_Salvador.svg" },
    { "country":  "estonia", "geoName": "Estonia", "cities": ["tallinn", "tartu", "pärnu", "narva", "kohtla-järve"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/8f/Flag_of_Estonia.svg" },
    { "country":  "ethiopia", "geoName": "Ethiopia", "cities": ["addis-ababa", "dire-dawa", "dire-dawa", "hawassa", "dessie"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/7/71/Flag_of_Ethiopia.svg" },
    { "country":  "finland", "geoName": "Finland", "cities": ["helsinki", "tampere", "oulu", "espoo", "vantaa"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/b/bc/Flag_of_Finland.svg" },
    { "country":  "france", "geoName": "France", "cities": ["paris", "marseille", "lyon", "bordeaux", "toulouse", "strasbourg", "nice", "nantes", "montpellier", "lille"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/c/c3/Flag_of_France.svg" },
    { "country":  "georgia", "geoName": "Georgia", "cities": ["tbilisi", "batumi", "kutaisi", "rustavi"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/0f/Flag_of_Georgia.svg" },
    { "country":  "germany", "geoName": "Germany", "cities": ["berlin", "munich", "hamburg", "cologne", "hamburg", "düsseldorf", "stuttgart", "dresden"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/b/ba/Flag_of_Germany.svg" },
    { "country":  "ghana", "geoName": "Ghana", "cities": ["accra", "kumasi", "sekondi-takoradi", "sunyani", "tamale", "obuasi"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/1/11/Ghana_Flag.svg" },
    { "country":  "greece", "geoName": "Greece", "cities": ["athens", "thessaloniki", "patras", "heraklion", "ioannina", "pireas", "volos", "agrinio"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/5/5c/Flag_of_Greece.svg" },
    { "country":  "guatemala", "geoName": "Guatemala", "cities": ["guatemala-city", "antigua-guatemala", "quetzaltenango", "chichicastenango", "villa-nueva", "totonicapán"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/e/ec/Flag_of_Guatemala.svg" },
    { "country":  "honduras", "geoName": "Honduras", "cities": ["tegucigalpa", "san-pedro-sula", "la-ceiba", "comayagua", "puerto-cortes", "choluteca", "el-progreso", "danli", "choloma"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/82/Flag_of_Honduras.svg" },
    { "country":  "hungary", "geoName": "Hungary", "cities": ["budapest", "debrecen", "szeged", "miskolc", "pécs", "győr"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/c/c1/Flag_of_Hungary.svg" },
    { "country":  "iceland", "geoName": "Iceland", "cities": ["reykjavík", "hafnarfjordur", "kópavogur", "reykjanesbær", "akureyri"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/c/ce/Flag_of_Iceland.svg" },
    { "country":  "india", "geoName": "India", "cities": ["mumbai", "bengaluru", "chennai", "ahmedabad", "pune", "kolkata", "hyderabad", "new-delhi", "lucknow", "jaipur"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/4/41/Flag_of_India.svg" },
    { "country":  "indonesia", "geoName": "Indonesia", "cities": ["jakarta", "bandung", "surabaya", "makassar", "medan", "semarang", "palembang", "depok"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/9f/Flag_of_Indonesia.svg" },
    { "country":  "iran", "geoName": "Iran", "cities": ["tehran", "isfahan", "tabriz", "shiraz", "mashhad", "qom"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/c/ca/Flag_of_Iran.svg" },
    { "country":  "iraq", "geoName": "Iraq", "cities": ["baghdad", "mosul", "basra", "erbil", "najaf"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/f6/Flag_of_Iraq.svg" },
    { "country":  "ireland", "geoName": "Ireland", "cities": ["dublin", "galway", "cork", "waterford", "limerick"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/45/Flag_of_Ireland.svg" },
    { "country":  "israel", "geoName": "Israel", "cities": ["jerusalem", "tel-aviv", "haifa", "lod", "be'er-sheva", "ashkelon", "bat-yam", "netanya"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/d4/Flag_of_Israel.svg" },
    { "country":  "italy", "geoName": "Italy", "cities": ["rome", "venice", "florence", "turin", "milan", "naples", "bologna", "genoa"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/0/03/Flag_of_Italy.svg" },
    { "country":  "jamaica", "geoName": "Jamaica", "cities": ["kingston", "montego-bay", "ocho-rios", "port-antonio"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/0a/Flag_of_Jamaica.svg" },
    { "country":  "japan", "geoName": "Japan", "cities": ["tokyo"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/9/9e/Flag_of_Japan.svg" },
    { "country":  "jordan", "geoName": "Jordan", "cities": ["amman", "aqaba", "zarqa", "mafraq", "jerash", "irbid"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/c/c0/Flag_of_Jordan.svg" },
    { "country":  "kazakhstan", "geoName": "Kazakhstan", "cities": ["almaty", "shymkent", "karagandy", "taraz", "nursultan", "pavlodar", "oskemen", "semey", "aktobe", "kostanay"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/d3/Flag_of_Kazakhstan.svg" },
    { "country":  "kenya", "geoName": "Kenya", "cities": ["nairobi", "mombasa", "kisumu", "nakuru", "eldoret"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/49/Flag_of_Kenya.svg" },
    { "country":  "kuwait", "geoName": "Kuwait", "cities": ["kuwait-city", "al-jahra", "mangaf", "salmiya"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/a/aa/Flag_of_Kuwait.svg" },
    { "country":  "laos", "geoName": "Laos", "cities": ["vientiane"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/5/56/Flag_of_Laos.svg" },
    { "country":  "latvia", "geoName": "Latvia", "cities": ["riga", "daugavpils", "liepāja", "jūrmala", "ventspils", "jelgava", "cēsis"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/84/Flag_of_Latvia.svg" },
    { "country":  "lithuania", "geoName": "Lithuania", "cities": ["vilnius", "kaunas", "klaipėda", "siauliai", "panevėžys", "alytus"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/1/11/Flag_of_Lithuania.svg" },
    { "country":  "luxembourg", "geoName": "Luxembourg", "cities": ["luxembourg", "echternach", "esch-sur-alzette", "pétange"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/da/Flag_of_Luxembourg.svg" },
    { "country":  "madagascar", "geoName": "Madagascar", "cities": ["antananarivo", "toamasina", "mahajanga", "antsirabe"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/b/bc/Flag_of_Madagascar.svg" },
    { "country":  "malawi", "geoName": "Malawi", "cities": ["lilongwe", "blantyre", "mzuzu", "zomba", "karonga"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/d1/Flag_of_Malawi.svg" },
    { "country":  "malaysia", "geoName": "Malaysia", "cities": ["kuala-lumpur", "malacca-city", "kuching", "ipoh", "johor-bahru"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/6/66/Flag_of_Malaysia.svg" },
    { "country":  "maldives", "geoName": "Maldives", "cities": ["malé", "addu-city"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/0f/Flag_of_Maldives.svg" },
    { "country":  "mali", "geoName": "Mali", "cities": ["bamako", "timbuktu", "segou", "mopti"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/92/Flag_of_Mali.svg" },
    { "country":  "malta", "geoName": "Malta", "cities": ["valletta", "sliema", "saint-pauls-bay"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/7/73/Flag_of_Malta.svg" },
    { "country":  "mauritania", "geoName": "Mauritania", "cities": ["nouakchott", "nouadhibou", "atar", "rosso"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/43/Flag_of_Mauritania.svg" },
    { "country":  "mauritius", "geoName": "Mauritius", "cities": ["port-louis", "curepipe", "vacoas-phoenix", "beau-bassin-rose-hill"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/7/77/Flag_of_Mauritius.svg" },
    { "country":  "mexico", "geoName": "Mexico", "cities": ["mexico-city", "guadalajara", "puebla", "ciudad-juárez", "tijuana", "monterrey", "mexicali"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/fc/Flag_of_Mexico.svg" },
    { "country":  "moldova", "geoName": "Moldova", "cities": ["chișinău", "tiraspol"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/2/27/Flag_of_Moldova.svg" },
    { "country":  "mongolia", "geoName": "Mongolia", "cities": ["ulaanbaatar", "ulaangom"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/4c/Flag_of_Mongolia.svg" },
    { "country":  "montenegro", "geoName": "Montenegro", "cities": ["podgorica", "nikšić"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/6/64/Flag_of_Montenegro.svg" },
    { "country":  "morocco", "geoName": "Morocco", "cities": ["casablanca", "tangier", "marrakesh", "meknes", "rabat", "fes"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/2/2c/Flag_of_Morocco.svg" },
    { "country":  "mozambique ", "geoName": "Mozambique", "cities": ["maputo", "beira", "quelimane", "chimoio", "matola", "nacala"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/d0/Flag_of_Mozambique.svg" },
    { "country":  "myanmar", "geoName": "Myanmar", "cities": ["yangon", "mandalay", "naypyitaw", "bago", "mawlamyine", "taunggyi"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/8c/Flag_of_Myanmar.svg" },
    { "country":  "namibia", "geoName": "Namibia", "cities": ["windhoek", "swakopmund", "walvis-bay", "otjiwarongo"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/00/Flag_of_Namibia.svg" },
    { "country":  "nepal", "geoName": "Nepal", "cities": ["kathmandu", "pokhara", "lalitpur", "bharatpur", "biratnagar", "birgunj", "janakpur", "hetauda"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/9b/Flag_of_Nepal.svg" },
    { "country":  "netherlands", "geoName": "Netherlands", "cities": ["amsterdam", "the-hague", "rotterdam", "utrecht", "groningen", "eindhoven"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/2/20/Flag_of_the_Netherlands.svg" },
    { "country":  "new zealand", "geoName": "New Zealand", "cities": ["auckland", "wellington", "christchurch", "dunedin"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/3/3e/Flag_of_New_Zealand.svg" },
    { "country":  "nicaragua", "geoName": "Nicaragua", "cities": ["managua", "leon", "granada", "masaya", "esteli"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/1/19/Flag_of_Nicaragua.svg" },
    { "country":  "nigeria", "geoName": "Nigeria", "cities": ["lagos", "ibadan", "abuja", "port-harcourt", "benin-city", "ilorin", "kano"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/7/79/Flag_of_Nigeria.svg" },
    { "country":  "norway", "geoName": "Norway", "cities": ["oslo", "bergen", "trondheim", "stavanger"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/d9/Flag_of_Norway.svg" },
    { "country":  "oman", "geoName": "Oman", "cities": ["muscat", "salalah", "nizwa", "sohar", "seeb"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/d/dd/Flag_of_Oman.svg" },
    { "country":  "pakistan", "geoName": "Pakistan", "cities": ["islamabad", "karachi", "lahore", "faisalabad", "peshawar"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/3/32/Flag_of_Pakistan.svg" },
    { "country":  "palestine", "geoName": "Palestine", "cities": ["gaza", "khan-yunis", "jabalia ", "hebron", "nablus"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/00/Flag_of_Palestine.svg" },
    { "country":  "panama", "geoName": "Panama", "cities": ["panama-city", "tocumen"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/a/ab/Flag_of_Panama.svg" },
    { "country":  "paraguay", "geoName": "Paraguay", "cities": ["asunción ", "ciudad-del-este", "encarnacion", "luque-paraguay"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/2/27/Flag_of_Paraguay.svg" },
    { "country":  "peru", "geoName": "Peru", "cities": ["lima ", "arequipa", "cusco", "chiclayo", "huancayo", "piura"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/c/cf/Flag_of_Peru.svg" },
    { "country":  "philippines", "geoName": "Philippines", "cities": ["manila", "quezon-city", "davao-city", "cebu-city", "makati", "baguio"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/9/99/Flag_of_the_Philippines.svg" },
    { "country":  "poland", "geoName": "Poland", "cities": ["warsaw", "kraków", "wrocław", "gdańsk", "poznań"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/1/12/Flag_of_Poland.svg" },
    { "country":  "portugal", "geoName": "Portugal", "cities": ["lisbon", "porto", "braga", "coimbra"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/5/5c/Flag_of_Portugal.svg" },
    { "country":  "qatar", "geoName": "Qatar", "cities": ["doha"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/6/65/Flag_of_Qatar.svg" },
    { "country":  "romania", "geoName": "Romania", "cities": ["bucharest", "constanța"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/7/73/Flag_of_Romania.svg" },
    { "country":  "russia", "geoName": "Russia", "cities": ["moscow", "saint-petersburg", "yekaterinburg", "novosibirsk", "kazan", "omsk", "volgograd", "chelyabinsk", "krasnoyarsk"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/f/f3/Flag_of_Russia.svg" },
    { "country":  "rwanda", "geoName": "Rwanda", "cities": ["kigali"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/1/17/Flag_of_Rwanda.svg" },
    { "country":  "saudi arabia", "geoName": "Saudi Arabia", "cities": ["riyadh", "jeddah", "mecca", "medina", "khamismushait", "dammam", "abha"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/0d/Flag_of_Saudi_Arabia.svg" },
    { "country":  "senegal", "geoName": "Senegal", "cities": ["dakar"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/fd/Flag_of_Senegal.svg" },
    { "country":  "serbia", "geoName": "Serbia", "cities": ["belgrade"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/ff/Flag_of_Serbia.svg" },
    { "country":  "sierra leone", "geoName": "Sierra Leone", "cities": ["freetown"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/1/17/Flag_of_Sierra_Leone.svg" },
    { "country":  "singapore", "geoName": "Singapore", "cities": ["singapore"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/48/Flag_of_Singapore.svg" },
    { "country":  "slovakia", "geoName": "Slovakia", "cities": ["bratislava", "košice"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/e/e6/Flag_of_Slovakia.svg" },
    { "country":  "slovenia", "geoName": "Slovenia", "cities": ["ljubljana", "maribor", "koper", "kranj", "celje"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/f0/Flag_of_Slovenia.svg" },
    { "country":  "south africa", "geoName": "South Africa", "cities": ["cape-town", "johannesburg", "durban", "pretoria", "soweto"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/a/af/Flag_of_South_Africa.svg" },
    { "country":  "south korea", "geoName": "South Korea", "cities": ["seoul", "busan", "incheon", "daegu", "ulsan", "daejeon"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/09/Flag_of_South_Korea.svg" },
    { "country":  "spain", "geoName": "Spain", "cities": ["madrid", "barcelona", "seville", "valencia ", "bilbao"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/89/Bandera_de_España.svg" },
    { "country":  "sri lanka", "geoName": "Sri Lanka", "cities": ["colombo", "kandy", "gampaha", "galle", "jaffna", "matara"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Flag_of_Sri_Lanka.svg/800px-Flag_of_Sri_Lanka.svg.png" },
    { "country":  "sudan", "geoName": "Sudan", "cities": ["khartoum", "omdurman"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/01/Flag_of_Sudan.svg" },
    { "country":  "sweden", "geoName": "Sweden", "cities": ["stockholm", "gothenburg", "uppsala", "helsingborg"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/4/4c/Flag_of_Sweden.svg" },
    { "country":  "switzerland", "geoName": "Switzerland", "cities": ["zürich", "geneva", "basel", "lausanne"], "imageUrl": "https://en.wikipedia.org/wiki/Switzerland#/media/File:Flag_of_Switzerland.svg" },
    { "country":  "syria", "geoName": "Syria", "cities": ["damascus", "aleppo", "homs", "latakia"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/5/53/Flag_of_Syria.svg" },
    { "country":  "tanzania", "geoName": "Tanzania", "cities": ["dar-es-salaam", "mwanza", "dodoma", "mbeya"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/3/38/Flag_of_Tanzania.svg" },
    { "country":  "thailand", "geoName": "Thailand", "cities": ["bangkok", "chiang-mai", "phuket", "pattaya"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/a/a9/Flag_of_Thailand.svg" },
    { "country":  "tunisia", "geoName": "Tunisia", "cities": ["tunis", "sfax", "sousse", "kairouan"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/c/ce/Flag_of_Tunisia.svg" },
    { "country":  "turkey", "geoName": "Turkey", "cities": ["istanbul", "ankara", "izmir", "konya", "gaziantep", "adana"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/b/b4/Flag_of_Turkey.svg" },
    { "country":  "uganda", "geoName": "Uganda", "cities": ["kampala"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/4e/Flag_of_Uganda.svg" },
    { "country":  "ukraine", "geoName": "Ukraine", "cities": ["kyiv", "lviv", "kharkiv", "odesa"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/4/49/Flag_of_Ukraine.svg" },
    { "country":  "united arab emirates", "geoName": "United Arab Emirates", "cities": ["dubai", "sharjah", "ajman"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/c/cb/Flag_of_the_United_Arab_Emirates.svg" },
    { "country":  "united kingdom", "geoName": "United Kingdom", "cities": ["london", "birmingham", "edinburgh", "manchester", "glasgow", "liverpool", "bristol"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/a/ae/Flag_of_the_United_Kingdom.svg" },
    { "country":  "united states", "geoName": "United States of America", "cities": ["new-york", "chicago", "los-angeles", "san-francisco", "austin", "seattle"], "imageUrl": "https://upload.wikimedia.org/wikipedia/en/a/a4/Flag_of_the_United_States.svg" },
    { "country":  "uruguay", "geoName": "Uruguay", "cities": ["montevideo"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/f/fe/Flag_of_Uruguay.svg" },
    { "country":  "uzbekistan", "geoName": "Uzbekistan", "cities": ["samarkand", "tashkent"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/84/Flag_of_Uzbekistan.svg" },
    { "country":  "venezuela", "geoName": "Venezuela", "cities": ["caracas", "maracay", "maracaibo", "guayana-city"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/06/Flag_of_Venezuela.svg" },
    { "country":  "vietnam", "geoName": "Vietnam", "cities": ["ho-chi-minh-city", "hanoi", "da-nang", "can-tho", "haiphong"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/2/21/Flag_of_Vietnam.svg" },
    { "country":  "yemen", "geoName": "Yemen", "cities": [" sana'a"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/8/89/Flag_of_Yemen.svg" },
    { "country":  "zambia", "geoName": "Zambia", "cities": [" Lusaka"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/0/06/Flag_of_Zambia.svg" },
    { "country":  "zimbabwe", "geoName": "Zambia", "cities": ["harare", "bulawayo"], "imageUrl": "https://upload.wikimedia.org/wikipedia/commons/6/6a/Flag_of_Zimbabwe.svg" }
  ]
}
```
## 📦 Third party

- [@octokit/graphql](https://www.npmjs.com/package/@octokit/graphql) - Send GraphQL requests to GitHub API.
- [fs-extra](https://www.npmjs.com/package/fs-extra) - Creating directories and files.
- [simple-git](https://www.npmjs.com/package/simple-git) - Handling Git commands.
## 📄 License

- GitHub Action - [gayanvoice/top-github-users-action](https://github.com/gayanvoice/top-github-users-action)
- Repository - [gayanvoice/top-github-users](https://github.com/gayanvoice/top-github-users)
- Data in the `./cache` directory - [Open Database License](https://opendatacommons.org/licenses/odbl/1-0/)
- Code - [MIT](./LICENSE) © [Gayan Kuruppu](https://github.com/gayanvoice)
