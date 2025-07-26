 Round 1A: PDF Outline Extractor

## 🧠 Problem Statement
Extract a structured outline from a PDF document, including:
- Title
- Headings: H1, H2, H3
- Output in a valid JSON format

### 📥 Expected Output Format:
```json
{
  "title": "Sample Title",
  "outline": [
    { "level": "H1", "text": "Introduction", "page": 1 },
    { "level": "H2", "text": "Background", "page": 2 }
  ]
}
````

---

## 📁 Project Structure

```
.
├── round1a/
│   └── main.py
├── input/
│   └── sample.pdf
├── output/
│   └── sample.json (auto-generated)
├── Dockerfile
├── requirements.txt
├── README.md
├── approach_explanation.md
```

---

## 🐳 Docker Instructions

### ✅ Build the Docker Image

```bash
docker build --platform linux/amd64 -t adobe-outline-extractor .
```

### ▶️ Run the Docker Container

```bash
docker run --rm \
  -v $(pwd)/input:/app/input \
  -v $(pwd)/output:/app/output \
  --network none adobe-outline-extractor
```

This will process all `.pdf` files in the `input/` folder and generate corresponding `.json` files in the `output/` folder.

---

## 🧰 Dependencies

Installed via `requirements.txt`:

* `pdfminer.six`

---

## ✅ Constraints Met

| Constraint                 | Status          |
| -------------------------- | --------------- |
| Runtime ≤ 10s              | ✅ Yes           |
| Model size ≤ 200MB         | ✅ No model used |
| CPU-only                   | ✅ Yes           |
| Works offline              | ✅ Yes           |
| Docker AMD64 compatibility | ✅ Yes           |

---

## 📌 Notes

* The script uses layout heuristics (e.g., text casing, font size logic) to detect heading levels.
* Title is inferred from the file name.
* No hardcoded content, fully generalizable.


