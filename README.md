# PD App — Parkinson's Disease Detection App

A web-based tool that allows users to trace a spiral on a drawing canvas, then uses drawing metrics and a Naive Bayes classifier to predict the likelihood of Parkinson's Disease. Built as a final-year Computer Science project (COMP390).

> **Disclaimer:** This application is for research and testing purposes only. It is not a clinical diagnostic tool. Please consult a medical professional for any health concerns.

---

## Features

- Interactive spiral drawing pad (200×200 canvas)
- Compares user drawing to a reference spiral stored in Firebase Firestore
- Calculates three metrics:
  - **Line length** — total pixel distance drawn
  - **Match percentage** — similarity to the reference spiral
  - **Pen lifts** — number of times the pen left the canvas
- Predicts PD likelihood based on thresholds for all three metrics
- Optionally uploads drawing data to Firestore for dataset growth

---

## Files

| File | Description |
|---|---|
| `pdapp.html` | Main application — drawing interface and prediction logic |
| `ml2.py` | Angle-analysis utility for drawing point sequences |
| `mlupdater.py` | Trains a Naive Bayes classifier on collected drawing data |
| `predictiontable.xlsx` | Dataset of drawing submissions with labels |
| `new_drawing_data.xlsx` | Additional collected drawing data |
| `BGspiral.png` | Background spiral reference image shown on the canvas |

---

## Setup

### Running the app

1. Clone the repo
2. Set up a [Firebase](https://firebase.google.com/) project with Firestore enabled
3. In `pdapp.html`, replace the placeholder Firebase config values with your own credentials:
   ```js
   var firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
     ...
   };
   ```
4. Open `pdapp.html` in a browser (no build step needed)

### Training the ML model

Install dependencies:
```bash
pip install pandas scikit-learn openpyxl
```

Run the updater:
```bash
python mlupdater.py
```

---

## Resources

- [NHS — Parkinson's Disease](https://www.nhs.uk/conditions/parkinsons-disease/)
- [International Parkinson and Movement Disorder Society](https://www.movementdisorders.org/)
- [WHO — Parkinson Disease Fact Sheet](https://www.who.int/news-room/fact-sheets/detail/parkinson-disease)
- [Parkinson's Foundation — Global Care Network](https://www.parkinson.org/living-with-parkinsons/finding-care/global-care-network)
