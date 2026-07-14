# Health Score

The health score is a single **0–100** number summarizing how clean your
scene is. It's the headline of the panel and updates live.

## How it's calculated

Every check carries a **severity weight**:

| Severity | Weight | Meaning |
|----------|:------:|---------|
| Error | 2.0 | Counts fully against the score |
| Warning | 1.0 | Counts partially |
| Info | 0.5 | Minor — small score impact |

The score is the percentage of total possible weight that is **passing**.
A scene where every check passes scores **100**; a scene where everything
fails scores **0**.

$$
\text{score} = 100 \times \left(1 - \frac{\text{lost weight}}{\text{total weight}}\right)
$$

## What moves it

- **Fixing** a check reclaims its weight — the score rises immediately.
- **Dismissing** a check counts it as healthy, so the score rises too
  (dismiss is for intentional "problems").
- **Profiles** change which checks run and can override severities, so
  the score reflects the profile you're working in.

## Reading the color

- **≥ 90** — clean.
- **60–89** — some issues worth a look.
- **< 60** — the health box turns red.

!!! note
    The score is a guide, not a grade. A scene can legitimately sit below
    100 — a stylized asset with intentional ngons, say. Dismiss the checks
    that don't apply to your work and the score reflects *your* standard.
