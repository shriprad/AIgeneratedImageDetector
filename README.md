# 🔬 AI Image Detector Pro

A comprehensive multi-layer forensic analysis tool for detecting AI-generated images.

## Features

### 6 Detection Layers

| Layer | What It Checks | Reliability |
|-------|---------------|-------------|
| **Layer 1: AI Markers** | C2PA manifests, IPTC DigitalSourceType, Software Agent | ~99% when found |
| **Layer 2: Camera Authenticity** | Make, Model, Lens, GPS, ISO, Aperture, etc. | High for proving real |
| **Layer 3: File Structure** | Dimensions, format, EXIF count, anomalies | Medium |
| **Layer 4: Pixel Forensics** | Compression ratio, quality indicators | Medium |
| **Layer 5: AI Vision** | Claude API visual analysis for artifacts | Medium-High |
| **Layer 6: Verdict Calculation** | Weighted scoring of all evidence | Combined |

### What Gets Detected

✅ **High Confidence Detection:**
- ChatGPT/GPT-4o generated images (C2PA markers)
- Gemini generated images (IPTC markers)
- DALL-E images with metadata
- Stable Diffusion with embedded parameters

⚠️ **Medium Confidence:**
- AI images with stripped metadata (relies on visual analysis)
- Screenshots of AI images
- Heavily processed images

❌ **Difficult/Impossible:**
- AI images with deliberately stripped metadata AND no visual artifacts
- Perfect AI images from latest models (Midjourney v6, DALL-E 3, etc.)

## Installation

### Option 1: Deploy to Netlify (Recommended)

1. **Download this package**

2. **Create a GitHub repository**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/ai-detector.git
   git push -u origin main
   ```

3. **Deploy on Netlify**
   - Go to [netlify.com](https://netlify.com)
   - Click "Add new site" → "Import an existing project"
   - Connect your GitHub repo
   - Deploy!

4. **Add API Key**
   - Go to: Site settings → Environment variables
   - Add: `ANTHROPIC_API_KEY` = your_key_here
   - Redeploy

### Option 2: Local Development

```bash
# Install dependencies
npm install

# Install Netlify CLI
npm install -g netlify-cli

# Create .env file
echo "ANTHROPIC_API_KEY=your_key_here" > .env

# Run locally
netlify dev
```

## Usage

1. Open the web app
2. Upload an image (drag & drop or click)
3. Click "Run Full Analysis"
4. Review the 6-layer analysis results

## Understanding Results

### Verdicts

| Verdict | Meaning |
|---------|---------|
| **AI-GENERATED** | Definitive AI markers found (HIGH confidence) |
| **LIKELY AI-GENERATED** | Multiple AI indicators detected (MEDIUM confidence) |
| **LIKELY REAL** | Strong camera authenticity signals (MEDIUM confidence) |
| **INCONCLUSIVE** | Insufficient evidence (LOW confidence) |

### Key Insights

```
PRESENCE of AI markers = PROOF of AI generation
ABSENCE of AI markers = PROVES NOTHING

PRESENCE of camera EXIF = Strong evidence of real photo  
ABSENCE of camera EXIF = PROVES NOTHING
```

## Metadata Preservation Table

| Service | Preserves Metadata? |
|---------|-------------------|
| AWS S3 | ✅ Yes |
| Google Drive | ✅ Yes |
| Dropbox | ✅ Yes |
| Email attachments | ✅ Yes |
| Facebook/Instagram | ❌ Strips all |
| Twitter/X | ❌ Strips most |
| WhatsApp (photo) | ❌ Strips |
| Screenshots | ❌ Creates new file |

## Cost

- **Netlify Free Tier**: Hosting + 125K function calls/month
- **Claude API**: ~$0.003-0.015 per image analysis

## Limitations

⚠️ **Important**: No detection method is 100% accurate!

- Metadata can be stripped with one command
- Modern AI produces highly realistic images
- This tool provides PROBABILITY, not CERTAINTY
- The future is ATTESTATION (proving real at capture), not detection

## Tech Stack

- **Frontend**: Pure HTML/CSS/JavaScript
- **Backend**: Netlify Serverless Functions
- **AI**: Claude API (Anthropic)
- **Metadata**: EXIF.js (client-side)

## License

MIT License - Free to use and modify!
