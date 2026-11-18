
<%*
const title = await tp.system.prompt("Заглавие на Linux урока");

if (!title) {
    new Notice("Не е въведено заглавие!");
    return;
}

const folder = "Лекции";
const files = app.vault.getMarkdownFiles()
    .filter(f => f.parent?.path === folder)
    .filter(f => /^\d{2} - /.test(f.basename));

const numbers = files.map(f => Number(f.basename.slice(0, 2)));
const nextNumber = String(
    Math.max(0, ...numbers) + 1
).padStart(2, "0");

const filename = `${nextNumber} - ${title}`;
const target = `${folder}/${filename}.md`;

if (app.vault.getAbstractFileByPath(target)) {
    new Notice("Тази лекция вече съществува!");
    return;
}

await tp.file.move(target);

const date = tp.date.now("YYYY-MM-DD");
const link = `[[${filename}]]`;

tR += `---
type: linux-lecture
date: ${date}
status: in-progress
tags:
  - linux
  - lecture
---

# ${title}

## 🎯 Цели на урока

- [ ] 

## 📖 Теория

### Основни понятия


## 💻 Linux команди

| Команда | Описание | Пример |
|---|---|---|
| | | |

## 🧪 Практически упражнения

- [ ] 

## 📝 Важни бележки


## ❓ Въпроси за преговор

- [ ] 

## 🔗 Свързани лекции


## 📚 Източници

- Udemy – Complete Linux Training Course

---

**Дата:** ${date}
**Статус:** В процес на изучаване
`;
%>
