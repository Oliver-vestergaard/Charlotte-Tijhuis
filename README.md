# Teknisk Dokumentation: Tema10, Gruppe9, Guldsmed Charlotte Tijhuis

## Om projektet:

MMD - 2. semester, Tema 10 - Eksamens Projekt.
I dette projekt udvikles et redesign af Guldsmed Charlotte Tijhuis website. Projektet omfatter både et kodet website, API udvikling og anvendelse, indholdsproduktion og SoMe materiale.


Løsningen udvikles i programmet Astro, der har den fordel at gøre det lettere at samarbejde om udviklingen af koden da Astro understøtter “Komponenter” . 

I løsningen gøres der også brug af vores eget API, som er udviklet i SupaBase. Her udtrækkes relevant information om Produkter såsom: Produkt navn, information om produktet, pris og billeder af produktet. 
Disse hentes ind, i productlist.astro samt productDetails.astro og sørger for at der nemt og overskueligt kan tilføjes flere produkter til samlingen.

## Projekt mappe opsætning:
``` 
Charlotte-Tijhuis

├── dist

├── public/
│   └── img
│       ├── hoverimg
│       │   └── Product hover imgs
│       └── Product imgs
│
│   ├── favicon
│   ├── Logo.svg
│   └── ForsideVideo
│
├── src/
│   ├── assets
│   │   ├── imgBohippie
│   │   ├── imgFooter
│   │   ├── imgForside
│   │   ├── imgIndex
│   │   ├── imgMenu
│   │   ├── imgOmOs
│   │   ├── imgProductDetails
│   │   └── imgProductList
│
│   ├── components
│   │   ├── Accordion.astro
│   │   ├── Card.astro
│   │   ├── CardButton.astro
│   │   ├── CtaButton.astro
│   │   ├── Footer.astro
│   │   ├── KategoriMenu.astro
│   │   ├── KortFormboks.astro
│   │   ├── LangFormboks.astro
│   │   ├── Menu.astro
│   │   ├── ProductCard.astro
│   │   ├── SocialMedia.astro
│   │   └── SortButton.astro
│
│   ├── layout
│   │   └── Layout.astro
│
│   ├── pages
│   │   ├── index.astro
│   │   ├── forside.astro
│   │   ├── productList
│   │   │   ├── armband.astro
│   │   │   ├── halskaede.astro
│   │   │   ├── herre.astro
│   │   │   ├── orering.astro
│   │   │   └── ring.astro
│   │   │
│   │   ├── productDetails
│   │   │   └── [id].astro
│   │   │
│   │   ├── OmOs.astro
│   │   ├── bohippie.astro
│   │   └── kontakt.astro
│
│   └── styles
│       └── global.css
│
├── .env
├── .gitignore
└── README.md
```

## Installation af Astro Projekt: 
Når man starter et Astro projekt gøres det af et gruppemedlem. Denne person uploader projektet til et Github repository og invitere de resterende gruppe medlemmer som udfører følgende.

- Accepter anmodningen om samarbejde. 
- Klon repository fra github og indsæt i Vscode. 
- Gem mappen i roden af computeren. 
- Åben terminalen og kør “npm install” 
- Lav en branch og start på din feature.

## Filbeskrivelser 
### alle astro pages

- index.astro - Fungerer som landingpage og introducerer brugeren til universet og brandidentiteten.
- forside.astro - Primær forside.
- omOs.astro - Fortæller om designeren og brandets historie
- productList.astro - Oversigt over alle produkter fra API
- armband.astro - Oversigt over smykker med kategorien “armband” fra API
- halskeade.astro - Oversigt over smykker med kategorien “halskeade” fra API
- herre.astro - Oversigt over smykker med kategorien “herre” fra API
- orering.astro - Oversigt over smykker med kategorien “orering” fra API
- ring.astro- Oversigt over smykker med kategorien “ring” fra API
- productDetails/[id].astro - Detaljeret produktside samt reservere sin ordre
- kontakt.astro - kontakt og reservationsformular
- bohíppie.astro - galleri og sekundært smykkeprojekt




### Alle Astro Components filer:
- Accordion.astro - Bruges på productDetails
- Card.astro - bruges på forside og omOs
- CardButton.astro - bruges i Card.astro
- CtaButton.astro - Bruges på forsiden og productDetails
- Footer.astro - Bruges i Layout
- KategoriMenu.astro - bruges i Menu
- KortFormbox.astro - bruges på Kontakt
- LangFormboks.astro - bruges på kontakt
- Menu.astro - Bruges i Layout
- ProductCard.astro - bruges på productList
- SocialMedia.astro - bruges i footer og kontakt
- SortButton.astro - bruge på productList
- Layout.astro - bruges på alle astro.pages, med undtagelse af index.astro

### .env
- Denne fil indeholder en nøgle (“SUPABASE_PUBLISHABLE_KEY”) der skal bruges når man vil tilgå vores SupaBase Api.Derudover indeholder den også URL’en til vores Database.

### .gitignore
- Denne fil indeholder forskellige elementer der ikke skal uploades på github når der publishes en branch. Her i blandt er også .env, da nøglen ikke skal lægges op og være public. 


### dist
- Denne fil fungerer som en building mappe. Når Astro indhenter data fra et Api til en side omhandlende et enkelt produkt, som skal fungere dynamisk, bygger Astro alle siderne som Html sider og placerer dem i mappen dist. Dette gøres ved, i terminalen. at skrive: npm run build.


## Sådan fungerer koden
Koden fungerer ved at “importe” komponenter ind i omOs-osv. Astro 
Komponenterne er stylet i sin egen fil, hvilket er smart hvis farven, størrelsen eller andet, skal ændres alle steder komponenten er brugt. 

Alle astro.pages, med untagelse af index.astro, er bygget op i det samme layout. Dette fungerer på samme måde som komponenter. Da alle pages skal indeholde den samme menu, burger menu og footer, mindsker det sandsynligheden for at man overskriver en menu style på sin egen html side. Samtidig er det også smart hvis man skal ændre i menuen, da det her kun behøver at gøres 1 sted for at det retter sig på alle sider. 

Derudover har vi oprettet en global.css der er linket ind i layout komponenten. Denne fil indeholder styles på elementer der går igen på alle sider: 
- Fonts
- Reset (fjerner browserens default styles)  
- Farve variable

## Billede behandling: 
Astro indeholder et indbygget <Image/> tag der gør det nemmere at optimere og styre billeder. Igennem dette tag er det muligt at komprimere og optimere billeder samt ændre billedet til WebP formatet. 
Dette er af væsentlig betydning, da ikke-optimerede og komprimerede billeder har flere uhensigtsmæssige konsekvenser: 
- Gøre siden langsom at loade
- Bruge unødvendigt meget data på mobil
- Give dårlig brugeroplevelse
- Skade SEO-ranking

Det bruges ved at importere Images tagget i mellem fences: import { Image } from "astro:assets";

Dernæst importeres billeder fra assets mappen: import Ringe from "../assets/imgMenu/ring.png";

Dernæst kan det bruges i den ønskede størrelse, filformat, quality osv. 
< Image src={Ringe} width={} quality={} format="webP" alt="" /> 


## Navngivning: 
Vi har igennem projektet forsøgt at holde vores navngivning på mapper, filer, og branches, så kontinuerlig og tydelig som muligt.
 

### camelCase:
- Gør koden ensartet
- Gør koden lettere at læse


### Eksempler på kommentarer:
-  /*sort button js*/
-  /*højt til lavt*/
-  /*få al data i en ny array*/
-  /*sorter efter vores price "attribute"*/
- /*grid--> sorterer og placerer samme data bare efter pris*/
 - /* for at kunne klikke igen og sortere efter modsat*/

### Eksempler på branches:
- navigationMenu-Oliver
- Forside-begyndelse---Louise
- productList_fetch_Katrine
- bohippie3---Nynne



## SupaBase
Supabase er et program, der giver mulighed for at oprette og arbejde med en database. 
Vores data organiseres i tabeller med kolonner, som så kan hentes i projektet ved hjælp af fetch. Det gør det nemt at tilføje nyt indhold, da det blot skal oprettes i databasen og derefter automatisk kan vises på websitet.

### kolonner som vi bruger i denne opgave: (h3)
- smykkenavn
- pris
- kategori
- materiale
- beskrivelse
- lock
- produktimage
- produkthover

## Branches og hvordan de bruges: 
Hver gang man starter på et nyt element i koden oprettes en branch fra Master.  Dette gør det muligt at samarbejde om en kode uden at forstyrre hinandens arbejde og derved undgå merge conflicts. 


Når et element er færdig og virker, commites det og pushes til GitHub hvorefter ens ændringer merges ind i Master. Herefter skifter man, i VsCode, tilbage i Master, synkroniserer (push & pull), laver en ny branch hvorefter punkterne gentages.   

## Udfordringer undervejs 

- Eftersom vi i Layout allerede havde dedikeret en baggrundsfarve til body var det en udfordring at ændre dette til Bohippie siden. Det blev dog løst ved hjælp af Astro.props samt at give body en class der, hvis bruges på en side, skifter baggrundfarven til den ønskede hex-kode. 

- CardButton og SortButton har mange af de samme styles. Dog er en “wrapped” i et a-tag/href og den anden bruges som en sorterings knap ved hjælp af id. De er lavet seperat da der var nogle udfordringer med at få sorterings script til at virke på min originale CardButton. Dette blev løst da vi lavede to components i stedet.

- Før vi uploadede projektet til Netlify forsøgte vi at køre npm run build, men fik en fejl. Efter en længere debugging fandt vi frem til fejlen som var denne kode linje ``` export const prerender = false; ```
Problemet er at når man kører npm run build, bygger astro alle .pages op inden de bliver besøgt. Det vil sige at i og med vi laver Productlist og Details dynamisk, leder astro i Url’en efter kategori eller Id som ikke eksisterer endnu. Dette betyder at når vi fjerner den linje kode, der ses oppe oven over, læser astro det som om den skal vise alle produkter. 
Det betyder altså at når man trykker på Kategori menuen med eksempelvis ringe, viser astro alle produkterne.
En midlertidig løsning blev at lave en mappe i astro.pages hvor vi oprettede 5 nye pages: orering, armband, ring, halskaede og herre. i hver af disse pages, henter vi den enkelte kategori ved denne kode:  ``` params.set("select", "*");
params.set("kategori", "eq.armband");```
Derudover fjernede vi dette på productList ```if (kategori) {params.set("kategori", `eq.${kategori}`);} ``` Vores næste udfordring blev at sende det enkelte produkt fra productList ind i productDetails, dette blev også statisk i forbindelse med fjernelsen af koden: ´´´ export const prerender = false; ´´´
Astro tog nu kun det første product (id) og viste på siden. Vi var derfor nødt til at bede astro om at, inden siden bliver bygget, at hente alle id’er fra Supabase med tilføjelsen af ``` export async function getStaticPaths() ``` samt ændring af Url fra
 localhost:4321/productDetails?id=8
til
 localhost:4321/productDetails/8


### Mulige forbedringer
En forbedring i vores projekt kunne være en mere stabil løsning af overstående problem hvor man også kunne gøre kategori sectionen dynamisk og ikke behøver at oprette individuelle pages til hver kategori. 

En anden forbedring vi gerne ville have implementeret, var at gøre Kontakt.astro mere dynamisk, så produktnavn automatisk kunne overføres fra produktdetaljesiden til kontaktformularen.



## Gruppemedlemmer 
- Katrine
- Nynne
- Louise
- Oliver


