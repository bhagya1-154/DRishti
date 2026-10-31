# DRishti

Low-cost diabetic retinopathy screening website. Built by **Team BioNexis** for **Hack for Social Cause** (theme: Healthcare, Wellbeing and Service Delivery, Karnataka).

**Problem:** Diabetic retinopathy causes no symptoms early, so rural and semi-urban patients often learn about it only after vision is lost. Eye specialists and retinal cameras are mostly in cities.

**Idea:** A health worker takes a retina photo with a **smartphone + 20D condensing lens + adapter**, uploads it to this website, adds a few health readings, and gets a **risk level with advice in Kannada**. A doctor confirms every referral.

> This is a screening aid, not a medical diagnosis. The risk rules are a simple demo and are not clinically validated.

## Features

- Retina photo upload with a quick quality check (too dark, glare, possibly blurry)
- Patient readings: blood sugar, blood pressure (top number), years with diabetes
- Image grade: No DR, Mild, Severe
- Risk level (Low, Medium, High) with advice in **Kannada or English**
- Print the result
- "Try a sample case" button for a quick demo (uses a drawn illustration, not a real retina)
- Everything runs in the browser. Photos are never uploaded or stored.

## How to run (setup)

No installation needed.

1. Download or clone this repository.
2. Open `index.html` in any modern browser (phone or laptop).

**Environment variables:** none.
**Requirements:** a web browser. No server, database or API keys.

## Connect the AI model (optional)

By default the site runs in **demo mode**: the image grade is chosen by hand. To fill it in automatically:

1. Go to Google Teachable Machine and create an **Image Project (Standard)** with three classes named exactly: `No DR`, `Mild`, `Severe`.
2. Train it with retina images (for example from the APTOS 2019 or IDRiD datasets). Use a similar number of images per class.
3. Choose **Export Model -> TensorFlow.js -> Upload (shareable link)** and copy the link. It must end with `/`.
4. In `index.html`, paste that link into `const MODEL_URL = "";`.
5. Host the site on a normal web page (for example GitHub Pages) so the browser can load the model.

If the model cannot load, the site falls back to demo mode.

## Project structure

```
index.html            the whole website (HTML, CSS, JavaScript)
README.md             this file
TECHNICAL_DESIGN.md   architecture, data flow and risk rules
TEST_CASES.md         test cases with expected results
LICENSE               MIT license
sample-data/          add 3-5 sample retina images here (see below)
```

## Sample data

Put 3 to 5 sample retina images in `sample-data/` for testing, taken from public datasets, and credit them:

- APTOS 2019 Blindness Detection (Kaggle)
- IDRiD: Indian Diabetic Retinopathy Image Dataset

The built-in "Try a sample case" button works without any files.

## Capture setup (hardware)

- Smartphone with a good rear camera and flash (soften the flash to reduce glare)
- 20D condensing lens fixed in front of the camera by an adapter
- Record a short video and pick the sharpest frame
- The pupil must be dilated by a trained person. Do not shine the flash into anyone's eyes without a trained professional.

## Limitations

- Demo mode needs a manual image grade until a model is connected.
- Risk rules are simple and not clinically validated.
- Image-quality check is a guide only (thresholds are not calibrated).
- Needs validation on Indian clinic images before any real use.

## Team

Team BioNexis, Acharya Institute of Technology, Bengaluru, Karnataka.

## License

MIT. See `LICENSE`.
