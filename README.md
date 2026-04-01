# Phishing Website Detection System

A machine learning-based web application that detects phishing websites in real time by analyzing URLs and returning a safety percentage.

Built as part of the B.Tech CSE Seminar at **Lovely Professional University, Punjab**.

---

## Demo

Enter any URL into the web interface and get an instant prediction:

- ✅ High % = Safe to visit
- ❌ Low % = Likely a phishing site

---

## How It Works

1. User enters a URL in the browser
2. The app extracts **30 features** from the URL
3. Features are passed to a trained **Gradient Boosting Classifier**
4. The model returns a safety probability score
5. Result is displayed as a percentage on screen

---

## Features Analyzed

The model checks 30 characteristics grouped into 4 categories:

| Category | Features |
|---|---|
| URL Structure | IP in URL, URL length, short URL, @ symbol, redirects, dash in domain, subdomains |
| Domain & Security | HTTPS, domain age, favicon source, non-standard port, HTTPS in domain name |
| Page Content | Request URLs, anchor links, script tags, form handlers, popups, iframes, right-click |
| External Reputation | Domain age, DNS record, web traffic, page rank, Google index, inbound links, blacklist |

---

## Tech Stack

| Technology | Purpose |
|---|---|
| Python 3.13 | Core language |
| Flask 2.0.2 | Web framework |
| scikit-learn | Gradient Boosting Classifier |
| pandas & numpy | Data processing |
| BeautifulSoup4 | HTML page analysis |
| requests | Fetching web pages |
| python-whois | Domain registration lookup |
| googlesearch-python | Google index check |
| pickle | Model serialization |

---

## Dataset

- **Source:** phishing.csv
- **Size:** 11,054 labeled URLs
- **Labels:** +1 (Legitimate), -1 (Phishing)
- **Features:** 30 per URL

---

## Model

- **Algorithm:** Gradient Boosting Classifier
- **Parameters:**
  - n_estimators = 30
  - max_depth = 4
  - learning_rate = 0.7
  - max_features = sqrt

---

## Installation and Running

### Step 1 — Clone the repository
```bash
git clone https://github.com/Somashekhar-peddinti/PhishingWebsite.git
cd PhishingWebsite
```

### Step 2 — Install dependencies
```bash
pip install -r requirements.txt
pip install python-whois
```

### Step 3 — Run the app
```bash
python app.py
```

### Step 4 — Open in browser
```
http://127.0.0.1:5000
```

---

## Project Structure
```
PhishingWebsite/
│
├── app.py                        # Flask web application
├── feature.py                    # 30-feature extraction module
├── phishing.csv                  # Training dataset
├── Phishing URL Detection.ipynb  # Model training notebook
├── requirements.txt              # Python dependencies
├── pickle/
│   └── model.pkl                 # Trained ML model
├── templates/
│   └── index.html                # Frontend web page
└── static/
    └── styles.css                # Stylesheet
```

---

## Test URLs

| URL | Expected Result |
|---|---|
| https://google.com | Safe |
| https://github.com | Safe |
| https://youtube.com | Safe |
| http://192.168.1.1/login | Suspicious |
| http://paypal-secure-login.com | Suspicious |

---

## Known Issues Fixed

- Removed pinned `numpy==1.21.4` — incompatible with Python 3.13
- Updated `pandas` version — 1.3.4 fails on Python 3.13
- Replaced `scikit-learn==1.0.1` — `numpy.distutils` removed in Python 3.13
- Downgraded `Werkzeug` to 2.0.3 — Flask 2.0.2 incompatible with Werkzeug 3.x
- Retrained model with correct 30 features — excluded Index column from dataset
- Added `python-whois` — missing from original requirements

---

## Author

**Somashekhar Peddinti**
Registration No. 12221722
B.Tech CSE — Lovely Professional University, Punjab

GitHub: [Somashekhar-peddinti](https://github.com/Somashekhar-peddinti)

---

## Acknowledgements

- Dataset based on research by Mohammad, R. M., Thabtah, F., & McCluskey, L. (2015)
- Lovely Professional University, Punjab
- 
