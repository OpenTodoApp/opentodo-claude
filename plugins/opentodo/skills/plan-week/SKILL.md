---
name: plan-week
description: Plan the user's coming week in OpenTodo, spreading open work over the days within the time they have. Use when the user asks to plan their week, or runs /opentodo:plan-week.
---

# Plan the week in OpenTodo

Follow the `opentodo-mcp` skill's rules throughout.

If this session offers the OpenTodo MCP prompt `plan-week`, use it: it is the server's own week-planning workflow and takes the user's notes, working hours and minutes of work per day. Otherwise do the same by hand:

1. Read the week with `list_tasks`: `view: "today"`, then `view: "upcoming"` with `due_to` seven days ahead, and `view: "anytime"` for undated work worth placing. Pass the user's time zone as `timezone`. Note deadlines (`deadline`) and estimates (`estimate_minutes`).
2. Ask how much time they have per day if they haven't said (default 8 hours), and which days are off.
3. Draft a plan: work with deadlines first, then by priority (1 is highest), keeping each day within its time and leaving room for the unexpected. Tasks without a date can stay without one; use `start` to defer and `start: "someday"` to park.
4. Show the plan as a list of changes per day, with each task's id and its new date, and wait for the user's yes or edits.
5. Apply only what they confirmed, with `schedule_tasks` (due dates) and `update_tasks` (start, deadline, evening), then report what changed with the ids, and that each change can be undone from the task's history.
