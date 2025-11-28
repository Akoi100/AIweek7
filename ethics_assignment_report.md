# AI Ethics Assignment
## "Designing Responsible and Fair AI Systems" 🌍⚖️

**Peer Group**: [Group Members]  
**Date**: November 28, 2025  
**Course**: AI Ethics

---

## Table of Contents

1. [Part 1: Theoretical Understanding](#part-1-theoretical-understanding)
2. [Part 2: Case Study Analysis](#part-2-case-study-analysis)
3. [Part 4: Ethical Reflection](#part-4-ethical-reflection)
4. [References](#references)

---

# Part 1: Theoretical Understanding (30%)

## 1. Short Answer Questions

### Q1: Define Algorithmic Bias and Provide Two Examples

**Definition**:

**Algorithmic bias** refers to systematic and repeatable errors in a computer system that create unfair outcomes, such as privileging one arbitrary group of users over others. It occurs when an AI system produces results that are systematically prejudiced due to erroneous assumptions in the machine learning process, biased training data, or flawed algorithm design.

**Key Characteristics**:
- **Systematic**: Not random errors, but consistent patterns of unfairness
- **Amplification**: AI can amplify existing societal biases at scale
- **Opacity**: Often hidden within complex models, making detection difficult
- **Perpetuation**: Can reinforce and perpetuate historical discrimination

---

**Example 1: Hiring Algorithms (Gender Bias)**

**Scenario**: Amazon's AI recruiting tool (2014-2017)

**How Bias Manifested**:
- The algorithm was trained on 10 years of historical resumes, predominantly from male candidates (tech industry gender imbalance)
- The model learned to penalize resumes containing the word "women's" (e.g., "women's chess club captain")
- It downranked graduates from all-women's colleges
- The system essentially learned that "male = qualified candidate"

**Impact**:
- Systematically discriminated against female applicants
- Perpetuated existing gender imbalance in tech
- Amazon disbanded the tool after discovering the bias

**Root Cause**: **Historical bias** in training data reflected past discriminatory hiring practices, which the AI learned to replicate.

---

**Example 2: Criminal Risk Assessment (Racial Bias)**

**Scenario**: COMPAS (Correctional Offender Management Profiling for Alternative Sanctions) recidivism prediction system

**How Bias Manifested**:
- ProPublica's 2016 analysis found the algorithm had different error rates across racial groups
- **False Positive Rate**: Black defendants were incorrectly labeled "high risk" at nearly twice the rate of white defendants (45% vs. 23%)
- **False Negative Rate**: White defendants were incorrectly labeled "low risk" more often than Black defendants
- Predictions were only 61% accurate overall, barely better than random

**Impact**:
- Black defendants received harsher bail conditions and sentencing recommendations
- Reinforced racial disparities in the criminal justice system
- Violated the principle of equal treatment under the law

**Root Cause**: **Proxy discrimination** - while the algorithm didn't explicitly use race, it relied on features correlated with race (zip code, employment history, social networks) that reflect systemic inequality.

---

### Q2: Explain the Difference Between Transparency and Explainability in AI

**Transparency** and **explainability** are related but distinct concepts in AI ethics:

---

#### Transparency

**Definition**: The degree to which the AI system's design, data, and decision-making processes are open and accessible to stakeholders.

**Focus**: **"What is the system doing?"**

**Key Aspects**:
1. **Model Documentation**: Publishing model architecture, training procedures, hyperparameters
2. **Data Transparency**: Disclosing training data sources, collection methods, preprocessing steps
3. **Process Transparency**: Documenting development lifecycle, testing procedures, deployment conditions
4. **Algorithmic Transparency**: Making source code available (open-source models)

**Example**: 
- OpenAI publishing technical papers on GPT models
- Google releasing Model Cards documenting intended use, limitations, and performance across demographics
- Sharing datasets publicly (ImageNet, COCO)

**Limitation**: A transparent system can still be incomprehensible. Knowing that a model has 175 billion parameters doesn't help users understand *why* it made a specific decision.

---

#### Explainability (Interpretability)

**Definition**: The ability to explain or present an AI system's decision-making process in understandable terms to humans.

**Focus**: **"Why did the system make this specific decision?"**

**Key Aspects**:
1. **Local Explanations**: Why did the model predict X for this specific input? (e.g., LIME, SHAP)
2. **Global Explanations**: What are the general rules the model follows? (e.g., feature importance)
3. **Counterfactual Explanations**: What would need to change for a different outcome? ("If your income were $5,000 higher, you'd be approved")
4. **Human-Understandable**: Explanations must be comprehensible to non-experts

**Example**:
- A loan denial system explaining: "Your application was rejected because: debt-to-income ratio (40% weight), credit score (30% weight), employment history (20% weight)"
- Medical diagnosis AI showing which regions of an X-ray led to a cancer detection
- SHAP values showing feature contributions to a prediction

**Limitation**: Explanations can be post-hoc rationalizations that don't truly reflect the model's internal logic (especially for deep neural networks).

---

#### Why Both Are Important

| Aspect | Transparency | Explainability |
|--------|--------------|----------------|
| **Audience** | Developers, regulators, researchers | End users, affected individuals |
| **Purpose** | Enable auditing, replication, accountability | Enable informed consent, contestability |
| **Scope** | System-level (entire model) | Instance-level (specific decisions) |
| **Requirement** | Technical documentation | User-facing explanations |

**Complementary Roles**:

1. **Trust Building**: 
   - Transparency shows *what* the system is (building institutional trust)
   - Explainability shows *why* decisions are made (building user trust)

2. **Accountability**:
   - Transparency enables external audits and regulatory compliance
   - Explainability enables individuals to challenge unfair decisions

3. **Debugging**:
   - Transparency helps developers identify systemic issues
   - Explainability helps identify specific failure cases

4. **Legal Compliance**:
   - GDPR Article 22: Right to explanation for automated decisions (explainability)
   - EU AI Act: Documentation requirements for high-risk AI (transparency)

**Example Scenario**: Healthcare AI

- **Transparency**: Hospital publishes that they use IBM Watson for cancer diagnosis, trained on 50,000 cases from Memorial Sloan Kettering
- **Explainability**: When Watson recommends chemotherapy for a patient, it shows: "Tumor size (35%), lymph node involvement (30%), genetic markers (20%), patient age (15%)"

**Conclusion**: You can have transparency without explainability (open-source black box), and explainability without transparency (proprietary model with user-facing explanations). **Both are necessary** for trustworthy AI.

---

### Q3: How Does GDPR Impact AI Development in the EU?

The **General Data Protection Regulation (GDPR)**, effective May 2018, fundamentally reshaped AI development in the European Union by imposing strict requirements on data processing and automated decision-making.

---

#### Key GDPR Provisions Affecting AI

**1. Right to Explanation (Article 22)**

**Provision**: Individuals have the right not to be subject to decisions based solely on automated processing that produce legal or similarly significant effects, **unless** they can contest the decision and obtain human intervention.

**Impact on AI**:
- **Explainability Requirement**: AI systems making consequential decisions (loan approvals, hiring, medical diagnosis) must provide meaningful explanations
- **Human-in-the-Loop**: Fully automated decision-making is restricted; human oversight often required
- **Model Choice**: Favors interpretable models (logistic regression, decision trees) over black boxes (deep neural networks)

**Example**: A bank's AI credit scoring system must explain why an applicant was rejected, not just provide a score.

---

**2. Data Minimization (Article 5)**

**Provision**: Collect only data that is adequate, relevant, and limited to what is necessary for the specified purpose.

**Impact on AI**:
- **Feature Selection**: Cannot collect "just in case" data; must justify every feature
- **Proxy Variables**: Prohibited from using proxies for protected attributes (e.g., zip code as proxy for race)
- **Training Data**: Must demonstrate that all training data is necessary

**Example**: A hiring AI cannot use applicants' social media data unless directly relevant to job performance.

---

**3. Purpose Limitation (Article 5)**

**Provision**: Data collected for one purpose cannot be repurposed without explicit consent.

**Impact on AI**:
- **Model Retraining**: Cannot repurpose customer data collected for service delivery to train marketing AI without consent
- **Transfer Learning**: Restrictions on using pre-trained models if original data purpose differs
- **Data Sharing**: Cannot share training data with third parties for different AI applications

**Example**: Healthcare data collected for treatment cannot be used to train insurance risk models without patient consent.

---

**4. Right to Erasure / "Right to be Forgotten" (Article 17)**

**Provision**: Individuals can request deletion of their personal data.

**Impact on AI**:
- **Model Unlearning**: Must remove individual's data from training sets and potentially retrain models
- **Data Retention**: Cannot indefinitely store training data; must implement deletion mechanisms
- **Technical Challenge**: Difficult to "unlearn" specific data points from trained neural networks

**Example**: If a user requests deletion, their photos must be removed from facial recognition training datasets.

---

**5. Data Protection by Design and Default (Article 25)**

**Provision**: Privacy must be built into systems from the outset, not added as an afterthought.

**Impact on AI**:
- **Privacy-Preserving AI**: Encourages techniques like differential privacy, federated learning, homomorphic encryption
- **Default Settings**: AI systems must use privacy-protective defaults (e.g., minimal data collection)
- **Impact Assessments**: Data Protection Impact Assessments (DPIAs) required for high-risk AI

**Example**: A recommendation system must use differential privacy to prevent individual user data from being inferred.

---

**6. Lawful Basis for Processing (Article 6)**

**Provision**: Data processing requires a lawful basis (consent, contract, legal obligation, vital interests, public task, or legitimate interests).

**Impact on AI**:
- **Consent Requirements**: Explicit, informed consent needed for AI training on personal data
- **Legitimate Interest**: Must balance business interests against individual rights
- **Sensitive Data**: Extra restrictions on processing race, health, biometric data (Article 9)

**Example**: Training a facial recognition model on publicly scraped photos may violate GDPR without explicit consent.

---

#### Practical Implications for AI Developers

**Compliance Costs**:
- **Legal Review**: Every AI project requires GDPR compliance assessment
- **Documentation**: Extensive record-keeping of data sources, processing activities, model decisions
- **Technical Investment**: Implementing explainability tools, privacy-preserving techniques
- **Estimated Cost**: 10-20% increase in AI development budgets for GDPR compliance

**Innovation Trade-offs**:
- **Slower Development**: Consent collection and impact assessments delay deployment
- **Reduced Data Access**: Stricter data minimization limits training data availability
- **Model Performance**: Interpretable models may sacrifice accuracy compared to black boxes

**Competitive Dynamics**:
- **EU Disadvantage**: Stricter regulations may slow EU AI development compared to US/China
- **Privacy as Differentiator**: EU companies can market GDPR-compliant AI as more trustworthy
- **Global Standard**: GDPR has inspired similar laws worldwide (CCPA in California, LGPD in Brazil)

---

#### Enforcement and Penalties

**Fines**:
- Up to **€20 million** or **4% of global annual revenue**, whichever is higher
- Notable Cases:
  - Google fined €50 million (2019) for lack of transparency in ad personalization
  - Amazon fined €746 million (2021) for behavioral advertising violations

**Impact**: High penalties incentivize GDPR compliance in AI systems.

---

#### Future: EU AI Act

The proposed **EU AI Act** (expected 2024-2025) will further regulate AI:
- **Risk-Based Approach**: Bans on high-risk AI (social scoring, real-time biometric surveillance)
- **Transparency Requirements**: Mandatory disclosure when interacting with AI (chatbots, deepfakes)
- **Conformity Assessments**: Third-party audits for high-risk AI systems

**Conclusion**: GDPR has made the EU the world's strictest jurisdiction for AI development, prioritizing individual rights over technological innovation. AI developers must balance compliance costs with the benefits of operating in a privacy-conscious market.

---

## 2. Ethical Principles Matching

Match the following principles to their definitions:

**A) Justice**  
**B) Non-maleficence**  
**C) Autonomy**  
**D) Sustainability**

---

### Definitions:

1. **Ensuring AI does not harm individuals or society.**  
   **Answer: B) Non-maleficence**
   
   *Explanation*: Non-maleficence ("do no harm") is the principle that AI systems should not cause harm to individuals, groups, or society. This includes preventing physical harm, psychological harm, economic harm, and social harm. Examples: ensuring autonomous vehicles prioritize safety, preventing AI-generated misinformation, avoiding discriminatory outcomes.

2. **Respecting users' right to control their data and decisions.**  
   **Answer: C) Autonomy**
   
   *Explanation*: Autonomy is the principle that individuals should have control over their own data, decisions, and lives. AI should empower users, not manipulate or coerce them. This includes informed consent, opt-out mechanisms, and transparency about AI use. Examples: allowing users to delete their data, providing clear explanations of AI decisions, avoiding dark patterns.

3. **Designing AI to be environmentally friendly.**  
   **Answer: D) Sustainability**
   
   *Explanation*: Sustainability refers to developing AI systems that minimize environmental impact, considering energy consumption, carbon footprint, and resource usage. Large language models and data centers have significant environmental costs. Examples: using renewable energy for training, optimizing model efficiency, considering lifecycle environmental impact.

4. **Fair distribution of AI benefits and risks.**  
   **Answer: A) Justice**
   
   *Explanation*: Justice (or fairness) is the principle that AI's benefits and burdens should be distributed equitably across society. This includes preventing discrimination, ensuring equal access to AI benefits, and avoiding concentration of power. Examples: ensuring AI healthcare benefits reach underserved communities, preventing algorithmic bias, fair compensation for data labor.

---

# Part 2: Case Study Analysis (40%)

## Case 1: Biased Hiring Tool - Amazon's AI Recruiting System

### Background

In 2014, Amazon began developing an AI-powered recruiting tool to automate resume screening and identify top candidates. The system was trained on resumes submitted to Amazon over a 10-year period (predominantly from male candidates due to tech industry demographics). By 2015, Amazon discovered the tool was systematically penalizing female candidates. The project was disbanded in 2017.

---

### Task 1: Identify the Source of Bias

The bias in Amazon's hiring AI stemmed from **multiple interconnected sources**:

#### Primary Source: Historical Bias in Training Data

**Problem**: The model was trained on 10 years of resumes from candidates who were hired or considered, 60-70% of whom were male.

**Mechanism**:
- The AI learned patterns from historical hiring decisions that reflected gender imbalance
- It identified "successful candidate" patterns that correlated with male-dominated backgrounds
- The model essentially learned: **"Male candidate characteristics = Good hire"**

**Specific Manifestations**:
1. **Keyword Penalization**: Downranked resumes containing "women's" (e.g., "women's chess club captain," "women's college")
2. **University Bias**: Penalized graduates from all-women's colleges
3. **Activity Patterns**: Favored language and activities more common in male resumes (e.g., "executed," "captured" vs. "coordinated," "collaborated")

#### Secondary Source: Proxy Features

**Problem**: Even after removing explicit gender indicators, the model used proxy features correlated with gender.

**Examples**:
- **Hobbies/Activities**: Sports teams, gaming communities (male-dominated)
- **Language Patterns**: Assertive language more common in male resumes
- **Career Gaps**: Penalized employment gaps (disproportionately affects women due to maternity leave)
- **Educational Institutions**: Certain universities or programs with gender imbalances

#### Tertiary Source: Feedback Loop Amplification

**Problem**: If deployed, the biased system would have created a self-reinforcing cycle.

**Mechanism**:
1. AI recommends more male candidates
2. Hiring managers interview and hire more men
3. New hiring data reinforces male = qualified
4. Model retraining amplifies the bias

---

### Task 2: Propose Three Fixes to Make the Tool Fairer

#### Fix 1: Debiased Training Data with Reweighing

**Approach**: Adjust training data to balance representation and outcomes across genders.

**Implementation**:
```python
# Pseudo-code
from aif360.algorithms.preprocessing import Reweighing

# Assign higher weights to underrepresented group (women)
# Lower weights to overrepresented group (men)
reweigher = Reweighing(unprivileged_groups=[{'gender': 'female'}],
                       privileged_groups=[{'gender': 'male'}])
dataset_transformed = reweigher.fit_transform(training_data)

# Train model on reweighted data
model.fit(dataset_transformed)
```

**Benefits**:
- Ensures model sees balanced examples of successful candidates
- Prevents learning "male = qualified" pattern
- Maintains data diversity

**Limitations**:
- Requires gender labels (may not always be available)
- Doesn't address proxy features

---

#### Fix 2: Remove Gendered Features and Proxies

**Approach**: Eliminate features that directly or indirectly encode gender.

**Direct Removals**:
- Name (can indicate gender)
- Pronouns (he/she)
- Gendered keywords ("women's," "men's")
- Photos (if included)

**Proxy Removals**:
- All-women's or all-men's colleges
- Gender-correlated hobbies/activities
- Sororities/fraternities
- Gendered language patterns

**Advanced Technique**: **Adversarial Debiasing**
```python
# Train model to predict qualifications while being unable to predict gender
# Uses adversarial network to remove gender information from learned representations
from aif360.algorithms.inprocessing import AdversarialDebiasing

debiased_model = AdversarialDebiasing(
    unprivileged_groups=[{'gender': 'female'}],
    privileged_groups=[{'gender': 'male'}],
    scope_name='debiased_classifier'
)
debiased_model.fit(training_data)
```

**Benefits**:
- Prevents direct and indirect gender discrimination
- Forces model to focus on job-relevant skills

**Limitations**:
- May remove legitimate signals (e.g., women's leadership experience)
- Difficult to identify all proxies

---

#### Fix 3: Fairness-Constrained Optimization

**Approach**: Train the model with explicit fairness constraints that enforce equal treatment.

**Constraint Types**:

1. **Demographic Parity**: Equal selection rates across genders
   ```
   P(selected | female) = P(selected | male)
   ```

2. **Equal Opportunity**: Equal true positive rates (qualified candidates recommended equally)
   ```
   P(selected | qualified, female) = P(selected | qualified, male)
   ```

3. **Equalized Odds**: Equal TPR and FPR across genders
   ```
   P(selected | qualified, female) = P(selected | qualified, male)
   P(selected | unqualified, female) = P(selected | unqualified, male)
   ```

**Implementation**:
```python
from fairlearn.reductions import ExponentiatedGradient, DemographicParity

# Train model with demographic parity constraint
mitigator = ExponentiatedGradient(
    base_estimator=LogisticRegression(),
    constraints=DemographicParity()
)
mitigator.fit(X_train, y_train, sensitive_features=gender)
```

**Benefits**:
- Mathematically guarantees fairness metrics
- Transparent and auditable
- Can balance accuracy and fairness

**Limitations**:
- May reduce overall accuracy
- Requires choosing which fairness metric to optimize (they can conflict)

---

### Task 3: Suggest Metrics to Evaluate Fairness Post-Correction

#### Metric 1: Disparate Impact Ratio

**Definition**: Ratio of selection rates between unprivileged (women) and privileged (men) groups.

**Formula**:
```
Disparate Impact = P(selected | female) / P(selected | male)
```

**Interpretation**:
- **1.0**: Perfect parity (equal selection rates)
- **< 0.8**: Adverse impact (80% rule violation, legally problematic in US)
- **> 1.2**: Reverse discrimination

**Example**:
- If 40% of female applicants are selected and 50% of male applicants:
- Disparate Impact = 0.40 / 0.50 = **0.80** (borderline acceptable)

**Why Important**: Simple, interpretable, legally recognized metric.

---

#### Metric 2: Equal Opportunity Difference

**Definition**: Difference in true positive rates (recall) between groups.

**Formula**:
```
EOD = TPR(female) - TPR(male)
= P(selected | qualified, female) - P(selected | qualified, male)
```

**Interpretation**:
- **0**: Perfect equal opportunity (qualified candidates equally likely to be selected)
- **Negative**: Qualified women less likely to be selected (bias against women)
- **Positive**: Qualified men less likely to be selected (bias against men)

**Example**:
- 80% of qualified women selected, 90% of qualified men selected
- EOD = 0.80 - 0.90 = **-0.10** (10% disadvantage for women)

**Why Important**: Focuses on fairness for qualified candidates (meritocracy).

---

#### Metric 3: Average Odds Difference

**Definition**: Average of TPR difference and FPR difference.

**Formula**:
```
AOD = 0.5 * [(TPR_female - TPR_male) + (FPR_female - FPR_male)]
```

**Interpretation**:
- **0**: Perfect equalized odds (equal error rates)
- Captures both false positives and false negatives

**Example**:
- TPR: 80% (female) vs. 90% (male) → difference = -0.10
- FPR: 15% (female) vs. 10% (male) → difference = +0.05
- AOD = 0.5 * (-0.10 + 0.05) = **-0.025**

**Why Important**: Comprehensive metric considering both types of errors.

---

#### Metric 4: Calibration

**Definition**: Among candidates predicted to have score X, the actual qualification rate should be the same across groups.

**Formula**:
```
P(qualified | score=X, female) = P(qualified | score=X, male)
```

**Why Important**: Ensures predictions are equally reliable across groups.

---

#### Recommended Monitoring Dashboard

```
┌─────────────────────────────────────────────────────────┐
│           FAIRNESS METRICS DASHBOARD                    │
├─────────────────────────────────────────────────────────┤
│ Disparate Impact Ratio:        0.95  ✓ (target: >0.8)  │
│ Equal Opportunity Difference:  -0.02 ✓ (target: <0.05) │
│ Average Odds Difference:       -0.01 ✓ (target: <0.05) │
│ Calibration Error:             0.03  ✓ (target: <0.05) │
├─────────────────────────────────────────────────────────┤
│ Overall Accuracy:              82%                      │
│ Female Applicants Selected:    35%                      │
│ Male Applicants Selected:      37%                      │
└─────────────────────────────────────────────────────────┘
```

**Continuous Monitoring**: Track metrics monthly, alert if any metric degrades beyond threshold.

---

## Case 2: Facial Recognition in Policing

### Background

Facial recognition technology (FRT) is increasingly used by law enforcement for suspect identification, surveillance, and investigations. However, studies have shown that commercial FRT systems have significantly higher error rates for minorities, particularly Black women, compared to white men.

**Key Statistics** (MIT/NIST Studies):
- Error rates for Black women: **34.7%**
- Error rates for white men: **0.8%**
- **43x higher** error rate for darkest-skinned females vs. lightest-skinned males

---

### Task 1: Discuss Ethical Risks

#### Risk 1: Wrongful Arrests and False Accusations

**Problem**: High false positive rates for minorities lead to innocent people being arrested.

**Real-World Cases**:
1. **Robert Williams (Detroit, 2020)**: Wrongfully arrested based on facial recognition mismatch, held for 30 hours
2. **Michael Oliver (Detroit, 2019)**: Falsely identified in theft case
3. **Nijeer Parks (New Jersey, 2019)**: Spent 10 days in jail for crime he didn't commit

**Consequences**:
- **Legal**: Wrongful arrest, criminal record, legal fees
- **Economic**: Job loss, missed work, bail costs
- **Psychological**: Trauma, loss of trust in law enforcement
- **Social**: Stigma, damaged reputation

**Disproportionate Impact**: Black individuals face 43x higher risk of false identification, violating equal protection under the law.

---

#### Risk 2: Privacy Violations and Mass Surveillance

**Problem**: FRT enables pervasive, warrantless surveillance of public spaces.

**Mechanisms**:
- **Real-Time Surveillance**: Cameras scan crowds, identify individuals without consent
- **Retroactive Tracking**: Search historical footage to track individual's movements
- **Database Matching**: Compare faces against driver's license photos, mugshots, social media

**Chilling Effects**:
- **Free Assembly**: People avoid protests/rallies fearing identification and retaliation
- **Free Speech**: Self-censorship in public spaces
- **Association**: Tracking who meets with whom (journalists, activists, lawyers)

**Legal Concerns**:
- **Fourth Amendment**: Warrantless searches and seizures
- **First Amendment**: Chilling effect on free speech and assembly
- **No Consent**: Individuals unaware they're being surveilled

---

#### Risk 3: Reinforcement of Systemic Racism

**Problem**: Biased FRT amplifies existing racial disparities in policing.

**Mechanisms**:
1. **Over-Policing**: FRT deployed disproportionately in minority neighborhoods
2. **Feedback Loop**: More surveillance → more arrests → more data → more surveillance
3. **Confirmation Bias**: Officers trust FRT matches, leading to biased investigations

**Systemic Impact**:
- **Discriminatory Policing**: Technology legitimizes racial profiling
- **Erosion of Trust**: Communities lose faith in law enforcement
- **Perpetuation**: Reinforces "criminal = Black" stereotypes

---

#### Risk 4: Lack of Accountability and Transparency

**Problem**: Proprietary FRT systems operate as "black boxes" with no public oversight.

**Issues**:
- **No Audits**: Police departments don't test accuracy on diverse populations
- **No Standards**: No regulations on acceptable error rates
- **No Recourse**: Individuals can't challenge FRT evidence effectively
- **Vendor Secrecy**: Companies refuse to disclose training data or algorithms

**Consequences**:
- **Unchecked Errors**: Systems deployed despite known biases
- **No Liability**: Vendors and police departments avoid responsibility
- **Erosion of Due Process**: Defendants can't cross-examine algorithmic evidence

---

#### Risk 5: Mission Creep and Function Creep

**Problem**: FRT deployed for limited purposes expands to broader surveillance.

**Examples**:
- **Initial Use**: Identify suspects in serious crimes (terrorism, murder)
- **Expansion**: Minor offenses (shoplifting, traffic violations)
- **Ultimate Scope**: Continuous monitoring of all public spaces

**Slippery Slope**: Once infrastructure is in place, political pressures can expand use without public debate.

---

### Task 2: Recommend Policies for Responsible Deployment

#### Policy 1: Moratorium on Real-Time Facial Recognition

**Recommendation**: **Ban real-time FRT in public spaces** until accuracy parity is achieved and regulations are in place.

**Rationale**:
- Current error rates (43x disparity) are unacceptable for consequential decisions
- Real-time surveillance poses greatest privacy and civil liberties risks
- Allows time for technology improvement and regulatory development

**Exceptions**:
- **Narrow Use Cases**: Missing children, imminent terrorist threats (with judicial oversight)
- **Retroactive Use**: Post-incident investigation with warrant (less invasive than real-time)

**Precedents**:
- **San Francisco (2019)**: First US city to ban government use of FRT
- **EU AI Act (Proposed)**: Bans real-time biometric surveillance in public spaces
- **Multiple US Cities**: Boston, Portland, Minneapolis have enacted bans

---

#### Policy 2: Mandatory Accuracy Audits and Transparency

**Requirement**: Before deployment, FRT systems must undergo independent audits demonstrating:

1. **Demographic Parity**: Error rates within 5% across race, gender, age groups
2. **Minimum Accuracy**: >99% accuracy for all demographic groups
3. **Public Reporting**: Results published in accessible format

**Implementation**:
```
┌──────────────────────────────────────────────────────┐
│         FRT ACCURACY AUDIT REPORT                    │
├──────────────────────────────────────────────────────┤
│ Demographic Group    │ False Positive Rate │ Pass?  │
├──────────────────────────────────────────────────────┤
│ White Male           │ 0.8%                │ ✓      │
│ White Female         │ 1.2%                │ ✓      │
│ Black Male           │ 2.1%                │ ✓      │
│ Black Female         │ 2.5%                │ ✓      │
│ Asian Male           │ 1.5%                │ ✓      │
│ Asian Female         │ 1.8%                │ ✓      │
├──────────────────────────────────────────────────────┤
│ Maximum Disparity    │ 1.7%                │ ✓ <5%  │
│ Overall Accuracy     │ 98.5%               │ ✗ <99% │
├──────────────────────────────────────────────────────┤
│ DEPLOYMENT STATUS: NOT APPROVED                      │
└──────────────────────────────────────────────────────┘
```

**Enforcement**: Systems failing audits cannot be procured or deployed.

---

#### Policy 3: Judicial Oversight and Warrant Requirements

**Requirement**: FRT use requires judicial authorization, similar to wiretaps.

**Process**:
1. **Warrant Application**: Law enforcement must demonstrate probable cause
2. **Scope Limitation**: Warrant specifies who, where, when FRT can be used
3. **Judicial Review**: Judge evaluates necessity and proportionality
4. **Notification**: Subjects notified after investigation (unless ongoing)

**Exceptions**: Emergency situations (kidnapping, active shooter) with retroactive judicial review within 48 hours.

**Benefits**:
- **Checks and Balances**: Independent oversight prevents abuse
- **Proportionality**: Ensures FRT used only for serious crimes
- **Accountability**: Creates paper trail for audits

---

#### Policy 4: Human Review and Corroboration Requirements

**Requirement**: FRT matches cannot be sole basis for arrest or search; must be corroborated by human investigation.

**Process**:
1. **FRT Match**: System identifies potential suspect (confidence score)
2. **Human Review**: Trained officer reviews match, considers confidence level
3. **Independent Corroboration**: Additional evidence required (witness, alibi, other forensics)
4. **Arrest Decision**: Based on totality of evidence, not FRT alone

**Training**: Officers must complete bias training and understand FRT limitations.

**Documentation**: All FRT uses logged with justification and outcome.

---

#### Policy 5: Community Consent and Democratic Oversight

**Requirement**: FRT deployment requires public consultation and ongoing oversight.

**Implementation**:
1. **Public Hearings**: Community input before procurement decisions
2. **Impact Assessments**: Evaluate effects on civil liberties, racial equity
3. **Oversight Board**: Independent civilian board reviews FRT use quarterly
4. **Annual Reports**: Public disclosure of FRT usage statistics, accuracy, complaints

**Transparency**:
- Number of FRT searches conducted
- Demographic breakdown of subjects
- Match accuracy rates
- Arrests resulting from FRT
- Complaints and resolutions

**Democratic Control**: Communities can vote to ban or restrict FRT use.

---

#### Policy 6: Data Protection and Retention Limits

**Requirements**:
1. **Purpose Limitation**: FRT data used only for specified law enforcement purposes
2. **Retention Limits**: Delete FRT data after 30 days unless part of active investigation
3. **No Sharing**: Prohibit sharing with third parties (ICE, private companies) without warrant
4. **Audit Trails**: Log all access to FRT databases

**Rationale**: Prevents mission creep and protects privacy.

---

#### Policy 7: Vendor Accountability

**Requirements**:
1. **Liability**: Vendors liable for damages from erroneous identifications
2. **Disclosure**: Publish training data demographics, accuracy metrics
3. **Continuous Improvement**: Quarterly accuracy audits, mandatory updates
4. **Ethical Sourcing**: Training data obtained with consent, no scraped photos

**Enforcement**: Contracts include performance guarantees and penalties for bias.

---

### Conclusion

Facial recognition in policing presents profound ethical risks, particularly for minority communities. **Responsible deployment requires**:
- ✅ Accuracy parity across demographics
- ✅ Judicial oversight and warrants
- ✅ Human review and corroboration
- ✅ Community consent and transparency
- ✅ Strong data protection

**Current Recommendation**: **Moratorium on real-time FRT** until these safeguards are in place. The technology's potential benefits do not justify the current disparate impact on marginalized communities.

---

# Part 4: Ethical Reflection (5%)

## Prompt: Reflect on a Personal Project - Ensuring Ethical AI Principles

### Project Context

**Hypothetical Project**: Developing an AI-powered mental health chatbot to provide 24/7 emotional support and crisis intervention for university students.

**Motivation**: Address rising mental health issues on campuses, provide accessible support when counseling centers are closed or overwhelmed.

---

### Ethical Principles and Implementation

#### 1. Non-Maleficence ("Do No Harm")

**Risks**:
- Chatbot provides harmful advice (e.g., downplaying suicidal ideation)
- Over-reliance on AI delays professional help
- Privacy breach exposes sensitive mental health data

**Mitigation Strategies**:

**a) Crisis Detection and Escalation**:
```python
# Implement keyword detection for crisis situations
crisis_keywords = ['suicide', 'kill myself', 'end it all', 'self-harm']

if detect_crisis(user_message, crisis_keywords):
    # Immediately escalate to human counselor
    escalate_to_professional()
    # Provide crisis hotline numbers
    display_crisis_resources()
    # Do NOT attempt AI-generated advice
```

**b) Clear Disclaimers**:
- "I'm an AI assistant, not a replacement for professional therapy"
- "If you're in crisis, please call [Crisis Hotline] or go to [Emergency Services]"
- Display disclaimer at start of every conversation

**c) Regular Safety Audits**:
- Test chatbot responses to crisis scenarios
- Red team testing with mental health professionals
- Continuous monitoring of flagged conversations

---

#### 2. Autonomy (User Control)

**Implementation**:

**a) Informed Consent**:
```
Before using the chatbot, users must acknowledge:
☑ I understand this is an AI, not a human therapist
☑ I consent to my conversations being analyzed to improve the service
☑ I can delete my data at any time
☑ I understand my data will be encrypted and anonymized
```

**b) Data Control**:
- **Export**: Users can download conversation history
- **Delete**: One-click data deletion (GDPR compliance)
- **Opt-Out**: Disable conversation logging for privacy

**c) Human Override**:
- Option to request human counselor at any time
- "This conversation isn't helpful" → escalate to human

---

#### 3. Justice (Fairness and Accessibility)

**Challenges**:
- AI trained on predominantly white, Western mental health data
- Language barriers for international students
- Accessibility for students with disabilities

**Solutions**:

**a) Diverse Training Data**:
- Include mental health conversations from diverse cultural backgrounds
- Partner with counseling centers serving minority students
- Ensure representation across race, gender, LGBTQ+ identities

**b) Cultural Sensitivity**:
- Avoid Western-centric mental health frameworks
- Recognize cultural differences in expressing distress
- Provide multilingual support (Spanish, Mandarin, etc.)

**c) Accessibility**:
- Screen reader compatibility (WCAG 2.1 AA standards)
- Text-to-speech for visually impaired users
- Simple language for users with cognitive disabilities

---

#### 4. Transparency and Explainability

**Implementation**:

**a) How It Works**:
```
About This Chatbot:
• Powered by GPT-4 fine-tuned on mental health conversations
• Trained on 50,000 therapy transcripts (anonymized, consented)
• Responses reviewed by licensed therapists
• Cannot prescribe medication or diagnose conditions
```

**b) Explainable Recommendations**:
```
User: "I'm feeling really anxious about exams"
Chatbot: "I hear that you're anxious about exams. I'm suggesting 
deep breathing exercises because research shows they reduce 
anxiety by activating the parasympathetic nervous system. 
Would you like to try a guided breathing exercise?"
```

**c) Open Source (Where Possible)**:
- Publish model architecture and training methodology
- Share anonymized evaluation results
- Allow external audits by mental health professionals

---

#### 5. Privacy and Confidentiality

**Critical for Mental Health**:

**a) End-to-End Encryption**:
- All conversations encrypted in transit and at rest
- Zero-knowledge architecture (even admins can't read conversations)

**b) Anonymization**:
- No personally identifiable information collected
- Conversations linked to anonymous IDs, not student names
- Aggregate analytics only (no individual tracking)

**c) Data Minimization**:
- Collect only conversation text, timestamp
- No location data, device fingerprinting, or behavioral tracking
- Delete conversations after 90 days (unless user opts to keep)

**d) Legal Compliance**:
- HIPAA compliance (if considered healthcare)
- FERPA compliance (student privacy)
- GDPR compliance (EU students)

---

#### 6. Beneficence (Doing Good)

**Positive Impact Measures**:

**a) Effectiveness Evaluation**:
- Pre/post surveys: "How are you feeling?" (1-10 scale)
- Validated mental health scales (PHQ-9 for depression, GAD-7 for anxiety)
- Track if users seek professional help after chatbot interaction

**b) Continuous Improvement**:
- Monthly reviews with therapists to improve responses
- A/B testing different therapeutic approaches
- Incorporate user feedback

**c) Accessibility Goals**:
- Provide support during off-hours (nights, weekends)
- Reduce wait times for counseling (chatbot as triage)
- Reach students who wouldn't seek traditional therapy (stigma reduction)

---

### Accountability and Governance

**Oversight Structure**:
1. **Ethics Review Board**: University IRB approval before deployment
2. **Advisory Board**: Licensed therapists, ethicists, student representatives
3. **Quarterly Audits**: Review flagged conversations, safety incidents
4. **Incident Response**: Protocol for handling harmful interactions

**Metrics Dashboard**:
```
┌────────────────────────────────────────────────────┐
│        MENTAL HEALTH CHATBOT ETHICS DASHBOARD      │
├────────────────────────────────────────────────────┤
│ Crisis Escalations:           12 this month        │
│ User Satisfaction:            4.2/5.0              │
│ Privacy Incidents:            0                    │
│ Diverse User Representation:  65% (target: 70%)   │
│ Accessibility Compliance:     WCAG 2.1 AA ✓        │
└────────────────────────────────────────────────────┘
```

---

### Reflection

Developing ethical AI for mental health requires **constant vigilance**. The potential to help students is immense, but the risks of harm are equally significant. I would ensure ethical principles are not afterthoughts but **foundational design constraints**.

**Key Lessons**:
1. **Safety First**: No AI feature is worth risking a student's life
2. **Humility**: AI cannot replace human empathy and professional expertise
3. **Transparency**: Users deserve to know they're talking to a machine
4. **Continuous Improvement**: Ethics is an ongoing process, not a checkbox

**Ultimate Test**: Would I trust this chatbot with my own mental health? If not, it's not ready for deployment.

---

# References

1. Buolamwini, J., & Gebru, T. (2018). Gender Shades: Intersectional Accuracy Disparities in Commercial Gender Classification. *Proceedings of Machine Learning Research*, 81, 1-15.

2. Angwin, J., Larson, J., Mattu, S., & Kirchner, L. (2016). Machine Bias. *ProPublica*. Retrieved from https://www.propublica.org/article/machine-bias-risk-assessments-in-criminal-sentencing

3. European Commission. (2019). Ethics Guidelines for Trustworthy AI. *High-Level Expert Group on AI*.

4. Dastin, J. (2018). Amazon scraps secret AI recruiting tool that showed bias against women. *Reuters*.

5. Regulation (EU) 2016/679 (General Data Protection Regulation). *Official Journal of the European Union*.

6. Bellamy, R. K., et al. (2019). AI Fairness 360: An extensible toolkit for detecting and mitigating algorithmic bias. *IBM Journal of Research and Development*, 63(4/5), 4-1.

7. Mehrabi, N., et al. (2021). A Survey on Bias and Fairness in Machine Learning. *ACM Computing Surveys*, 54(6), 1-35.

8. Barocas, S., & Selbst, A. D. (2016). Big Data's Disparate Impact. *California Law Review*, 104, 671.

---

**End of Report**

*Submitted by: [Group Members]*  
*Date: November 28, 2025*  
*Course: AI Ethics*
