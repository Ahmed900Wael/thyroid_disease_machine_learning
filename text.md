## Dataset Overview
The dataset consists of **9,172 records** and **31 columns**
- Identities: patient_id (A unique number for each patient).
- Demographics: age and sex.
- Medical History (Flags): Columns like sick, pregnant, lithium, psych. These are mostly Boolean (True/False represented as 't'/'f').
- Clinical Measurements: Quantitative lab results like TSH, T3, TT4, T4U, FTI, and TBG.
- The Target: The target column contains the medical diagnosis coded as letters.

---

### Nature of each column
By looking at the unique values and types, we can group the columns into three main "Natures":
1. The indicator flags (binary) <br>
    There are 20+ columns that are strictky **'t'** or **'f'**
    - History: on_thyroxine, thyroid_surgery, I131_treatment.
    - Current State: sick, pregnant, goitre, tumor.
    - Administrative/Lab Logic: TSH_measured, T3_measured, etc. These tell us if the lab actually ran the test.

2. The Measurements <br>
   These are the diagnostic tools.
   - TSH: Thyroid Stimulating Hormone (The "Signal" from the brain).
   - T3/TT4: The actual hormones produced.
   - FTI: Free Thyroxine Index (A calculated value showing how much hormone is actually "free" to work in the body).

3. Clinical outcome (Target)
    This is the most complex column. It isn't just "Sick" or "Healthy"; it has over 30 combinations of letters representing specific subtypes of thyroid health.

---

### Early Observations (The "Red Flags")
Looking at the raw statistical summary, we immediately see things that tell us how to proceed:
1. Impossible Age: The max age is 65,526. This tells us the data has entry errorsthat need to be addressed later.
1. Missing Values (The Sparse Column): The column TBG only has 349 values out of 9172. This means for most patients, this specific test was never done.
1. TSH Variation: The mean TSH is 5.2, but the max is 530. This massive differencebetween the average and the maximum tells us that "Hypothyroid" patients have hormonelevels that are hundreds of times higher than normal.
1. Skewed Gender: By looking at the first few rows and the counts, we see a much higher frequency of 'F' than 'M'.