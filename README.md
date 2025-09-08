
## 🧑‍🎨 AI Image Agents – FaceLogo & CrownTopper

This repository contains two AI-powered generative agents for modifying images using **Stable Diffusion XL inpainting** and **brand-driven style integration**.  
Users can quickly swap faces with logos or add crown-like logo toppers to existing portraits.

---

### 📂 Assets
Testing assets (images, masks, example logos) are stored in this repository.  
⚠️ When referencing them in url input box, always use **raw.githubusercontent.com** URLs.

Example format:

```
First copy permalink from git repo , then replace `github.com` with `raw.githubusercontent.com` 
https://raw.githubusercontent.com/asdspal/cere-agent-testing/blob/30ff018379264530fcd36e8b509fa061147fc14b/facelogo-test/test_subject.jpg
```

---

## 1️⃣ FaceLogo Agent

The **FaceLogo Agent** replaces a detected face with a logo using a segmentation mask.  
It’s suitable for experiments with brand-styled avatars.

### 👉 Input Schema

```json
{
  "type": "object",
  "properties": {
    "prompt": {
      "type": "string",
      "description": "Optional text prompt to guide the face swap"
    },
    "maskImageUrl": {
      "type": "string",
      "description": "URL of the mask image defining the swap area"
    },
    "targetFaceUrl": {
      "type": "string",
      "description": "URL of the face to use for swapping (e.g., a logo)"
    },
    "originalImageUrl": {
      "type": "string",
      "description": "URL of the original image to modify"
    }
  },
  "required": [
    "maskImageUrl",
    "targetFaceUrl",
    "originalImageUrl"
  ]
}
```

### 📝 Example Input

```json
{
  "prompt": "Seamlessly integrate the Apple logo as a futuristic mask over the face.",
  "maskImageUrl": "https://raw.githubusercontent.com/<your-username>/<repo-name>/main/assets/face-mask.png",
  "targetFaceUrl": "https://raw.githubusercontent.com/<your-username>/<repo-name>/main/assets/apple-logo.png",
  "originalImageUrl": "https://raw.githubusercontent.com/<your-username>/<repo-name>/main/assets/test1.png"
}
```

---

## 2️⃣ CrownTopper Agent

The **CrownTopper Agent** adds a logo-shaped crown or head accessory on top of a person’s head.  
You can specify the artistic style (realistic, artistic, professional).

### 👉 Input Schema

```json
{
  "type": "object",
  "properties": {
    "style": {
      "type": "string",
      "description": "Style of the replacement",
      "enum": ["realistic", "artistic", "professional"]
    },
    "imageUrl": {
      "type": "string",
      "description": "URL of the original image to edit"
    },
    "brandLogoUrl": {
      "type": "string",
      "description": "URL of the brand logo"
    },
    "replacementPrompt": {
      "type": "string",
      "description": "Description of what to replace the masked area with"
    }
  },
  "required": [
    "imageUrl",
    "brandLogoUrl",
    "replacementPrompt"
  ]
}
```

### 📝 Example Input

```json
{
  "style": "realistic",
  "imageUrl": "https://raw.githubusercontent.com/<your-username>/<repo-name>/main/assets/test1.png",
  "brandLogoUrl": "https://raw.githubusercontent.com/<your-username>/<repo-name>/main/assets/apple-logo.png",
  "replacementPrompt": "A metallic silver crown shaped like the Apple logo, subtly glowing."
}
```

---

## 🚀 Usage Notes

- Use the **raw.githubusercontent.com** link for all image assets (not the GitHub “blob” link).
- The `facelogo` agent works best when the **mask tightly covers the face**.
- The `crown-topper` agent works best with **head/portrait photos** where the crown position is clear.
- Small, descriptive prompts (e.g., *“minimalist glowing crown”*, *“Apple logo facemask”*) yield the best results.


