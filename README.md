# SportsSimulations

A statistical simulation framework for modeling NFL play outcomes and in-game 
decision-making, built around a case study of 4th & Goal decisions: when should 
a team go for it versus kick a field goal?

This project was originally developed as part of an advanced sports analytics 
course at the University of Virginia, and has been extended and cleaned up here 
as a standalone project.

## Overview

The core question: **in a 4th & Goal situation, in what scenarios should a team 
go for it versus kick a field goal, and what factors drive that decision?**

The simulation combines several modeling components:
- **Field goal success probability** - logistic regression on field position
- **Fourth down decision modeling** - multinomial regression over go/punt/kick
- **Yards gained** - mixture-of-normals models, fit separately by play type and field zone
- **Win probability** - a base model calibrated on score differential and time 
  remaining, with adjustments for late-game situations
- **Decision criterion** - a win-probability-based rule (rather than expected 
  points) for recommending go-for-it vs. field goal, accounting for score 
  differential, yards to go, and time remaining

## Key Findings

- **Score differential** is the primary driver of the go-for-it decision — more 
  so than yards to go or time remaining
- Teams trailing by 4–8 points in the final 5 minutes should be considerably 
  more aggressive on 4th & Goal, since a field goal alone leaves them behind
- The traditional "take the points inside 3 yards" heuristic holds — except at 
  high score differentials, where going for it dominates regardless of distance
- Yards to go matters most as a secondary factor, particularly around a 
  ~3-yard threshold

Full methodology, results, and discussion are in the report: [`docs/4th-and-goal-report.pdf`](docs/4th-and-goal-report.pdf)

## Repository Structure

R/       # Simulation and modeling scripts
data/    # Fitted models, decision matrices, and analysis outputs (.rds, .csv)
docs/    # Final written report

## Contributors

Maximilian Van Zandt, Andrew Tran, Zain Bangash, JJ Sutkus

Adjust the file path in the report link if the PDF ends up named something other than `4th-and-goal-report.pdf`. Once this is in, your repo should read cleanly to anyone landing on it cold.
