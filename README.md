# cat-lighting-effectiveness

Scores how well the lighting in a photograph reveals a cat as its subject. Evaluates visibility, detail and texture, and naturalness across a 0-to-1 scale. High scores mean light that lets you see the cat clearly and comfortably. Low scores mean the cat is lost to shadow, overexposure, silhouette, or distortion.

## Input

| Field | Type | Required | Description |
|---|---|---|---|
| `photograph` | `image` | Yes | A photograph containing a cat as its subject. |

The function receives a single photograph and nothing else. There is no metadata, no camera settings, no context about the scene or the photographer's intent. The function assesses the image exactly as a viewer would — looking at what is visible and judging whether the light did its job. This simplicity is deliberate: when someone looks at a photo of a cat, they do not ask about shutter speed. They ask whether they can see the cat.

## Output

A scalar score between **0** and **1**.

| Score Range | Meaning |
|---|---|
| **0.8 – 1.0** | Excellent lighting. The cat is clearly visible, its fur and features are rendered with rich detail and dimension, and the light feels natural and comfortable. The viewer sees the cat immediately and pleasantly. |
| **0.5 – 0.8** | Adequate lighting. The cat is visible and some detail comes through, but the light may be slightly flat, mildly harsh, or partially obscuring. The cat can be seen, but the light is not doing its job generously. |
| **0.2 – 0.5** | Poor lighting. The cat is partially lost — significant areas of the body or face are obscured by shadow, washed out by overexposure, or distorted by unnatural color casts. The viewer struggles to see the cat clearly. |
| **0.0 – 0.2** | Failed lighting. The cat is mostly or entirely invisible — swallowed by darkness, blown out to a featureless white shape, reduced to a silhouette, or so distorted that the subject is unrecognizable. |

## What It Evaluates

The function assesses lighting effectiveness across three qualities. Each addresses a different aspect of what it means for light to serve its subject, and together they form a complete picture.

### 1. Visibility

The most fundamental question: can you see the cat? This evaluates whether the lighting provides enough contrast and clarity for the cat to emerge from its surroundings as a distinct, recognizable subject. It catches failures at every extreme — deep shadows that swallow the cat's body, overexposure that erases features into white, and backlighting that reduces the cat to a dark silhouette.

Visibility is not a demand for brightness. A dim photograph where the cat's form is still distinguishable scores well. A brightly lit photograph where glare obliterates the cat's face scores poorly. The question is whether the light, at whatever level it exists, makes the cat perceivable.

**Scores high when:** The cat's full shape — head, ears, body — is clearly distinguishable against the background.

**Scores low when:** The cat is lost in shadow, blown out by overexposure, or reduced to a silhouette.

### 2. Detail and Texture

Beyond basic visibility, this evaluates whether the light reveals the physical qualities that make a cat a cat. Does the fur have visible texture and dimension — can you sense whether it is soft or coarse, short or long, patterned or solid? Do the eyes catch some light, bringing life and presence to the image? Are the contours of the face, the whiskers, and the body rendered with depth rather than flattened into a featureless mass?

This is not about photographic sharpness or resolution. A gently soft image where lighting sculpts the cat's form with dimension scores well. A tack-sharp image where harsh light has flattened every surface scores poorly.

**Scores high when:** Fur shows texture and dimension, eyes carry light, facial contours and whiskers come through with depth.

**Scores low when:** Fur is a uniform mass with no visible texture, eyes are dark or blank, and the cat looks flat rather than three-dimensional.

### 3. Naturalness and Comfort

Even when a cat is visible and detailed, lighting can fail if it introduces distortions that make the image feel wrong or unpleasant. This evaluates whether the light produces coherent, honest colors and a comfortable viewing experience. It identifies problems such as:

- **Unnatural color casts** — heavy green from fluorescent lighting, overwhelming orange from sodium lamps, sickly blue from poor white balance
- **Harsh flash artifacts** — blank reflective discs in the eyes, hard-edged shadows carving the face, flat frontal light stripping away depth
- **Extreme contrast** — deep black shadows immediately adjacent to blown-out highlights, creating visual discomfort

Naturalness does not require neutral or white light. Warm golden sunset light, cool overcast blue, soft amber lamplight — these all score well when they feel coherent. What matters is whether the viewer notices the cat before they notice the light.

**Scores high when:** Colors feel honest, the image is comfortable to look at, and the viewer's eye goes to the cat without distraction.

**Scores low when:** Strong color casts distort the cat's appearance, flash artifacts create jarring visual elements, or extreme contrast makes the image uncomfortable.

## Use Cases

- **Pet adoption platforms** — Surface listings where the cat is most clearly shown. Flag photos that need retaking because the cat cannot be seen well enough to attract adopters.
- **Image collection and curation** — Filter cat photographs by lighting quality for calendars, websites, photo books, or training datasets. Separate images where the light cooperated from images where it did not.
- **Personal photo selection** — Given dozens of photos from an afternoon, identify the ones where the lighting best reveals the cat — formalizing the instinct that already drives people to swipe past the dark, washed-out, and backlit ones.
- **Quality assurance pipelines** — Integrate into automated workflows that process cat images at scale, establishing a minimum lighting quality threshold before images proceed downstream.

## Philosophy

The standard is not professional lighting. It is functional lighting. A photograph taken with a phone under a kitchen lamp scores beautifully if the light falls on the cat in a way that lets you see it clearly, with texture, and without distortion. A photograph taken with expensive studio equipment scores poorly if the flash has blown the cat's face into a featureless white shape. The question is never whether the light is ideal — it is whether the light was enough. Whether, given whatever light was present, the cat came through.
