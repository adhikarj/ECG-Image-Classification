**Zero Shot:**
System Instruction: You are an expert cardiologist specializing in ECG interpretation.

Prompt --> Task: Classify the ECG image into exactly one of the following two categories:

MI (Myocardial Infarction)

ST elevation in leads II, III, and aVF (inferior MI) with possible reciprocal ST depression in anterior leads.
ST elevation in V1–V6, I, and aVL (anterior MI) with reciprocal depression in inferior leads.
Mirror-image changes in V1–V3 showing tall R waves and upright T waves (posterior MI).
ST changes in the same direction as the QRS complex in the presence of LBBB, or ST elevation > 5 mm in V1–V3, or Q waves in consecutive lateral leads (Sgarbossa criteria).
Non-MI (Non-Myocardial Infarction)

Old inferior MI pattern without acute injury:
– Q wave in lead III > 1 mm (1 small square)
– Q wave in aVF > 0.5 mm
– Q wave of any size in lead II
– No ST-segment elevation
Normal sinus rhythm or any arrhythmia without acute ischemic changes.
Output: Respond only with one of the two labels:
→ MI
→ Non-MI

Rules:

Do not explain your reasoning or provide probabilities.
Choose the closest match even if uncertain.
[Use the uploaded ECG image for interpretation.]



