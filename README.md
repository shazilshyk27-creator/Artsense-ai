# 🎨 ArtSense AI

### AI-Powered Artwork Style & Visual Analysis

ArtSense AI is a web-based artwork analysis platform that combines **browser-based computer vision measurements** with **AI-powered visual classification** to analyze artwork.

Users can upload an artwork and receive an interactive analysis covering:

- 🎭 Artistic style
- 🖌️ Artistic medium
- 🎨 Dominant color palette
- 💡 Brightness & contrast
- 🌡️ Color temperature
- 🧩 Texture characteristics
- 📐 Composition
- 🎯 Symmetry & negative space
- 📊 Style and medium confidence distributions
- 📝 AI-generated explanation

The project was created as a portfolio project combining my interests in **Computer Science, Artificial Intelligence, Computer Vision, and Art**.

---

## ✨ Features

### 🖼️ Artwork Upload

Upload an artwork image directly through the ArtSense AI interface.

The image is resized and processed in the browser before analysis.

---

### 🎭 Artistic Style Classification

ArtSense AI currently analyzes artwork across the following style categories:

- Realism
- Impressionism
- Expressionism
- Surrealism
- Abstract
- Cubism
- Minimalism
- Pop Art
- Anime/Manga
- Digital Art

The system returns a probability distribution across the available styles rather than presenting the prediction as an absolute artistic fact.

---

### 🖌️ Medium Classification

Style and medium are treated as separate classification tasks.

Supported medium categories include:

- Pencil / Graphite
- Ink
- Watercolor
- Oil Painting
- Acrylic
- Charcoal
- Digital Art

For example:

```text
Style:
Impressionism — 72%

Medium:
Watercolor — 84%
