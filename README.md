# Willkommen Clinic & Gogita Dent

Лендинг стоматології (Харків) з ІІ-консультантом по цінах.

- `public/`: сайт (статичний `index.html` і фото).
- `netlify/functions/chat/`: серверна функція `POST /api/chat`. Прайс у `knowledge.mjs` генерується скриптом збірки, вручну його не правити.
- `tools/eval.mjs`: прогон типових запитань на живій моделі зі звіркою цифр.

## Змінні середовища (Netlify → Site configuration → Environment variables, scope **Functions**)

Після зміни змінних потрібен новий деплой.

| Змінна | Призначення |
| --- | --- |
| `LLM_API_KEY` | Ключ будь-якого OpenAI-сумісного API (за замовчуванням Groq). Якщо задано, має пріоритет. |
| `LLM_BASE_URL` | Необов'язково. За замовчуванням `https://api.groq.com/openai/v1`. OpenRouter: `https://openrouter.ai/api/v1`. |
| `LLM_MODEL` | Необов'язково. За замовчуванням `llama-3.3-70b-versatile`. Назви моделей у провайдерів змінюються, перевіряйте. |
| `ANTHROPIC_API_KEY` | Запасний варіант, якщо `LLM_API_KEY` не задано. Модель задає `CLAUDE_MODEL`. |

Без жодного ключа чат показує відвідувачу номер телефону клініки.

## Перевірка консультанта

```sh
LLM_API_KEY=... node tools/eval.mjs
```

Потрібен Node 22.18+. Ключ беруть із середовища й не записують у файли.
