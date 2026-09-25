# ArtSense AI

PROJECT: AI Art Style Analyzer

Build a complete, production-quality AI-powered web application called "ArtSense AI — Art Style Analyzer".

The purpose of this project is to analyze uploaded artworks using Computer Vision, Machine Learning, and AI and provide a detailed analysis of the artwork's artistic style, medium, colors, texture, composition, and other visual characteristics.

This is a portfolio-level project intended for a Computer Science student with an art/painting background. The application should demonstrate real AI/ML engineering rather than simply sending an image to an LLM and asking it to guess the style.

1. CORE OBJECTIVE

The application should allow a user to:

Upload an artwork image.

Analyze the artwork using trained/fine-tuned computer vision models.

Predict the artistic style.

Predict the likely artistic medium.

Analyze the color palette.

Analyze visual texture.

Analyze contrast and brightness.

Analyze basic composition characteristics.

Display confidence scores.

Generate a human-readable explanation of the results.

Generate a complete visual analysis report.

Allow users to analyze multiple artworks and create an "Artist Style Profile."

Optionally find visually similar artworks using image embeddings.

The system must clearly distinguish between:

AI model predictions

Computer-vision measurements

AI-generated explanations

Do not present subjective artistic judgments as objective facts.

2. MAIN ART STYLE CLASSES

The first version should classify artworks into these categories:

Realism

Impressionism

Expressionism

Surrealism

Abstract

Cubism

Minimalism

Pop Art

Anime/Manga

Digital Art

The architecture must make it easy to add additional styles later.

3. MEDIUM CLASSIFICATION

Create a separate classification system for artistic medium.

Initial classes:

Pencil / Graphite

Ink

Watercolor

Oil Painting

Acrylic

Charcoal

Digital Art

The style classifier and medium classifier should be separate models or separate classification heads.

Example:

Style:
Realism — 87%

Medium:
Pencil — 93%

Do NOT assume that style and medium are the same thing.

4. AI/ML APPROACH

Do NOT build the project as:

Image → LLM → Guess

Instead, implement a genuine computer-vision pipeline.

Recommended architecture:

Image
↓
Preprocessing
↓
Pre-trained Vision Model
↓
Transfer Learning / Fine-Tuning
↓
Style Classification
↓
Medium Classification

In parallel:

Image
↓
OpenCV / Computer Vision
↓
Color Analysis
Texture Analysis
Contrast Analysis
Composition Analysis

Then combine the results into a final analysis report.

5. MACHINE LEARNING MODEL

Use Python and PyTorch.

Start with transfer learning rather than training a deep neural network completely from scratch.

Preferred models:

ResNet50
OR

EfficientNet
OR

Vision Transformer (ViT)

Choose the model that provides the best balance between accuracy, training requirements, inference speed, and available hardware.

The implementation should allow the model to be replaced later.

The code should be modular.

Example:

models/
style_classifier.py
medium_classifier.py

training/
train_style.py
train_medium.py
evaluate.py

6. DATASET STRUCTURE

Create a clean dataset structure:

dataset/

styles/
    realism/
    impressionism/
    expressionism/
    surrealism/
    abstract/
    cubism/
    minimalism/
    pop_art/
    anime_manga/
    digital_art/

mediums/
    pencil/
    ink/
    watercolor/
    oil/
    acrylic/
    charcoal/
    digital/


The application should NOT automatically download copyrighted artwork from random websites.

The README must explain that the project should use:

public-domain datasets

appropriately licensed datasets

datasets with permission for machine-learning use

The dataset source and license must be documented.

7. DATA PREPROCESSING

Implement an image preprocessing pipeline.

Requirements:

Convert images to RGB.

Resize images.

Normalize images.

Handle corrupted images.

Handle extremely small images.

Remove unsupported image formats where necessary.

Implement training augmentation.

Possible augmentation:

Random horizontal flip

Small rotations

Random crop

Slight brightness adjustment

Slight contrast adjustment

Normalization

Avoid aggressive transformations that could destroy artistic characteristics.

Create reusable preprocessing functions.

8. DATASET SPLITTING

Split data into:

Training set: 70%

Validation set: 15%

Test set: 15%

Ensure that the same artwork does not appear in multiple sets.

Use reproducible random seeds.

Document the split.

9. STYLE CLASSIFICATION OUTPUT

For an uploaded artwork, the model should return probabilities.

Example:

Style predictions:

Realism: 0.87
Impressionism: 0.06
Expressionism: 0.03
Surrealism: 0.02
Abstract: 0.01
Other: ...

The UI should display:

Predicted Style:
Realism

Confidence:
87%

Also display the top 3 predictions rather than hiding all alternative possibilities.

10. MEDIUM CLASSIFICATION OUTPUT

Example:

Predicted Medium:
Pencil / Graphite

Confidence:
93%

Top alternatives:

Ink — 4%
Charcoal — 2%
Digital — 1%

11. COLOR ANALYSIS

Implement color analysis using Python/OpenCV.

Extract:

Dominant colors

Average brightness

Saturation

Contrast

Warm/cool tendency

Number of dominant colors

Use K-Means clustering or another appropriate method to extract the dominant palette.

Example output:

Dominant Palette:

#2C2521
#7B6250
#C8A98C
#E7DED4

Generate a visual palette in the frontend.

Also classify the palette approximately as:

Warm

Cool

Neutral

Mixed

Do not claim that these categories are artistic truths. They are visual measurements/heuristics.

12. TEXTURE ANALYSIS

Use computer vision techniques to analyze visual texture.

Possible features:

Edge density

Sharpness

Local variance

Texture strength

Fine vs coarse visual patterns

Return a simple interpretation such as:

Texture:
Fine / Moderate / Strong

Also provide the underlying measurements where appropriate.

13. CONTRAST AND BRIGHTNESS

Calculate:

Average luminance

Contrast

Brightness distribution

Dark/light pixel distribution

Example:

Brightness:
Medium

Contrast:
High

Use charts or visual indicators.

14. COMPOSITION ANALYSIS

Implement basic computer-vision-based composition analysis.

Possible features:

Approximate visual center

Edge distribution

Symmetry

Negative-space estimation

Subject/focal region estimation where technically feasible

Horizontal/vertical balance

Rule-of-thirds regions

Important:

Do NOT claim that the system can objectively determine whether an artwork has "good" or "bad" composition.

Use wording such as:

"Visual balance appears relatively centered."

or:

"Edge density is concentrated toward the right side."

15. ARTWORK ANALYSIS DASHBOARD

After upload, display:

ARTWORK PREVIEW

STYLE

Realism
87%

Top alternatives:
Impressionism 6%
Expressionism 3%

MEDIUM

Pencil / Graphite
93%

COLOR

Palette:
[Color] [Color] [Color] [Color]

Temperature:
Warm

Saturation:
Medium

Contrast:
High

TEXTURE

Fine texture

COMPOSITION

Visual center:
Center-right

Symmetry:
Low

Negative space:
Moderate

Make the dashboard visually attractive and suitable for screenshots on LinkedIn.

16. AI EXPLANATION SYSTEM

After the computer-vision analysis, generate a natural-language explanation.

The explanation should be based ONLY on the actual detected features and model results.

Example input:

Style = Realism
Confidence = 87%
Medium = Pencil
Color = Monochromatic
Contrast = High
Texture = Fine

The explanation might say:

"This artwork was classified as most consistent with Realism. The model detected visual characteristics associated with realistic artwork, while the fine texture and monochromatic palette are consistent with pencil-based rendering."

Do not invent visual characteristics that were not detected.

If using an external LLM API, isolate the integration in:

services/ai_explanation.py

Make the LLM provider configurable through environment variables.

17. ARTIST PROFILE FEATURE

Create a feature where the user can upload multiple artworks.

Allow:

5–20 artworks.

Analyze them collectively.

Generate an Artist Style Profile.

Example:

ARTIST STYLE PROFILE

Primary Style:
Realism

Secondary Characteristics:
Minimalism
High contrast
Fine line work

Common Medium:
Pencil / Ink

Color Profile:
Monochromatic / Neutral

Texture:
Fine

The profile should be based on aggregate model predictions rather than arbitrary AI-generated claims.

Display charts showing how frequently each style/medium appears.

18. SIMILAR ARTWORK FEATURE

Implement an optional advanced feature using image embeddings.

Pipeline:

Artwork
↓
Vision Encoder
↓
Embedding Vector
↓
Vector Similarity Search
↓
Similar Artworks

Use cosine similarity.

For the first version, FAISS or another lightweight vector database is acceptable.

Display:

Similar Artwork #1 — 91%
Similar Artwork #2 — 87%
Similar Artwork #3 — 83%

Clearly label this as visual similarity, NOT proof of copying, authorship, or artistic influence.

19. BACKEND

Use:

Python
FastAPI

Recommended endpoints:

POST /api/analyze

POST /api/analyze/style

POST /api/analyze/medium

POST /api/analyze/colors

POST /api/analyze/texture

POST /api/analyze/composition

POST /api/artist-profile

POST /api/similar

GET /api/health

Use Pydantic models for request/response validation.

Return clean JSON.

Example:

{
"style": {
"prediction": "Realism",
"confidence": 0.87,
"alternatives": []
},
"medium": {
"prediction": "Pencil",
"confidence": 0.93
},
"color": {
"temperature": "Warm",
"saturation": "Medium",
"contrast": "High",
"palette": []
},
"texture": {},
"composition": {}
}

20. FRONTEND

Use:

React + TypeScript

or

Next.js + TypeScript.

Create a modern art-focused UI.

Pages:

Home

Analyze Artwork

Analysis Results

Artist Profile

About

Model / Technology

21. DESIGN DIRECTION

The design should feel like a premium digital art platform.

Use:

Clean typography

Large artwork previews

Elegant cards

Subtle animations

Minimal interface

Artistic but professional layout

Responsive design

Dark/light mode if practical

Avoid making the interface look like a generic AI dashboard.

The artwork itse

This project was built with [Lovable](https://lovable.dev).

## Build with Lovable

Continue developing this project in the [Lovable editor](https://lovable.dev/projects/79267451-993a-54b9-8bf5-3acc572ca123).

- **Ship faster**: describe what you want to build and Lovable handles the code.
- **Stay in sync**: every change made in Lovable is committed straight to this repository.
- **Full ownership**: this code is yours. Push to `main` on GitHub and your changes sync back into Lovable, ready for your next prompt.

## Development

Prefer working locally? You need Node.js and npm — [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating).

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm run dev
```
