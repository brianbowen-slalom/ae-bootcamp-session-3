# Product Requirements Document (PRD) - Todo App Upgrade

## 1. Overview

Upgrade the basic Todo app so it is more useful without going overboard, while keeping the scope to a simple, teachable MVP. The upgrade adds due dates, priorities, and filters to help users organize tasks better, while keeping storage local and avoiding backend changes.

---

## 2. MVP Scope

- Add a `dueDate` field to tasks.
- Make `dueDate` optional.
- Require `dueDate`, when present, to use ISO `YYYY-MM-DD` format.
- Ignore invalid `dueDate` values and treat them as absent.
- Add a `priority` field to tasks.
- Restrict `priority` to `P1`, `P2`, or `P3`.
- Default `priority` to `P3`.
- Require `title` for each task.
- Display priority visually using color-coded badges.
- Add filter views for `All`, `Today`, and `Overdue`.
- Show completed tasks in the `All` view.
- Hide completed tasks in the `Today` and `Overdue` views.
- Keep storage local only.
- Do not make backend changes.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks.
- Sort tasks with overdue tasks first, then by priority (`P1` to `P3`), then by due date ascending, with tasks without a due date last.

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation.
- External storage.