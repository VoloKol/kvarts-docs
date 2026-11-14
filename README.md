# Кварц — документация платформы сбора телеметрии

[![Docs CI](https://github.com/VoloKol/kvarts-docs/actions/workflows/deploy.yml/badge.svg)](https://github.com/VoloKol/kvarts-docs/actions/workflows/deploy.yml)

> **Демонстрационный проект для портфолио технического писателя.**
> Компания и продукт вымышлены: названия, параметры и данные созданы для демонстрации навыков.

Портал документации вымышленной платформы «Кварц»: шлюз телеметрии Кварц-T1 (аппаратное изделие) и облачный Кварц API.

## Что демонстрирует проект

- **Docs as Code**: контент в Markdown, ревью через pull request, автосборка и публикация из CI;
- **Diplodoc** (YFM → статический сайт) — движок портала;
- **RAG-ориентированный стайлгайд**: правила написания статей, чтобы документация работала и для людей, и для LLM/RAG-ассистентов — [docs/style-guide-rag.md](docs/style-guide-rag.md);
- **Автопроверки контента**: markdownlint-cli2 (структура разметки) и Vale с собственным стилем `KB` (языковые правила стайлгайда);
- **Документация для ИИ**: сборка генерирует `llms.txt` и `llms-full.txt` для LLM-ассистентов (флаг `--llms` Diplodoc);
- **В планах**: API-референс из OpenAPI 3.1, диаграммы как код (Mermaid), образец эксплуатационной документации по ЕСКД (ГОСТ 2.601/2.610).

## Структура репозитория

| Путь | Назначение |
|---|---|
| `docs/` | Исходники статей портала (YFM) |
| `docs/style-guide-rag.md` | RAG-стайлгайд: структура, язык, метаданные, YFM-разметка |
| `styles/KB/` | Правила Vale: абсолютные даты, самодостаточность чанков, осмысленные ссылки |
| `.markdownlint-cli2.jsonc` | Конфиг markdownlint-cli2 |
| `.vale.ini` | Конфиг Vale |
| `.github/workflows/deploy.yml` | CI: lint → build → deploy на GitHub Pages |

## Локальная работа

```bash
npm ci           # установка зависимостей (node 20+)
npm run lint     # markdownlint-cli2 по всем .md
npm run build    # сборка портала в build/ (+ llms.txt, llms-full.txt)
```
