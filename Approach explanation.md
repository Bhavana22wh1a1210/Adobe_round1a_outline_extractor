# Approach Explanation 

## 🧩 Round 1A – PDF Outline Extractor

### Objective
To extract a structured outline from a PDF file, including the document title and headings (H1, H2, H3), with accurate page numbers and a valid JSON output.

### Methodology
We used `pdfminer.six` to parse the layout and text of the PDF file. Since heading detection cannot rely solely on font size, our approach uses a set of layout-aware heuristics:
- **Title** is inferred from the filename (as no standard metadata is available).
- **H1** is detected based on ALL CAPS headings with 8–10 words max.
- **H2** is identified using Title Case headings (e.g., Introduction to AI).
- **H3** is matched using short bold-style or small heading phrases.

Each heading's text and its corresponding page number are stored in a hierarchical JSON format, as per the Adobe-provided schema.

### Highlights
- Runs under 10 seconds per PDF
- No model dependencies — entirely rule-based and lightweight
- Robust to heading variations (works across structured and semi-structured PDFs)

