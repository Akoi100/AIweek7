# AI Ethics Assignment

**Theme**: "Designing Responsible and Fair AI Systems" 🌍⚖️

This repository contains comprehensive analysis of AI ethics principles, case studies, and a practical bias audit of the COMPAS recidivism prediction system.

---

## 📁 Repository Structure

```
AI_Ethics_Assignment/
│
├── ethics_assignment_report.md      # Parts 1, 2, 4: Theory, case studies, reflection
├── healthcare_ai_ethics_policy.md   # Bonus: Healthcare AI ethics guidelines
│
├── code/
│   ├── compas_bias_audit.ipynb      # Part 3: COMPAS dataset bias analysis
│   └── bias_audit_report.md         # 300-word findings summary
│
├── data/
│   └── (COMPAS dataset - download separately)
│
├── README.md                         # This file
└── requirements.txt                  # Python dependencies
```

---

## 🎯 Assignment Overview

### Part 1: Theoretical Understanding (30%)

**Q1: Algorithmic Bias**
- Definition and manifestation mechanisms
- Examples: Amazon hiring tool (gender bias), COMPAS (racial bias)

**Q2: Transparency vs. Explainability**
- Transparency: System-level openness (what the system is)
- Explainability: Instance-level interpretability (why specific decisions)
- Both necessary for trustworthy AI

**Q3: GDPR Impact on AI**
- Right to explanation (Article 22)
- Data minimization and purpose limitation
- Privacy by design requirements
- Enforcement: Up to €20M or 4% global revenue

**Ethical Principles Matching**:
- Justice → Fair distribution of AI benefits/risks
- Non-maleficence → Do no harm
- Autonomy → User control over data/decisions
- Sustainability → Environmental responsibility

---

### Part 2: Case Study Analysis (40%)

#### Case 1: Amazon's Biased Hiring Tool

**Source of Bias**:
- Historical bias in training data (70% male resumes)
- Proxy features (women's colleges, gendered language)
- Feedback loop amplification

**Proposed Fixes**:
1. Reweighed training data for gender balance
2. Remove gendered features and proxies
3. Fairness-constrained optimization (equal opportunity)

**Fairness Metrics**:
- Disparate Impact Ratio (target: >0.8)
- Equal Opportunity Difference (target: <0.05)
- Average Odds Difference
- Calibration across groups

#### Case 2: Facial Recognition in Policing

**Ethical Risks**:
- Wrongful arrests (43x higher error rate for Black women)
- Privacy violations and mass surveillance
- Reinforcement of systemic racism
- Lack of accountability

**Policy Recommendations**:
1. Moratorium on real-time FRT until accuracy parity
2. Mandatory accuracy audits (>99% for all demographics)
3. Judicial oversight and warrant requirements
4. Human review and corroboration
5. Community consent and democratic oversight
6. Data protection and retention limits
7. Vendor accountability

---

### Part 3: Practical Audit (25%)

**COMPAS Recidivism Dataset Analysis**

**Key Findings**:
- **Disparate Impact**: 0.65 (violates 80% rule)
- **False Positive Rate**: Black defendants 44.9% vs. White 23.5% (2x disparity)
- **False Negative Rate**: White defendants 47.7% vs. Black 28.0%

**Visualizations**:
- Risk score distributions by race
- Confusion matrices showing error disparities
- Fairness metrics dashboard

**Remediation**:
- Suspend use until bias eliminated
- Retrain with fairness constraints
- Remove proxy features
- Continuous monitoring

---

### Part 4: Ethical Reflection (5%)

**Personal Project**: Mental health chatbot for university students

**Ethical Principles Applied**:
- **Non-maleficence**: Crisis detection, escalation to professionals
- **Autonomy**: Informed consent, data control, opt-out rights
- **Justice**: Diverse training data, cultural sensitivity, accessibility
- **Transparency**: Clear AI disclosure, explainable recommendations
- **Privacy**: End-to-end encryption, anonymization, HIPAA compliance

---

### Bonus Task (10%)

**Healthcare AI Ethics Policy**

**Key Components**:
1. **Patient Consent**: Informed consent forms, opt-out rights, vulnerable population protections
2. **Bias Mitigation**: Pre-deployment audits, diverse training data, continuous monitoring
3. **Transparency**: Model cards, explainable AI, audit trails
4. **Accountability**: Human oversight, clinical validation board, liability framework
5. **Privacy**: HIPAA compliance, de-identification, data minimization

---

## 🚀 How to Run the COMPAS Bias Audit

### Prerequisites

```bash
# Install Python 3.8+
python --version

# Install dependencies
pip install -r requirements.txt
```

### Download COMPAS Dataset

```bash
# Option 1: From ProPublica GitHub
wget https://raw.githubusercontent.com/propublica/compas-analysis/master/compas-scores-two-years.csv -O data/compas-scores-two-years.csv

# Option 2: Manual download
# Visit: https://github.com/propublica/compas-analysis
# Download compas-scores-two-years.csv to data/ folder
```

### Run the Audit

```bash
# Launch Jupyter Notebook
jupyter notebook code/compas_bias_audit.ipynb

# Or run as Python script (if converted)
python code/compas_bias_audit.py
```

**Expected Output**:
- Fairness metrics (disparate impact, equal opportunity)
- Confusion matrices by race
- Visualizations of bias
- 300-word findings report

---

## 📊 Key Results

### COMPAS Bias Metrics

| Metric | Value | Interpretation |
|--------|-------|----------------|
| **Disparate Impact Ratio** | 0.65 | Violates 80% rule (adverse impact) |
| **FPR (Black)** | 44.9% | Nearly 2x higher than white defendants |
| **FPR (White)** | 23.5% | Significantly lower false positive rate |
| **Equal Opportunity Diff** | +0.197 | Unequal treatment of recidivists |

**Conclusion**: COMPAS exhibits systematic racial bias and should not be used for consequential decisions.

---

## 📚 Technologies Used

- **Python 3.8+**
- **AI Fairness 360**: IBM's bias detection and mitigation toolkit
- **Pandas & NumPy**: Data manipulation
- **Matplotlib & Seaborn**: Visualization
- **Jupyter Notebook**: Interactive analysis

---

## 🌐 Real-World Impact

This assignment demonstrates:

✅ **Critical Analysis**: Understanding sources and manifestations of algorithmic bias  
✅ **Practical Skills**: Using AI Fairness 360 to audit real-world systems  
✅ **Policy Thinking**: Proposing actionable solutions to ethical dilemmas  
✅ **Stakeholder Awareness**: Considering impacts on vulnerable populations  
✅ **Regulatory Knowledge**: GDPR, healthcare regulations, legal standards  

---

## 📖 Learning Outcomes

- ✅ Define and identify algorithmic bias
- ✅ Distinguish transparency from explainability
- ✅ Understand GDPR's impact on AI development
- ✅ Analyze case studies (Amazon hiring, facial recognition)
- ✅ Conduct bias audits using AI Fairness 360
- ✅ Propose fairness metrics and remediation strategies
- ✅ Draft ethical AI policies for healthcare
- ✅ Reflect on personal project ethics

---

## 📄 References

1. Angwin, J., et al. (2016). Machine Bias. *ProPublica*.
2. Buolamwini, J., & Gebru, T. (2018). Gender Shades. *Proceedings of Machine Learning Research*.
3. Dastin, J. (2018). Amazon scraps secret AI recruiting tool. *Reuters*.
4. European Commission. (2019). Ethics Guidelines for Trustworthy AI.
5. Bellamy, R. K., et al. (2019). AI Fairness 360. *IBM Journal of Research and Development*.

---

## 👥 Contributors

[Peer Group Members]

---

## 📄 License

This project is submitted as part of the AI Ethics course assignment.

---

**Submission**: GitHub Repository - https://github.com/Akoi100/AIweek7  
**Date**: November 28, 2025  
**Course**: AI Ethics
