# G6 Invigilation Arrangement Generator

Builds the Grade 6 exam invigilation workbook for St. Hilary's School (Primary)
from four files, entirely in the browser.

**Live:** https://iverlee83.github.io/g6-invigilation/

## Inputs

1. **Teaching Roster** (xlsx) — Campus, Class, HR, HR, Chi, Eng, Maths, G.S.H., Sci, Music, P.E., V.A.
2. **G6 Exam Timetable** (csv) — Day, Date, Grade, Session, Start_Time, End_Time, Subject, Notes
3. **Teacher Timetable** (xlsx) — one sheet per teacher; used to detect lesson-swap conflicts
4. **Cross Campus Teachers** (xlsx) — Name of teacher, Initials, Mon–Fri

## Output

One Excel workbook: a Balance sheet, one sheet per exam day, and a Lesson Swap
sheet split into Tai Po / Mong Kok / Diamond Hill blocks. Each day sheet also
carries an SEN Invigilation table, the cross-campus list for that day, a
teacher-per-day cross-check and a teacher duty count.

## Rules applied

- Invigilator: own-teacher rule, then same grade / same subject / different
  class on the same campus, then same campus / same subject / different grade,
  then any same-campus teacher. Diamond Hill has one G6 class, so its own
  subject teacher invigilates directly.
- Science Prediction day: invigilator is the Science teacher of the
  neighbouring class; duty teachers are drawn from the class's own subject
  teachers, filled per time slot, at most 3 lessons each.
- Lesson 5: the teacher who normally has lesson 5 with that class; if they are
  already on 4 invigilation lessons, the lesson 6 / study hall teacher instead.
- Recess, Dismissal and SEN slots are left blank for manual completion.
- Clashes are flagged on the Lesson Swap sheet only — nothing is swapped
  automatically.

## Privacy

Every file is read and processed in your own browser. Nothing is uploaded to
GitHub or anywhere else, and the generated workbook downloads straight to your
computer.
