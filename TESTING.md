# Bilingual release tests

Run each case in a new Codex chat with the plugin installed. Check both activation and output quality. Use anonymized sample data only.

## English

1. Direct activation: `Build a financial model for a small coffee shop in Manchester.`
   Expected: the skill activates, starts with the project brief, uses English labels, and asks only for missing inputs.
2. Indirect activation: `I need to understand the cash needed to open a two-chair dental clinic.`
   Expected: the skill recognizes a financial-modeling task and proposes the relevant first stage.
3. Existing model audit: `Audit the attached spreadsheet and identify broken formulas and unsupported assumptions.`
   Expected: it inspects the existing model first and does not restart the full workflow.
4. Locale check: `Use GBP, UK date formatting, and English spreadsheet labels.`
   Expected: currency, dates, separators, filenames, and narrative output follow the requested locale.

## Russian

1. Прямой вызов: `Собери финансовую модель небольшой пекарни в Самаре.`
   Ожидание: скилл начинает с паспорта проекта, использует русский язык и задаёт только недостающие вопросы.
2. Косвенный вызов: `Хочу понять, сколько денег потребуется для открытия салона на три рабочих места.`
   Ожидание: скилл распознаёт задачу финмоделирования и предлагает подходящий первый этап.
3. Проверка готовой модели: `Проверь приложенный Excel и найди ошибки в формулах и допущениях.`
   Ожидание: сначала проводится аудит существующего файла без перезапуска полного маршрута.
4. Проверка локали: `Используй рубли, российский формат дат и русские названия листов.`
   Ожидание: валюта, даты, разделители, имена файлов и пояснения соответствуют запросу.

## Unsupported-language boundary

Prompt: `Construye un modelo financiero para una cafetería.`

Expected: the skill says that the current release supports English and Russian and asks the user to choose one. It must not claim tested Spanish support.

## Release acceptance

- All calculations are formulas linked to inputs.
- Every material assumption has a source or an estimate label.
- Approval gates stop the workflow at the documented points.
- No personal or company identifiers appear in research queries or public outputs.
- English and Russian outputs use consistent financial terminology throughout each project.
