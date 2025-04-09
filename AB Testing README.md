# 📊 A/B Testing: Personalized vs Generic Chatbot Greetings

This project analyzes the effectiveness of personalized chatbot greetings (Group B) compared to generic greetings (Group A) in improving user engagement. Using simulated data and statistical hypothesis testing, we assess whether personalization leads to higher interaction rates, faster responses, and longer session durations.

---

## 📁 Dataset Overview

The dataset consists of 5,000 users split evenly across two groups:
- **Group A**: Received a generic chatbot greeting.
- **Group B**: Received a personalized chatbot greeting (e.g., using the user's name).

Each entry contains:
- `group`: A or B (greeting type)
- `engaged`: 1 if the user engaged with the chatbot, 0 otherwise
- `time_to_response_sec`: Time (in seconds) it took to respond
- `session_length_sec`: Total time the user spent in the session

> 🔗 *Synthetic dataset was generated for demonstration purposes.*

---

## 🔬 Objective

**Hypothesis:**
- **H₀ (Null Hypothesis):** There is no difference in engagement rates between generic and personalized greetings.
- **H₁ (Alternative Hypothesis):** Personalized greetings (Group B) result in significantly higher engagement.

---

## 🧪 Methods Used

### 1. Exploratory Data Analysis (EDA)
- Visualized engagement rates by group
- Compared distributions of session lengths and response times

### 2. Statistical Testing
- ✅ **Z-Test**: Compared proportions of engagement between groups
- ✅ **Chi-Square Test**: Checked independence of group and engagement
- ✅ **Mann-Whitney U-Test**: Compared median session durations and response times
- ✅ **T-Test** (optional): Compared means for normally distributed features
- ✅ **Cohen's d**: Measured effect size for business interpretation

---

## 📊 Results

| Metric                  | Group A        | Group B        | Lift (%) / Notes       |
|-------------------------|----------------|----------------|-------------------------|
| Engagement Rate         | 18.1%          | 21.6%          | 🚀 +19.58% Uplift         |
| Mean Session Length     | 58.7 sec      | 61.1 sec      | ⏱️ Longer sessions       |
| P-value (Z-Test)        | 0.0003         | —              | 📉 Statistically significant |
| Z- Statistic            | 0.35           | —              | 🧠 Strong evidence    |

✅ **Conclusion**: The results support the alternative hypothesis. Personalized chatbot greetings significantly increase engagement and session activity.

---

## 📈 Visuals

- 📊 Bar plots of engagement rate per group
- 📈 Histograms of response time
- 📦 Boxplots for session durations
- 🔍 Heatmaps and summary tables for clear comparison

---

## 🧠 Key Takeaways

- Personalization leads to **statistically significant improvement** in user engagement.
- Session lengths and response times are **better** for personalized interactions.
- This type of test can be implemented easily by SaaS companies, support bots, and customer experience teams.

---

## 💡 Future Improvements

- Use real-world A/B testing platforms like Optimizely or VWO.
- Track long-term impact on conversions or retention.
- Include user segmentation (device type, time of day, etc.).
- Run Bayesian A/B testing for continuous learning.
