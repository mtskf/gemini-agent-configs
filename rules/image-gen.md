---
trigger: model_decision
description: When generating images using Nano Banana, the prompt must ALWAYS strictly follow the JSON format defined below.
---

# Nano Banana Image Generation Prompt Rules

When generating images using Nano Banana, the prompt must ALWAYS strictly follow the JSON format defined below.

## Prompt Schema

```json
{
  "image_type": "Define the specific medium, art style, or format of the source image.",
  "time_period_and_year": "Estimate the specific year or decade based on fashion, technology, image quality, and color grading visible in the photo.",
  "mood_and_vibe": "Describe the emotional atmosphere, energy, and intangible 'feeling' evoked by the image (e.g., the specific psychological impression it gives).",
  "subject": "Describe the main character(s) focusing on demographics, body morphology, distinct physical features, and posture.",
  "clothing": "Describe the outfit in detail, strictly specifying garment names, fabric textures, patterns, colors, and how the clothes fit on the subject.",
  "hair": "Describe the hair color, specific hairstyle name, length, and texture.",
  "face": "Describe facial features, skin texture, makeup details, and the exact facial expression.",
  "accessories": "List all visible accessories, jewelry, glasses, or held items, including their material and design details.",
  "action": "Describe the specific activity, movement, or interaction occurring in the scene.",
  "location": "Describe the environment, visible background elements, architectural style, and spatial context.",
  "lighting": "Analyze the light source, direction, color temperature, hardness/softness of the light, and shadow characteristics.",
  "camera_angle_and_framing": "Describe the vertical and horizontal angle of the camera relative to the subject (e.g., eye-level, low-angle), and the shot composition size.",
  "camera_equipment": "Estimate the likely camera type, lens focal length (e.g., wide-angle vs telephoto), aperture effect (depth of field), and film stock or digital sensor characteristics.",
  "style": "Describe the overall aesthetic, color palette, artistic technique, and visual processing style.",
  "negative_prompt": "List visual defects or unwanted elements to be excluded to ensure high quality."
}
```

## Instructions

1. **Output Format**: The output must be a single valid JSON object.
2. **Completeness**: All fields are required. If a field is not applicable, provide a reasonable default or describe it as "neutral" or "standard".
3. **Detail**: Be descriptive and specific in each field to ensure high-quality image generation.
4. **Language**: The values in the JSON should be in English (as most image generation models are optimized for English prompts), unless otherwise specified.