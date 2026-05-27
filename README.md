# FitLife Architecture Documentation

**Документация архитектуры FitLife в формате C4-модели с использованием PlantUML.**

Проект содержит архитектурную документацию системы FitLife в формате **C4 model** с использованием **PlantUML**.  
Диаграммы хранятся в текстовом виде (`.puml`), а их растровые версии (`.png`) **генерируются автоматически** через GitHub Actions при каждом изменении в ветке `main`.

## 🚀 Автоматическое обновление диаграмм

- Разработчик редактирует `.puml` файлы локально (или через веб-интерфейс GitHub).
- После пуша в ветку `main` запускается GitHub Actions workflow `PlantUML Diagrams`.
- Workflow:
  - Устанавливает Java и PlantUML на виртуальную машину Ubuntu.
  - Генерирует `.png` из всех `.puml` файлов в папке `diagrams/`.
  - Коммитит и пушит новые/изменённые `.png` обратно в репозиторий.
- В результате в репозитории всегда есть актуальные картинки диаграмм, которые можно просматривать прямо на GitHub без установки PlantUML.



## 📁 Структура репозитория

```
FitLife/
├── .github/
│ └── workflows/
│ └── plantuml.yml # GitHub Actions для автогенерации картинок
├── diagrams/
│ ├── context/ # Уровень L1 (контекст)
│ │ ├── FitLife_Context_User.puml
│ │ └── FitLife_Context_Admin.puml
│ ├── container/ # Уровень L2 (контейнеры)
│ │ └── FitLife_Container.puml
│ ├── component/ # Уровень L3 (компоненты)
│ │ └── FitLife_Component_WebApp.puml
│ └── code/ # Уровень L4 (классы)
│ └── FitLife_Code_Membership.puml
├── src/ # Исходный код проекта (не относится к диаграммам)
│ ├── main/
│ └── test/
├── .gitignore
└── README.md
```

## Структура
- `diagrams/context/` – контекстные диаграммы (уровень L1)
- `diagrams/container/` – диаграммы контейнеров (уровень L2)
- `diagrams/component/` – диаграммы компонентов (уровень L3)
- `diagrams/code/` – диаграммы классов / кода (уровень L4)


## 🖼️ Просмотр диаграмм

- **В GitHub**: просто откройте любой `.png` файл в папке `diagrams/` — он отобразится в браузере.
- **Локально** (macOS + VS Code):
  - Установите расширение PlantUML (jebbs).
  - Установите Graphviz: `brew install graphviz`.
  - Настройте `settings.json`:  
    `"plantuml.render": "Local"`,  
    `"plantuml.graphvizDot": "/opt/homebrew/bin/dot"`.
  - Нажмите `⌥ Option + D` для предпросмотра.

## 🔧 Используемые технологии

- [PlantUML](https://plantuml.com/) – текстовое описание диаграмм
- [C4-PlantUML](https://github.com/plantuml-stdlib/C4-PlantUML) – макросы для C4 модели
- [GitHub Actions](https://github.com/features/actions) – CI/CD для автоматической генерации PNG
- Git – контроль версий диаграмм

## 📝 Как вносить изменения

1. Клонируйте репозиторий:
   ```bash
   git clone https://github.com/ваш-аккаунт/FitLife.git
   cd FitLife

**Примечание:** Исходные `.puml` остаются единственным источником правды (single source of truth). Автоматические коммиты с картинками не запускают новый workflow (благодаря флагу `[skip ci]`).