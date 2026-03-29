# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :TANGUTURI TEJASWINI 
**Student ID    :2310040077 
**Date Submitted: 29-03-2026

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
count_clashes() calculates the number of conflicts in the generated timetable such as room or teacher clashes. It evaluates how good the timetable is. A value of 0 means a perfect timetable with no conflicts.
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
generate_neighbor() creates a new timetable by making a small change to the current timetable, such as swapping two class slots. This helps explore different possible schedules. The new timetable is slightly different from the current one.
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):

```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
This condition decides whether the new timetable should replace the current one. If the new solution is better (delta < 0) it is always accepted. Sometimes worse solutions are accepted with a probability to help the algorithm escape local minima and explore better solutions.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed |1379 |
| Clashes at iteration 1 |12 |
| Final best clashes | 3|
| Did SA reach 0 clashes? (Yes / No) | NO|

**Copy the printed timetable output here:**
```
 Final Timetable
------------------------------------------
  Slot 1:  Geography
  Slot 2:  Chemistry, English
  Slot 3:  History, Computer Science, Economics
  Slot 4:  Biology, Statistics
  Slot 5:  Mathematics, Physics
------------------------------------------
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
The number of clashes decreases quickly during the initial iterations, showing that the algorithm rapidly improves the timetable. After that the curve flattens near 3 clashes, indicating slower improvements as the algorithm converges.
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        |         8     |       31               |         NO           |
| 0.95        |           3    |        135              |       NO             |
| 0.995       |            3   |        1379              |       NO             |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
The cooling rate affects how quickly the temperature decreases and how much the algorithm explores possible solutions. With a fast cooling rate like 0.80, the temperature drops quickly, so the algorithm stops exploring early and results in more clashes. With 0.95, the algorithm runs longer and finds a better solution with fewer clashes. The slowest cooling rate 0.995 allows the algorithm to explore the most solutions, resulting in a better timetable though it takes more iterations
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
The cooling rate 0.995 gave the best result because the temperature decreases slowly, allowing the algorithm more time to explore different timetable configurations and avoid getting stuck in poor solutions.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 |3 |The algorithm gradually reduced clashes but did not reach a perfect timetable.|
| 2 — Cooling rate | cooling_rate = 0.995 |3 |Slower cooling allows the algorithm to explore more solutions and produce better results.|

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```

```
Simulated Annealing gradually improves a solution by exploring many neighboring possibilities. The temperature controls how much the algorithm explores different solutions. A slower cooling rate allows more exploration and usually gives better results. Accepting slightly worse solutions sometimes helps the algorithm escape local optima and find a better overall timetable.
---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
