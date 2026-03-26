---
title: 🍌 Banana Peel
description: Automatically remove Google Gemini watermarks
---
**Github link:** [https://github.com/kendaniels/banana-peel](https://github.com/kendaniels/banana-peel)

Banana Peel removes Gemini watermarks from PNG images and losslessly compress them.

Point Banana Peel at your Downloads folder and it watches for new Gemini images, automatically peeling the watermark and compressing them the moment they land. Install it as an OS service and never think about it again -- every image arrives clean. It also works as a one-shot CLI for processing files you already have.

### How It Works

**Detection** -- Normalized cross-correlation matches the image against known watermark alpha masks (48x48 and 96x96 variants)

**Removal** -- Reverse alpha blending restores the original pixel values: original = (watermarked - alpha * 255) / (1 - alpha)

**Compression** -- oxipng (via pyoxipng) runs lossless optimization

The result is pixel-perfect to within +/-1 per channel due to quantization.

The reverse alpha blending method and calibrated alpha masks originate from Allen Kuo's GeminiWatermarkTool, licensed under MIT. See THIRD_PARTY_NOTICES for details.