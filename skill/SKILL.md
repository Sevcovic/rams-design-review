---
name: "rams-design-review"
description: "Review a design (screenshot, Figma link, live URL or UI code) against Dieter Rams' 10 principles and list each mistake with the principle it breaks."
---

# Rams Design Review

Critique a design strictly through Dieter Rams' 10 principles of good design. Output is a list of concrete mistakes, each tied to the principle it breaks, with a fix. Be honest and direct: no praise padding, no generic advice.

## 1. Get the design

- **Screenshot / image**: look at it directly.
- **Figma link**: use the Figma connector (get_screenshot for visuals, get_design_context / get_metadata for structure, text, components). Review every frame the link points to. Check frame names, page names and annotations for context before asking anything.
- **Live URL**: open it in the browser and take screenshots of the relevant screens/states.
- **Code (HTML/React/etc.)**: read it; render it if possible so you judge what the user sees, not just markup.

## 2. Gather context (before reviewing)

An image alone can't tell you the goal, the users, or how finished the design is supposed to be, and several principles depend on those. Look at the design first, then ask only what it and the user's message don't already answer.

Ask in ONE round, max 4 questions, using AskUserQuestion with multiple-choice options (the user can always type their own). Tailor options to what you see. Pick from:

1. **Goal** — What is the main thing the user should do on this screen? (offer 2–3 plausible actions you see, e.g. "Complete checkout", "Browse products", "Sign up")
2. **Users** — Who uses it? (e.g. first-time visitors, returning customers, internal/admin users, mixed)
3. **Fidelity** — How finished is it? (Wireframe / Mid-fidelity / Final hi-fi / Live in production)
4. **Constraints** — What must it follow? (Existing design system, Strict brand guidelines, Platform conventions iOS/Android/web, Free to change anything) — multiSelect

Optional only if clearly relevant and you have room: platform/device, what's out of frame (other states or steps), or the specific area the user worries about.

Rules:
- Never ask what's visible in the design.
- If the user says "just review" / "no questions", or isn't around to answer, skip asking: state your assumptions in one line at the top and continue.
- Ask once. Don't follow up with more questions after the answers.

Use the answers:
- **Goal + users** drive #2 Useful and #10 As little design as possible (what's essential vs. noise).
- **Fidelity** sets severity: in wireframes ignore visual polish (#3, #8 pixel details) and focus on structure, usefulness, understandability; in final/live designs, details count fully.
- **Constraints**: don't flag something as a mistake if the design system or platform requires it; flag it as a system-level issue instead if it still breaks a principle.

## 3. The principles and what to look for

1. **Innovative** — Copies a pattern without reason; misses an obvious better interaction that current tech allows.
2. **Useful** — Elements that don't serve the user's goal; primary task buried; missing something the task needs.
3. **Aesthetic** — Inconsistent spacing, alignment, type scale, color; visual noise; poor hierarchy; clashing styles.
4. **Understandable** — Unclear labels or icons without text; ambiguous CTAs; unclear state, affordance or next step; needs explanation to use.
5. **Unobtrusive** — Decoration competing with content; loud colors/animations/badges where neutral would do; brand shouting over the task.
6. **Honest** — Dark patterns (confirmshaming, preselected upsells, hidden costs, fake urgency/scarcity, disguised ads); overstated claims; misleading visual weight between options.
7. **Long-lasting** — Trend-chasing styles likely to date fast (heavy glassmorphism, gimmicky gradients, novelty fonts) without functional reason.
8. **Thorough to the last detail** — Missing states (empty, loading, error, disabled, long text, overflow); truncation; misaligned pixels; inconsistent components; accessibility gaps (contrast, tap targets, focus).
9. **Environmentally friendly** — Wasteful heavy assets, autoplay video, unnecessary animation, forcing extra steps/pages; dark mode or weight considerations where relevant.
10. **As little design as possible** — Redundant elements, duplicate CTAs, unnecessary dividers/cards/shadows, ornament without function. Ask of every element: what breaks if it's removed?

One mistake can break several principles; name the primary one and optionally a secondary.

## 4. Output format

If you assumed context, start with one line: **Assumed:** goal, users, fidelity.

Then a one-line verdict (the single biggest problem).

Then list issues, most severe first:

**[Severity: High / Medium / Low] Short title**
- **Where:** element / screen / frame
- **Problem:** what's wrong, concretely
- **Breaks:** #N Principle name (+ secondary if any)
- **Fix:** specific change

If something might be a problem but depends on context you don't have (other screens, data, behavior), mark it **[Needs context]** with what would confirm it, instead of guessing.

Rules:
- Only real issues. If a principle isn't violated, don't invent one.
- Be specific ("the grey 'Skip' link has 2.1:1 contrast"), never vague ("improve hierarchy").
- Max ~12 issues; group repeated ones.

End with a compact table: Principle | Status (OK / Issues / Can't judge) | Count — covering all 10.

## 5. Tone

Concise and honest, like a senior design critic. No flattery. Don't soften real problems.