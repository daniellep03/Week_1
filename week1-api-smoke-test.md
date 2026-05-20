# Week 1 — LLM API Smoke Test

Smoke test of the class LLM endpoint (Ollama, model `gpt-oss:120b`).

## Curl command

The command below is exactly what was run. The API key is supplied through the
`$OLLAMA_API_KEY` environment variable, so the key itself never appears in the
command. (API key: `<REDACTED>`)

```bash
curl https://ollama.com/api/generate \
  -H "Authorization: Bearer $OLLAMA_API_KEY" \
  -d '{
    "model": "gpt-oss:120b",
    "prompt": "Why is the sky blue?",
    "stream": false
  }'
```

## JSON response

```json
{"model":"gpt-oss:120b","created_at":"2026-05-20T20:50:59.485823919Z","response":"**Short answer:**  \nThe sky looks blue because molecules and tiny particles in Earth’s atmosphere scatter short‑wavelength (blue‑violet) sunlight much more efficiently than longer‑wavelength (red‑orange) light. Our eyes are also more sensitive to blue than to violet, so the scattered light we see is predominantly blue.\n\n---\n\n## The physics behind the color\n\n### 1. Sunlight is white, but it’s a mixture of colors  \nSunlight contains all visible wavelengths, from about 380 nm (violet) to 750 nm (red). When you pass it through a prism or a raindrop you can see the familiar rainbow of colors.\n\n### 2. Light interacts with the atmosphere  \nAs sunlight travels through the atmosphere it encounters gas molecules (N₂, O₂) and tiny particles (dust, water droplets). When a photon hits one of these tiny scatterers, the direction of the photon changes—a process called **scattering**.\n\n### 3. Rayleigh scattering favors short wavelengths  \nFor particles that are **much smaller than the wavelength of light** (the case for air molecules), the scattering intensity follows *Rayleigh’s law*:\n\n\\[\nI \\propto \\frac{1}{\\lambda^{4}}\n\\]\n\nwhere \\(I\\) is the scattered intensity and \\(\\lambda\\) is the wavelength. Because of the \\(\\lambda^{-4}\\) dependence:\n\n- Blue light (\\(\\lambda \\approx 450\\) nm) is scattered **~10 times more** than red light (\\(\\lambda \\approx 650\\) nm).\n- Violet (\\(\\lambda \\approx 400\\) nm) would be scattered even more, but…\n\n### 4. Why we see blue, not violet  \nTwo reasons mute the violet contribution:\n\n1. **Human eye sensitivity** – The photoreceptors (cones) in our eyes have a peak response around 555 nm (yellow‑green). Their sensitivity drops sharply toward the violet end, so violet photons produce a weaker signal than blue photons.\n2. **Solar spectrum** – The Sun emits less violet light than blue light to begin with, so there’s simply less violet to scatter.\n\nThe combination makes the scattered sunlight that reaches our eyes appear blue.\n\n### 5. The sky isn’t uniformly bright blue  \n- **Direct line of sight:** When you look straight up, the path through the atmosphere is relatively short, so you see a pale, nearly white sky near the zenith.\n- **Near the horizon:** The line of sight passes through a longer stretch of air, scattering more blue light toward you, so the horizon can look a deeper blue or even turquoise.\n\n### 6. Why sunrise and sunset turn red  \nWhen the Sun is low, its light must traverse **many times more atmosphere**. Most of the blue and violet light gets scattered out of the direct path long before the light reaches your eyes, leaving the longer‑wavelength reds and oranges to dominate the direct sunlight. The scattered blue light you still see overhead makes the sunrise/sunset sky glow with vivid reds and pinks.\n\n### 7. Variations and exceptions  \n- **Pollution, dust, or water droplets** (particles comparable in size to the wavelength) cause **Mie scattering**, which is less wavelength‑dependent. This can give the sky a whitish or hazy look.\n- **Volcanic eruptions** that inject fine ash high in the stratosphere can create spectacular red sunsets worldwide.\n- On other planets, the sky color changes with atmospheric composition (e.g., Mars has a butterscotch‑orange sky because of iron‑oxide dust, while Titan’s orange haze comes from complex hydrocarbons).\n\n---\n\n## Bottom line\n\nThe sky is blue because **Rayleigh scattering** in our atmosphere preferentially redirects short‑wavelength (blue) sunlight toward every direction, and our eyes are tuned to see that blue more strongly than the violet that is scattered even more. The same scattering physics explains why the sky can appear red at sunrise and sunset, why hazy conditions look whitish, and why other worlds have different sky colors.","thinking":"The user asks a simple question: \"Why is the sky blue?\" Need to give a thorough yet accessible explanation about Rayleigh scattering, sunlight composition, scattering preferentially shorter wavelengths, etc. Possibly mention why sunrise/sunset are red, variations with atmospheric conditions, why not violet, human eye sensitivity, etc. Provide details. Provide analogies maybe. Provide answer in plain language. Also could include brief summary. Probably deliver concise but thorough.","done":true,"done_reason":"stop","total_duration":10047267811,"prompt_eval_count":73,"eval_count":944}
```

## What surprised me

I expected that I'm going to take forever to complete this homework with the API, but it worked on the first try once the key was set as an environment variable. The trickiest part was just being careful not to expose the key and making sure that the code is right.
