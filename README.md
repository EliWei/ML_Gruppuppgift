# Marketplace Safety – ML-projekt

## Projektbeskrivning
Detta projekt handlar om att utveckla en maskininlärningsmodell som hjälper ett Trust & Safety-team att prioritera vilka aktiviteter på en marknadsplatsplattform som bör granskas först.

Varje rad i datan representerar en händelse (t.ex. annons eller meddelande). Modellen försöker förutsäga om händelsen är **misstänkt (`is_suspicious = 1`)** eller inte.

Målet är inte att få 100 % rätt, utan att skapa ett beslutsstöd som kan prioritera vilka fall som bör granskas manuellt.

---

# Hur man kör projektet

1. Klona repot

2. Öppna projektet i t.ex. VS Code eller Jupyter. Använd Python v 3.13

3. Installera beroenden (om de saknas):



4. Säkerställ att följande filer finns i projektmappen:
- `historical_data.csv`
- `new_data.csv`

5. Kör notebooken:



Notebooken kan köras från början till slut med **"Restart & Run All"**.

---

# Kravkort

**Stakeholder:** Customer Support (Lina, Customer Support Lead)

Customer Support får klagomål när legitima användare flaggas. Därför är det viktigt att modellen **minimerar onödiga flaggningar** och att de fall som flaggas känns rimliga och konsekventa.

Vår prioritet är därför att **hålla nere false positives och uppnå hög precision**, även om det innebär att vissa misstänkta fall missas.

---

# Strategi

Vi byggde en klassificeringspipeline som hanterar både numeriska och kategoriska features genom imputering, skalning och one-hot encoding.

Tre modeller jämfördes:
- DummyClassifier (baseline)
- Logistic Regression
- Random Forest

Logistic Regression valdes som slutlig modell eftersom den gav bäst precision enligt vårt kravkort.

Modellen optimerades med **GridSearchCV** där hyperparametrar som regularisering (`C`) och `class_weight` testades.

För att använda modellen i praktiken analyserade vi olika **threshold-värden** och valde en threshold på **0.4**. Detta gav en bra balans mellan att identifiera misstänkta fall och att undvika onödiga flaggningar.

---

# Ansvarsfördelning

| Ansvarsområde | Person |
|---|---|
| Data & EDA | Victoria |
| Pipeline & Preprocessing | Elisabeth |
| Modelljämförelse | Victoria |
| Optimering | Anarkoli |
| Threshold / Prioritering | Eliesa |
| Pitch & Risker | Daniel |