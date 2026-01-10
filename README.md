# Analyse des Domain Gaps bei der Pflanzenkrankheitserkennung

![Python](https://img.shields.io/badge/Python-3.12.3-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.16.2-orange)
![License](https://img.shields.io/badge/License-MIT-green)

Dieses Repository beinhaltet den Quellcode (als .ipynb), die KI-Modelle (als .keras) und die Analyse-Skripte zur Bachelorarbeit an der **IU Internationalen Hochschule**.

Das Projekt untersucht die Herausforderung, Deep-Learning-Modelle (basierend auf **EfficientNet-B0**), die auf kontrollierten Labordaten trainiert wurden, auf reale landwirtschaftliche Feldbedingungen zu übertragen. Der Fokus liegt auf der Quantifizierung des *Domain Gaps* und der Evaluierung verschiedener Trainingsstrategien zur Verbesserung der Generalisierung.

## 🎯 Forschungsfragen

Im Kern dieser Arbeit werden folgende vier Fragestellungen empirisch untersucht:

1.  **Quantifizierung des Domain Gaps:** Wie stark sinkt die Klassifikationsleistung des auf PlantVillage (Labordaten) trainierten Basismodells (**Modell A**) bei der Anwendung auf PlantDoc (Felddaten)?
2.  **Robustheit durch Augmentierung:** Wie stark verbessert eine domänen-agnostische Datenaugmentierungsstrategie (RandAugment) ohne aufwändiges Parameter-Tuning (**Modell B**) die Generalisierungsleistung auf PlantDoc im Vergleich zum Basismodell?
3.  **Dateneffizienz (Few-Shot vs. Full-Data):** Wie stark verbessert der Einsatz des vollständigen PlantDoc-Datensatzes (**Modell D**) die Modellleistung im Vergleich zum dateneffizienten Finetuning mit nur ca. 10 % der Daten (30 Bilder pro Klasse, **Modell C**)?
4.  **Erklärbarkeit (XAI):** Kann mithilfe von **Grad-CAM** qualitativ gezeigt werden, dass das Basismodell (A) stärker auf irrelevante Hintergrundmerkmale fokussiert, während die angepassten Modelle (B, C, D) zunehmend auf krankheitsspezifische Blattregionen achten?

## 🧪 Experimentelles Design & Modelle

Um die Forschungsfragen zu beantworten, wurden vier Modellvarianten implementiert:

| Modell | Strategie | Trainingsdaten | Ziel |
| :--- | :--- | :--- | :--- |
| **A** | Baseline | PlantVillage (Labor) | Messung der Referenzleistung & Domain Gap |
| **B** | Robustness | PlantVillage + **RandAugment** | Test der Generalisierung ohne Felddaten |
| **C** | Data-Efficient | PlantVillage (Weights) + **Few-Shot PlantDoc** | Test der Adaption bei Datenknappheit (30 img/cls) |
| **D** | High-Resource | PlantVillage (Weights) + **Full PlantDoc** | Referenz für maximale Performance (Upper Bound) |

## 📂 Datensätze

Das Projekt nutzt zwei primäre Datensätze, die vorverarbeitet und harmonisiert wurden:

* **Quelldomäne:** [PlantVillage](https://github.com/spMohanty/PlantVillage-Dataset) (Einzelblätter, neutraler Hintergrund)
* **Zieldomäne:** [PlantDoc-(Cropped)]([https://github.com/pratikkayal/PlantDoc-Object-Detection-Dataset]) (Reale Feldbedingungen, komplexer Hintergrund)

## 🛠️ Technologien & Setup

Die Implementierung erfolgte unter **Ubuntu 24.04 (WSL)** mit folgender Konfiguration:

* **Sprache:** Python 3.12.3
* **Frameworks:** TensorFlow 2.16.2, Keras
* **Libraries:** NumPy, Pandas, Scikit-learn, Matplotlib, Seaborn
* **Hardware:** Berechnungen durchgeführt auf NVIDIA GTX 1080 Ti.

## 📝 Zitation

Falls dieser Code für eigene Forschungszwecke genutzt wird, bitte wie folgt referenzieren:

> [Simmeth, Sandro]. (2025). *Pflanzenkrankheitserkennung mit Deep Learning: Ein interpretierba-rer Vergleich von Datenaugmentation und Finetuning zur daten-effizienten Überbrückung der „Lab-to-Field“-Domänenlücke*. Bachelorarbeit, IU Internationale Hochschule.

---
*Hinweis: Dies ist ein wissenschaftliches Repository zu Bildungszwecken.*
