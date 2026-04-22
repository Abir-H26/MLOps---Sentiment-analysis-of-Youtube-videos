# YouTube Sentiment Analyzer

> *What are people saying about EY on YouTube — and what does it reveal about their hiring brand?*

Every day, candidates across the world turn to YouTube to prepare for consulting interviews, share career experiences, and seek advice. But what does this content actually tell us about how EY is perceived as an employer?

This project automates that question. Built as an end-to-end MLOps pipeline, it collects YouTube comments and classifies them as **positive**, **negative**, or **neutral** in real time — delivered through a Chrome Extension you can run on any video.

---

## See It in Action

[![Watch the demo](thumbnail.png)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID)

> *One click. Instant sentiment.*

---

## Real Case: How Do Candidates Talk About EY on YouTube?

EY does not allow comments on its official YouTube channel — meaning public opinion about the firm can only be captured **indirectly**, through third-party content like career vlogs and interview coaching videos.

This makes for an interesting data science question: *what does candidate-generated content reveal about EY's employer brand?*

I analyzed three types of EY-related videos to find out.

---

### Video 1 — Authentic Career Interview
**["Life at EY: Finance Transformation with a Senior Consultant"](https://www.youtube.com/watch?v=U04WpvpuwkE)**

| Metric | Result |
|---|---|
| Comments analyzed | 3 |
| Dominant sentiment | 🟢 100% Positive |

**What the comments say:** Viewers respond with genuine enthusiasm — praising the conversation, asking for more career insights, and engaging with the guest's story.

**Limitation:** Only 3 comments were available, making this a weak statistical sample. However the tone is consistent and aligns with the video's authentic, personal nature.

---

###  Video 2 — EY Interview Coaching
**["EY Interview Questions and Answers (How To Pass!)"](https://www.youtube.com/watch?v=dskGPEq6GUQ)**

| Metric | Result |
|---|---|
| Comments analyzed | 173 |
| Dominant sentiment | ⚪ 85.6% Neutral · 🟢 12.1% Positive · 🔴 2.9% Negative |

**What the comments say:** Almost every comment follows the same pattern — a location and a role (*"EY India, Data Engineer"*, *"EY Toronto"*, *"EY London — Audit Associate"*). These are candidates from around the world, sharing the EY branch and role they are applying to in response to the host's call-to-action to receive tailored interview resources.

**Geographic reach:** India, Australia, Japan, Brazil, Switzerland, Ireland, Dubai, the UK, Canada, and across the US.

---

###  Video 3 — EY Video Interview Tips
**["How to Ace Your EY Video Interview: Insider Tips"](https://www.youtube.com/watch?v=qNTK9b_TQys)**

| Metric | Result |
|---|---|
| Comments analyzed | 21 |
| Dominant sentiment | ⚪ 71.4% Neutral · 🟢 28.6% Positive |

**What the comments say:** The same pattern repeats — candidates sharing their branch and target role (*"EY Vancouver, Canada — Assurance"*, *"EY Lagos, Nigeria"*, *"EY Denmark"*). The higher proportion of positive comments reflects a warmer tone, with some viewers expressing genuine gratitude for the content.

**Geographic reach:** Canada, Nigeria, Denmark, Finland, Malaysia, Dubai, Ireland, the UK, and the US.

---

###  Key Insight

> **Across two independent coaching videos, the same pattern emerges: candidates from every continent are actively seeking help to get into EY.**

The neutrality of the sentiment score is not indifference — it simply reflects that these comments are informational rather than emotional. The pattern repeating across two separate videos makes this a finding, not a coincidence. Combined with the positive tone of authentic career content, this reveals **EY has strong and consistent employer brand pull worldwide**, attracting motivated applicants across every service line and geography.

A traditional sentiment score alone would miss this entirely. Understanding *why* comments are neutral matters as much as the score itself.

>  Screenshots, word clouds, and full comment data → [`ey-analysis/`](./ey-analysis/)

---

##  How It Works

```
1. The extension scrapes comments from the YouTube video
2. Comments are sent to a REST API hosted on AWS
3. A machine learning model classifies each comment
4. Results are displayed instantly in your browser
```

Under the hood, the entire pipeline — from raw data to live prediction — is automated, versioned, and reproducible using industry-standard MLOps tools.

---

##  Tech Stack

| What | How |
|---|---|
| Collect & process comments | Python, YouTube API |
| Train & track the model | Scikit-learn, MLflow, DVC |
| Serve predictions | Flask REST API |
| Deploy to production | Docker, AWS EC2 + ECR |
| Automate releases | GitHub Actions CI/CD |
| Deliver to the user | Chrome Extension |

---

##  Project Structure

```
youtube-sentiment-mlops/
│
├── src/                  # Pipeline stages
├── chrome-extension/     # The browser extension
├── ey-analysis/          # EY use case: charts, insights, comments
├── app.py                # Flask REST API
├── dvc.yaml              # Pipeline definition
├── params.yaml           # Hyperparameters
└── requirements.txt
```

---

## 🙏 Credits

Reproduced from the original course by [Bappy Ahmed](https://github.com/entbappy/End-to-end-Youtube-Sentiment),
featured on [freeCodeCamp](https://www.youtube.com/watch?v=gwNPV882tkc).
