# Exercises API

Read-only static JSON API served by GitHub Pages. 872 exercises, with images.

## Base URL

```
https://fushi500.github.io/exercises-api
```

## Endpoints

| URL | Description |
|-----|-------------|
| `index.json` | API overview & endpoint map |
| `exercises.json` | All 872 exercises |
| `categories.json` | All categories with slugs & counts |
| `muscles.json` | All muscles with slugs & counts |
| `equipment.json` | All equipment types with slugs & counts |
| `categories/{slug}.json` | Exercises filtered by category |
| `muscles/{slug}.json` | Exercises filtered by primary muscle |
| `equipment/{slug}.json` | Exercises filtered by equipment |
| `exercises/{slug}.json` | Single exercise by slug |

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
const res = await fetch('https://fushi500.github.io/exercises-api/exercises.json');
const { exercises } = await res.json();

// By muscle
const res = await fetch('https://fushi500.github.io/exercises-api/muscles/chest.json');
const { exercises } = await res.json();

// Single exercise
const res = await fetch('https://fushi500.github.io/exercises-api/exercises/barbell-bench-press.json');
const exercise = await res.json();
```

## Images

Each exercise has photos under `exercises/{Name_With_Underscores}/0.jpg` and `1.jpg`, for example
`https://fushi500.github.io/exercises-api/exercises/3_4_Sit-Up/0.jpg`.

The images come from [yuhonas/free-exercise-db](https://github.com/yuhonas/free-exercise-db) (Unlicense). I did not create them. My part is the packaging and publishing.
