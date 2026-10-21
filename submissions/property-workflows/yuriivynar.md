# Здача WS6

## Дані

- Роль: dev
- Команда: property-workflows
- GitHub-логін: yuriivynar
- Ваше репо: https://github.com/yuriivynar/property-workflows
- SHA: d576e80372aadbbdf41733e783fd9b21745b8627
- Репо вимог PM: https://github.com/solomchaak/property-workflows-spec
- Прод-URL: https://property-workflows-eta.vercel.app

## PM

—

## Розробник

- Рядок «Вимоги:» з `docs/conformance.md` на SHA: Вимоги: https://github.com/solomchaak/property-workflows-spec · джерело: issues · знімок 2026-10-21
- Перший PR «Оновлення вимог»: https://github.com/yuriivynar/property-workflows/pull/2
- Журнал `docs/spec-reading.md`: https://github.com/yuriivynar/property-workflows/blob/d576e80372aadbbdf41733e783fd9b21745b8627/docs/spec-reading.md
- Питання в репо PM (щонайменше 3, з них щонайменше 1 — власне issue): https://github.com/solomchaak/property-workflows-spec/issues/13, https://github.com/solomchaak/property-workflows-spec/issues/14, https://github.com/solomchaak/property-workflows-spec/issues/15, https://github.com/solomchaak/property-workflows-spec/issues/10#issuecomment-6288873114
- PR «Специфікація» з перекладом першого зрізу: https://github.com/yuriivynar/property-workflows/pull/3 — зміна `add-workflow-runs`: кожен AC PM (AC-RUN-01…09, AC-TASK-01…09) — сценарій з тим самим ID, archive у гілці, 18 рядків матриці
- Зміна `impl-<зріз>`: https://github.com/yuriivynar/property-workflows/tree/d576e80372aadbbdf41733e783fd9b21745b8627/openspec/changes/archive/2026-10-20-impl-workflow-runs (план — PR https://github.com/yuriivynar/property-workflows/pull/4, archive — в останньому PR задачі)
- PR-и задач «Реалізація» (щонайменше 2): https://github.com/yuriivynar/property-workflows/pull/5, https://github.com/yuriivynar/property-workflows/pull/6 (після уточнень PM — ще https://github.com/yuriivynar/property-workflows/pull/10) — PM опублікував перші вимоги 19.10, пізніше за кінець 16.10, тож для C достатньо одного; злито два. Запис екрана — https://github.com/yuriivynar/property-workflows/pull/6#issuecomment-6292778564
- PR «Оновлення вимог» після уточнень PM: https://github.com/yuriivynar/property-workflows/pull/8 — знімок 2026-10-21 після відповідей PM на solomchaak/property-workflows-spec#4–#18: 12 нових AC, 4 змінені
- PR «Специфікація» зі змінами після уточнень: https://github.com/yuriivynar/property-workflows/pull/9 — зміна `clarify-workflow-runs`: MODIFIED AC-TASK-01, AC-TASK-02, AC-TASK-04, AC-TASK-07; ADDED AC-RUN-10…12, AC-TASK-10…18; реалізація змін — https://github.com/yuriivynar/property-workflows/pull/10
- AC, які ви реалізували: AC-RUN-01…AC-RUN-12, AC-TASK-01…AC-TASK-18 — усі 30 «реалізовано» (змінені AC-TASK-01/02/04/07 і нові AC — у PR https://github.com/yuriivynar/property-workflows/pull/10)

## Бонус E

`/opsx:verify impl-workflow-runs` + власний розбір: https://github.com/yuriivynar/property-workflows/pull/7 (звіт, вердикт по кожній знахідці й виправлення — в описі PR).

План заархівовано в останньому PR задачі, а OpenSpec CLI бачить лише активні зміни, тому процедуру `verify.md` (кроки 4–8) виконав окремий агент без контексту реалізації — на архівних артефактах і канонічних специфікаціях (`skip_specs: true`). Результат: CRITICAL 0, WARNING 3, SUGGESTION 5. Справжні: W1 — за AC-TASK-03 менеджер без задач у запуску після відмови бачив «Run not found» без повідомлення (тест з AC ID і `ac:coverage` були зелені, бо перевіряли відображення коду в текст, а не екран); W2 — форма обрізала NBSP, а база ні (два втілення одного правила розходились на символах, яких не було в тестових даних); W3 — частина написів поза `messages.ts`, всупереч design; S2 — тест, що проходив порожньо, запущений окремо; S3 — незакриті PGlite і OOM при паралельному запуску. Посилення: S1 (FK задача → розділ того самого шаблону). Смак: S4 (форма не зберігає введене після помилки). Хибне: «не git-репо». Висновок: verify ловить розбіжності «AC ↔ екран», «правило в коді ↔ правило в базі» і «код ↔ design», яких не бачать ні тести з AC ID, ні `ac:coverage`; але він не замінює e2e на екрані й плутається в середовищі. Усі справжні знахідки виправлено в PR #7 новою міграцією й тестами.
