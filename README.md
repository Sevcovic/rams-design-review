# Rams Design Review

A Claude skill that reviews a design against Dieter Rams' 10 principles of good design and lists each mistake with the principle it breaks.

Give it a screenshot, Figma link, live URL or UI code. It asks up to four quick questions about the goal, the users, how finished the design is and its constraints, then returns:

- a one-line verdict
- issues ranked by severity, each with where it is, what's wrong, which principle it breaks and a concrete fix
- a table covering all 10 principles

It only reports real problems. A clean design gets a short review.

## The 10 principles

1. Innovative
2. Useful
3. Aesthetic
4. Understandable
5. Unobtrusive
6. Honest
7. Long-lasting
8. Thorough down to the last detail
9. Environmentally friendly
10. As little design as possible

## Install

**Claude.ai / Claude app:** download [`skill/SKILL.md`](skill/SKILL.md), zip the `skill` folder and upload it under Settings → Capabilities → Skills.

**Claude Code:** copy the folder into your skills directory:

```sh
mkdir -p ~/.claude/skills/rams-design-review
cp skill/SKILL.md ~/.claude/skills/rams-design-review/
```

## Use

> Review this with Rams principles. *(attach a screenshot or paste a Figma link)*

## Author

Petr Ševčovič
