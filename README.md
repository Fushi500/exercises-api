# Exercises API

Read-only static REST API served via GitHub Pages. 872 exercises.

## Base URL

```
https://<your-username>.github.io/<your-repo>/api
```

## Endpoints

| URL | Description |
|-----|-------------|
| `api/index.json` | API overview & endpoint map |
| `api/exercises.json` | All 872 exercises |
| `api/categories.json` | All categories with slugs & counts |
| `api/muscles.json` | All muscles with slugs & counts |
| `api/equipment.json` | All equipment types with slugs & counts |
| `api/categories/{slug}.json` | Exercises filtered by category |
| `api/muscles/{slug}.json` | Exercises filtered by primary muscle |
| `api/equipment/{slug}.json` | Exercises filtered by equipment |
| `api/exercises/{slug}.json` | Single exercise by slug |

## Category slugs

`strength` · `stretching` · `plyometrics` · `strongman` · `cardio` · `olympic-weightlifting` · `calisthenics` · `crossfit`

## Muscle slugs

`abs` · `chest` · `shoulders` · `biceps` · `triceps` · `forearms` · `brachialis` · `lats` · `middle-back` · `lower-back` · `traps` · `quads` · `hamstrings` · `glutes` · `calves` · `soleus` · `adductors` · `abductors` · `neck`

## Equipment slugs

`none` · `barbell` · `dumbbell` · `ez-curl-bar` · `kettlebell` · `machine` · `cable` · `bands` · `bench` · `incline-bench` · `pull-up-bar` · `gym-mat` · `exercise-ball` · `medicine-ball` · `foam-roll` · `other`

## Exercise object shape

```json
{
  "slug": "bench-press",
  "name": "Bench Press",
  "category": "strength",
  "description": "...",
  "equipment": ["barbell", "bench"],
  "primary_muscles": ["chest"],
  "secondary_muscles": ["shoulders", "triceps"],
  "instructions": ["Step 1...", "Step 2..."],
  "video": "https://www.youtube.com/watch?v=..."
}
```

> Optional fields: `tips`, `aliases`, `variation_on`, `variations_on`, `tempo`, `license`, `license_author`

## Example fetch (JavaScript)

```js
// All exercises
const res = await fetch('https://<user>.github.io/<repo>/api/exercises.json');
const { exercises } = await res.json();

// By muscle
const res = await fetch('https://<user>.github.io/<repo>/api/muscles/chest.json');
const { exercises } = await res.json();

// Single exercise
const res = await fetch('https://<user>.github.io/<repo>/api/exercises/bench-press.json');
const exercise = await res.json();
```
