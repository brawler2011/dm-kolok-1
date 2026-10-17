# Дискретная математика · III семестр · Коллоквиум 1

[![Build PDF](https://github.com/brawler2011/dm-kolok-1/actions/workflows/pdf.yml/badge.svg)](https://github.com/brawler2011/dm-kolok-1/actions/workflows/pdf.yml)

[Скачать актуальный PDF](https://github.com/brawler2011/dm-kolok-1/releases/download/latest/notes-colored.pdf)

Конспект переработан по рукописному файлу
`дм _261012_193210.pdf` (60 страниц). Сохранены 21 билет по `questions.md`;
темы вне списка билетов, не используемые в доказательствах, исключены.

Основной источник — лекции. Материал, которого в скане нет (билеты 8, 11, 12),
сохранён по Д. В. Карпову, `graphs_dk.pdf`. Ссылки на лекции используют номер
страницы PDF с 1; ссылки на книгу — печатный номер страницы.
Восстановленные детали и книжные дополнения обозначены в тексте.

Двусвязность доказывается элементарно через пути и циклы, Хватал — через
максимальный негамильтонов надграф, Кирхгоф — через инцидентность и Бине–Коши,
Брукс — по Ловасу. Добавлены ориентированный критерий Эйлера и топологическая
сортировка.

Для Понтрягина–Куратовского дана лекционная **схема** через цикл и его части;
полный перебор геометрических конфигураций не приводится. Это явно оговорено в PDF.

## Файлы

- `notes-colored.pdf` — готовый конспект.
- `main.tex`, `notation.tex`, `config.tex` — основной документ, определения, оформление.
- `tickets/01.tex`–`tickets/21.tex` — билеты.
- `report.md` — сравнение исходной редакции с лекциями; после переработки сохранено как отчёт об исходном состоянии.
- `fonts/` — CMU Serif и лицензия SIL OFL.

## Сборка

Нужны LuaLaTeX, latexmk и пакеты TeX Live, включая babel-russian,
fontspec, tcolorbox, titlesec, tocloft, fancyhdr, TikZ, luaotfload,
lualibs и Latin Modern.

Установка зависимостей в Ubuntu 24.04:

```sh
sudo apt-get update
sudo apt-get install -y --no-install-recommends \
  latexmk texlive-luatex texlive-lang-cyrillic \
  texlive-latex-extra texlive-fonts-recommended
```

```sh
latexmk main.tex
cp .build/notes-colored.pdf notes-colored.pdf
```

## CI/CD

GitHub Actions собирает PDF при каждом push, pull request и ручном запуске
workflow `Build PDF`. Артефакт `notes-colored` хранится 30 дней; при ошибке
логи сборки доступны в артефакте `latex-logs` в течение 7 дней.

После успешной сборки ветки `main` PDF автоматически публикуется в релизе
[`latest`](https://github.com/brawler2011/dm-kolok-1/releases/tag/latest).
Тег `latest` перемещается на собранный коммит. Дополнительные секреты не нужны:
публикация использует встроенный `GITHUB_TOKEN`.

## Замечания

Первые два билета сохраняют повторение из списка вопросов. Лекционный
термин «путь» допускает повторения; степени матрицы считают такие пути,
а не простые. Отношение вершинной двусвязности, как в лекциях, задано на рёбрах.
