# Deník vývoje
**Pracovní název:** Možnosti a limity vibe codingu při tvorbě výukové aplikace o svalové soustavě člověka

### Záznamy:
- **Datum,čas** - *Pořadové číslo záznamu, datum a kolik času krok zabral*
- **Požadavek** - *Kterého požadavku se týká*
- **Prompt**
- **Odpověď AI***
- **Výsledek**
- **Co bylo potřeba potom**
- **Chyba**
- **Kategorie**
- **Commit**
  
# Záznam č. 1:
- **Datum,čas** - 8.11.
- **Požadavek** - SVG vs Canvas
- -> AI *chatgpt* vygeneruje malou ukázku 2-3 svalů pomocí obou technologií, podle kritérií (Jak snadné je označit jednotlivý sval, přesnost označení, jak vypadá po zvětšení, kolik práce dalo vytvoření) zhodnotit výhody a nevýhody.

## SVG
- **Prompt**
Vytvoř samostatnou webovou aplikaci v jednom HTML souboru, která pomocí SVG znázorňuje schematickou lidskou paži se třemi samostatnými svalovými oblastmi:

1. Biceps – dvojhlavý sval pažní.
2. Triceps – trojhlavý sval pažní.
3. Deltoid – deltový sval.

Požadavky:
- Každý sval musí být samostatný SVG element.
- Na každý sval musí být možné kliknout.
- Při najetí myší se sval barevně zvýrazní.
- Po kliknutí se zobrazí český název svalu.
- Vybraný sval zůstane zvýrazněný.
- Aplikace musí fungovat v běžném webovém prohlížeči.
- Nepoužívej externí knihovny.
- Vysvětli, jak funguje klikání na jednotlivé SVG elementy.

Vrať kompletní HTML kód, který lze uložit jako svg.html a otevřít přímo v prohlížeči.
- **Odpověď AI*** - 
<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interaktivní anatomie paže</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f6fa;
            margin: 0;
            padding: 30px;
            text-align: center;
            color: #263247;
        }

        h1 {
            margin-bottom: 10px;
        }

        .description {
            color: #68758a;
            margin-bottom: 25px;
        }

        .container {
            max-width: 650px;
            margin: auto;
            padding: 25px;
            background: white;
            border-radius: 18px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        }

        svg {
            width: 100%;
            max-width: 430px;
            height: auto;
        }

        /* Základní vzhled svalů */
        .muscle {
            fill: #e7a18e;
            stroke: #9e6255;
            stroke-width: 2.5;
            cursor: pointer;
            transition: fill 0.2s ease, opacity 0.2s ease;
        }

        /* Zvýraznění při najetí myší */
        .muscle:hover {
            fill: #f4a340;
        }

        /* Trvale vybraný sval */
        .muscle.selected {
            fill: #e85d75;
            stroke: #a52d49;
            stroke-width: 3.5;
        }

        /* Informace o vybraném svalu */
        #info {
            margin-top: 20px;
            padding: 18px;
            background: #f0f3f9;
            border-radius: 12px;
            min-height: 55px;
        }

        #muscleName {
            font-size: 21px;
            font-weight: bold;
            color: #304b78;
        }

        #muscleDescription {
            color: #68758a;
            margin-top: 8px;
        }

        .hint {
            font-size: 13px;
            color: #8993a3;
            margin-top: 18px;
        }
    </style>
</head>

<body>

    <h1>Interaktivní anatomie paže</h1>

    <p class="description">
        Kliknutím na sval zobrazíš jeho český název.
    </p>

    <div class="container">

        <svg viewBox="0 0 500 620"
             xmlns="http://www.w3.org/2000/svg"
             role="img"
             aria-label="Schematické znázornění lidské paže se třemi svaly">

            <!-- Silueta paže -->
            <path
                d="M 180,105
                   C 130,125 115,180 125,240
                   C 135,290 155,330 155,385
                   L 170,535
                   C 180,565 215,570 250,555
                   L 325,530
                   C 335,515 325,490 320,460
                   L 300,375
                   C 330,325 350,265 345,210
                   C 340,150 300,105 250,90
                   Z"
                fill="#f1c5ac"
                stroke="#b77d68"
                stroke-width="4"
            />

            <!-- DELTOID – deltový sval -->
            <path
                id="deltoid"
                class="muscle"
                data-name="Deltový sval (musculus deltoideus)"
                data-description="Deltový sval tvoří zaoblený tvar ramene. Pomáhá zvedat a pohybovat paží."
                d="M 180,105
                   C 205,65 280,65 310,115
                   C 340,155 335,205 305,235
                   C 280,210 240,205 205,230
                   C 175,200 155,150 180,105 Z"
            />

            <!-- BICEPS – dvojhlavý sval pažní -->
            <path
                id="biceps"
                class="muscle"
                data-name="Dvojhlavý sval pažní (musculus biceps brachii)"
                data-description="Biceps se nachází na přední straně paže. Jeho hlavní funkcí je ohýbání lokte a otáčení předloktí."
                d="M 205,230
                   C 225,210 270,205 295,235
                   C 310,265 305,315 290,355
                   C 280,380 265,395 250,390
                   C 225,385 205,350 195,315
                   C 185,275 185,250 205,230 Z"
            />

            <!-- TRICEPS – trojhlavý sval pažní -->
            <path
                id="triceps"
                class="muscle"
                data-name="Trojhlavý sval pažní (musculus triceps brachii)"
                data-description="Triceps se nachází na zadní straně paže. Jeho hlavní funkcí je natahování lokte."
                d="M 305,235
                   C 330,240 335,280 320,325
                   C 310,355 300,390 290,410
                   C 275,430 250,410 250,390
                   C 265,375 280,350 290,320
                   C 305,285 310,255 305,235 Z"
            />

            <!-- Popisky anatomických oblastí -->
            <g fill="#704f48" font-size="13" font-weight="bold"
               pointer-events="none">
                <text x="245" y="145" text-anchor="middle">RAMENO</text>
            </g>

        </svg>

        <!-- Informace po kliknutí -->
        <div id="info" aria-live="polite">
            <div id="muscleName">
                Vyber sval
            </div>

            <div id="muscleDescription">
                Klikni na jednu ze tří svalových oblastí.
            </div>
        </div>

        <p class="hint">
            Najeď myší na sval nebo na něj klikni.
        </p>

    </div>

    <script>

        // Vybereme všechny SVG elementy se třídou muscle
        const muscles = document.querySelectorAll(".muscle");

        // Najdeme informační pole
        const muscleName = document.getElementById("muscleName");
        const muscleDescription =
            document.getElementById("muscleDescription");

        // Přidáme každému svalu funkci pro kliknutí
        muscles.forEach(function(muscle) {

            muscle.addEventListener("click", function() {

                // Odstraníme zvýraznění ze všech svalů
                muscles.forEach(function(item) {
                    item.classList.remove("selected");
                });

                // Zvýrazníme právě vybraný sval
                muscle.classList.add("selected");

                // Zobrazíme jeho český název a popis
                muscleName.textContent = muscle.dataset.name;
                muscleDescription.textContent =
                    muscle.dataset.description;

            });

        });

    </script>

</body>
</html>

- **Výsledek** - Stranka se opravdu otevrela v prohlizeci, zaroven jdou zvolit presne jednotlive svaly, ktery se zvyrazni. Nevyhoda je ze svaly se prekryvaji a neni uplne zretelne z obrazku co to je.

## Canvas
- **Prompt**
- Vytvoř samostatnou webovou aplikaci v jednom HTML souboru, která pomocí Canvas znázorňuje schematickou lidskou paži se třemi samostatnými svalovými oblastmi:

1. Biceps – dvojhlavý sval pažní.
2. Triceps – trojhlavý sval pažní.
3. Deltoid – deltový sval.

Požadavky:
- Každý sval musí být samostatný element.
- Na každý sval musí být možné kliknout.
- Při najetí myší se sval barevně zvýrazní.
- Po kliknutí se zobrazí český název svalu.
- Vybraný sval zůstane zvýrazněný.
- Aplikace musí fungovat v běžném webovém prohlížeči.
- Nepoužívej externí knihovny.
- Vysvětli, jak funguje klikání na jednotlivé elementy.

Vrať kompletní HTML kód, který lze uložit jako Canvas.html a otevřít přímo v prohlížeči.
- **Odpoved AI**
  
<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interaktivní anatomie paže – Canvas</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f3f5f9;
            color: #263247;
            text-align: center;
            padding: 25px;
            margin: 0;
        }

        h1 {
            margin-bottom: 10px;
        }

        .description {
            color: #68758a;
            margin-bottom: 25px;
        }

        .container {
            max-width: 600px;
            margin: auto;
            padding: 25px;
            background: white;
            border-radius: 18px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
        }

        canvas {
            display: block;
            width: 100%;
            max-width: 450px;
            height: auto;
            margin: auto;
            cursor: default;
        }

        #info {
            margin-top: 20px;
            padding: 18px;
            background: #f0f3f9;
            border-radius: 12px;
            min-height: 65px;
        }

        #muscleName {
            font-size: 21px;
            font-weight: bold;
            color: #304b78;
        }

        #muscleDescription {
            color: #68758a;
            margin-top: 8px;
            line-height: 1.5;
        }

        .hint {
            color: #8993a3;
            font-size: 13px;
            margin-top: 18px;
        }
    </style>
</head>

<body>

    <h1>Interaktivní anatomie paže</h1>

    <p class="description">
        Klikni na jednotlivé svaly a zjisti jejich české názvy.
    </p>

    <div class="container">

        <canvas id="armCanvas" width="500" height="620">
            Váš prohlížeč nepodporuje Canvas.
        </canvas>

        <div id="info" aria-live="polite">
            <div id="muscleName">Vyber sval</div>

            <div id="muscleDescription">
                Najeď myší na sval nebo na něj klikni.
            </div>
        </div>

        <p class="hint">
            Oranžová barva = najetí myší.
            Růžová barva = vybraný sval.
        </p>

    </div>

    <script>

        // ==========================================
        // 1. PŘÍPRAVA CANVAS
        // ==========================================

        const canvas = document.getElementById("armCanvas");
        const ctx = canvas.getContext("2d");

        const muscleName = document.getElementById("muscleName");
        const muscleDescription =
            document.getElementById("muscleDescription");


        // ==========================================
        // 2. DEFINICE JEDNOTLIVÝCH SVALŮ
        // ==========================================

        const muscles = [

            {
                id: "deltoid",

                name: "Deltový sval (musculus deltoideus)",

                description:
                    "Deltový sval tvoří zaoblenou část ramene. " +
                    "Pomáhá při zvedání a pohybu paže.",

                path: new Path2D(
                    "M 180 105 " +
                    "C 205 65 280 65 310 115 " +
                    "C 340 155 335 205 305 235 " +
                    "C 280 210 240 205 205 230 " +
                    "C 175 200 155 150 180 105 Z"
                )
            },

            {
                id: "biceps",

                name: "Dvojhlavý sval pažní (musculus biceps brachii)",

                description:
                    "Biceps se nachází na přední straně paže. " +
                    "Jeho hlavní funkcí je ohýbání lokte " +
                    "a otáčení předloktí.",

                path: new Path2D(
                    "M 205 230 " +
                    "C 225 210 270 205 295 235 " +
                    "C 310 265 305 315 290 355 " +
                    "C 280 380 265 395 250 390 " +
                    "C 225 385 205 350 195 315 " +
                    "C 185 275 185 250 205 230 Z"
                )
            },

            {
                id: "triceps",

                name: "Trojhlavý sval pažní (musculus triceps brachii)",

                description:
                    "Triceps se nachází na zadní straně paže. " +
                    "Jeho hlavní funkcí je natahování lokte.",

                path: new Path2D(
                    "M 305 235 " +
                    "C 330 240 335 280 320 325 " +
                    "C 310 355 300 390 290 410 " +
                    "C 275 430 250 410 250 390 " +
                    "C 265 375 280 350 290 320 " +
                    "C 305 285 310 255 305 235 Z"
                )
            }

        ];


        // ==========================================
        // 3. STAV APLIKACE
        // ==========================================

        let hoveredMuscle = null;
        let selectedMuscle = null;


        // ==========================================
        // 4. VYKRESLENÍ PAŽE
        // ==========================================

        function drawArm() {

            // Vymazání předchozího vykreslení
            ctx.clearRect(0, 0, canvas.width, canvas.height);


            // Základní tvar lidské paže
            ctx.beginPath();

            ctx.moveTo(180, 105);

            ctx.bezierCurveTo(
                130, 125, 115, 180, 125, 240
            );

            ctx.bezierCurveTo(
                135, 290, 155, 330, 155, 385
            );

            ctx.lineTo(170, 535);

            ctx.bezierCurveTo(
                180, 565, 215, 570, 250, 555
            );

            ctx.lineTo(325, 530);

            ctx.bezierCurveTo(
                335, 515, 325, 490, 320, 460
            );

            ctx.lineTo(300, 375);

            ctx.bezierCurveTo(
                330, 325, 350, 265, 345, 210
            );

            ctx.bezierCurveTo(
                340, 150, 300, 105, 250, 90
            );

            ctx.closePath();

            ctx.fillStyle = "#f1c5ac";
            ctx.fill();

            ctx.strokeStyle = "#b77d68";
            ctx.lineWidth = 4;
            ctx.stroke();


            // Vykreslení každého svalu samostatně
            muscles.forEach(function(muscle) {

                let color = "#e7a18e";

                // Kontrola, zda je sval právě vybraný
                if (selectedMuscle === muscle) {
                    color = "#e85d75";
                }

                // Kontrola, zda je sval pod kurzorem
                else if (hoveredMuscle === muscle) {
                    color = "#f4a340";
                }

                ctx.fillStyle = color;
                ctx.strokeStyle = "#9e6255";
                ctx.lineWidth = 2.5;

                ctx.fill(muscle.path);
                ctx.stroke(muscle.path);

            });

        }


        // ==========================================
        // 5. ZJIŠTĚNÍ, NA KTERÝ SVAL MYŠ UKAZUJE
        // ==========================================

        function getMuscleAtPosition(x, y) {

            // Procházíme jednotlivé svaly
            for (let i = muscles.length - 1; i >= 0; i--) {

                const muscle = muscles[i];

                // Zjistíme, zda bod leží uvnitř tvaru
                if (ctx.isPointInPath(muscle.path, x, y)) {

                    return muscle;

                }

            }

            return null;

        }


        // ==========================================
        // 6. PŘEVOD SOUŘADNIC MYŠI
        // ==========================================

        function getCanvasPosition(event) {

            const rect = canvas.getBoundingClientRect();

            return {

                x: (event.clientX - rect.left) *
                    (canvas.width / rect.width),

                y: (event.clientY - rect.top) *
                    (canvas.height / rect.height)

            };

        }


        // ==========================================
        // 7. POHYB MYŠI – ZVÝRAZNĚNÍ SVALU
        // ==========================================

        canvas.addEventListener("mousemove", function(event) {

            const position = getCanvasPosition(event);

            hoveredMuscle = getMuscleAtPosition(
                position.x,
                position.y
            );

            canvas.style.cursor = hoveredMuscle
                ? "pointer"
                : "default";

            drawArm();

        });


        // ==========================================
        // 8. KLIKNUTÍ – VÝBĚR SVALU
        // ==========================================

        canvas.addEventListener("click", function(event) {

            const position = getCanvasPosition(event);

            const muscle = getMuscleAtPosition(
                position.x,
                position.y
            );

            if (muscle !== null) {

                selectedMuscle = muscle;

                muscleName.textContent = muscle.name;

                muscleDescription.textContent =
                    muscle.description;

            }

            drawArm();

        });


        // ==========================================
        // 9. ODJEZD MYŠI Z CANVAS
        // ==========================================

        canvas.addEventListener("mouseleave", function() {

            hoveredMuscle = null;

            drawArm();

        });


        // ==========================================
        // 10. PRVNÍ VYKRESLENÍ
        // ==========================================

        drawArm();

    </script>

</body>
</html>

- **Výsledek** Stejne jako SVG (Stranka se opravdu otevrela v prohlizeci, zaroven jdou zvolit presne jednotlive svaly, ktery se zvyrazni. Nevyhoda je ze svaly se prekryvaji a neni uplne zretelne z obrazku co to je.) Ale nevyhoda pri zvetseni dochazi ke ztrate kvality.
  
- **Co bylo potřeba potom**
- **Chyba**
- **Kategorie**
- **Commit**
