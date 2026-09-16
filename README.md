# prd-grill

Скилл для Claude, который проводит интервью по твоему проекту и собирает мини-PRD перед работой с AI-агентом.

Логика интервью основана на [grill-me](https://github.com/mattpocock/skills) Мэтта Покока: вопросы идут раундами по дереву решений, у каждого вопроса есть варианты ответа, рекомендация и объяснение, на что влияет решение. Шаблон PRD, примеры и промпты взяты из учебного лендинга [PRD для агентов](https://prd-agentic-lab.vercel.app).

## Что получится

Файл `PRD.md` из 9 блоков:

1. Контекст
2. Цель v1
3. Пользователь
4. Основной сценарий
5. Функциональные требования
6. Нефункциональные требования
7. Не входит в v1
8. Критерии готовности
9. Вопросы и риски

После PRD скилл предлагает первый промпт агенту: понимание, реализация, проверка.

## Установка

### Claude Code: через маркетплейс плагинов

```
/plugin marketplace add YOUR_GITHUB/prd-grill
/plugin install prd-grill@ai-lab-skills
```

### Claude Code, Codex, Cursor и другие агенты: через skills CLI

```bash
npx skills add https://github.com/YOUR_GITHUB/prd-grill --skill prd-grill
```

### Вручную

```bash
git clone https://github.com/YOUR_GITHUB/prd-grill.git
cp -r prd-grill/skills/prd-grill ~/.claude/skills/
```

Для одного проекта положи папку в `.claude/skills/` внутри проекта.

### Claude.ai (веб и десктоп)

Скачай [`dist/prd-grill.skill`](dist/prd-grill.skill) и загрузи его в разделе скиллов в настройках Claude.

## Как запустить

Напиши `/prd-grill` или просто опиши идею:

> Хочу сделать бота для записи клиентов в салон. Помоги собрать PRD.

Каждый раунд — один вопрос: варианты ответа, строка «На что влияет» и рекомендация. После ответа скилл показывает, что изменилось в проекте, и задает следующий вопрос. В Claude Code вопросы приходят как меню с выбором; в чате — текстом, отвечай буквой, «ок» на рекомендацию или своими словами. «Не знаю» — нормальный ответ, он попадет в блок рисков.

## Структура

```
skills/prd-grill/
├── SKILL.md                     # логика интервью
└── references/
    ├── prd-template.md          # шаблон PRD
    ├── question-map.md          # вопросы и красные флаги по 9 блокам
    ├── example-prd.md           # пример заполненного PRD
    └── next-steps.md            # промпты агенту после PRD
```

---

Сделано для [Agentic Lab](https://www.ai-lab-agents.com). Видео и конспект: [prd-agentic-lab.vercel.app](https://prd-agentic-lab.vercel.app)
