# How to Add Notes

This site renders Markdown files served from this repository. The only two files you ever need to touch are `notes.json` and a new `.md` file.

## Workflow

1. Create a Markdown file anywhere in the repo — e.g. `notes/telecom/5g-overview.md`
2. Add one entry to `notes.json`:

```json
{
  "title": "5G Overview",
  "file": "notes/telecom/5g-overview.md",
  "category": "Telecom"
}
```

3. Commit and push. GitHub Pages serves the update in ~1 minute.

That's it — `index.html` never needs to change.

## notes.json structure

```json
[
  { "title": "Note Title",  "file": "notes/path/to/file.md", "category": "Category" },
  { "title": "Other Note",  "file": "notes/other.md",        "category": "Category" }
]
```

Notes with the same `category` are grouped together in the sidebar. Order within the file controls sidebar order.

## Supported Markdown

Standard [GFM (GitHub Flavored Markdown)](https://github.github.com/gfm/) is fully supported.

### Headings, emphasis, lists

- **bold**, *italic*, ~~strikethrough~~
- `inline code`
- Nested lists

### Code blocks with syntax highlighting

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"
```

```bash
git add notes/my-new-note.md notes.json
git commit -m "add note: my topic"
git push
```

### Tables

| Syntax    | Description |
|-----------|-------------|
| `**text**`| Bold        |
| `*text*`  | Italic      |
| `` `code` ``| Inline code|

### Task lists

- [x] Set up the notes site
- [ ] Write first real note
- [ ] Organize by category

### Blockquotes

> Key insight or quote goes here.

### Images

Place images in the repo (e.g. `notes/images/diagram.png`) and reference them relatively:

```markdown
![alt text](images/diagram.png)
```
