# GitHub Profile README Design

## Summary

This spec defines the design direction for the `itkdm` GitHub profile README.

The profile should feel a little polished and expressive, but still clean. It should present Bujidao as someone with a clear main line in Java and backend work, while also exploring broadly across the stack. The first thing visitors should remember is the featured project `open-lab-components`.

The README will default to Chinese, provide a separate English version, and use a small language switch at the top instead of mixing both languages into a single long page.

## Goals

- Make the GitHub profile feel less plain without becoming noisy
- Put the featured project at the center of the page
- Present cross-stack exploration as a coherent path, not a scattered skill list
- Keep the page readable, lightweight, and easy to maintain
- Support both Chinese and English, with Chinese as the default

## Non-Goals

- Building a highly customized self-hosted SVG dashboard
- Turning the profile into a component showcase with many decorative widgets
- Writing two completely different personas for Chinese and English readers

## Audience

Primary audience:

- Developers visiting the profile through repositories, issues, pull requests, or open source activity
- People evaluating the owner's interests, strengths, and projects quickly

Secondary audience:

- Potential collaborators
- People who may click through to the personal site

## Profile Positioning

The README should communicate this identity:

- Always learning technology
- Likes building small tools
- Wants to build products of his own
- Cares about making boring things interesting, making complex things clear, and solving real problems

The page should feel like it belongs to a builder with a long-term project, not someone listing every technology they have touched.

## Language Strategy

The profile will use a two-document setup:

- `README.md`: default Chinese version shown on the GitHub profile
- `README.en.md`: English version with the same structure and tone

At the top of both files, add a light language switch:

- Chinese page: `简体中文 | English`
- English page: `简体中文 | English`

The switch should act as simple links between the two files. It should be visible but low emphasis.

## Visual Direction

Tone:

- A little cool, but still clean
- Light and airy rather than dark and heavy
- More product-oriented than badge-oriented

Visual guidance:

- Prefer light backgrounds or transparent cards
- Use blue as the main accent for stats and headings
- Avoid heavy gradients, loud neon themes, and dense visual clutter
- Use 1-2 dynamic elements only, not a pile of widgets

## Information Architecture

The Chinese `README.md` should use this order:

1. Language switch
2. Hero banner
3. Short intro
4. Featured project: `open-lab-components`
5. Exploration path
6. GitHub stats row
7. Skill icons
8. Contact links

Rationale:

- The hero establishes mood
- The short intro explains identity
- The featured project becomes the main memory anchor
- The exploration path explains breadth without becoming a laundry list
- Stats support credibility but do not become the main attraction

## Section Requirements

### 1. Language Switch

Purpose:

- Provide a clean bilingual entry point

Requirements:

- Keep it visually light
- Do not use large badges or oversized buttons

### 2. Hero Banner

Purpose:

- Set the tone and first impression

Requirements:

- Use `capsule-render`
- Keep text as the main focus
- Optional: include a short animated subtitle only if it stays restrained

### 3. Short Intro

Purpose:

- Introduce the owner in 2-3 compact lines

Approved Chinese copy:

> 我一直在学习技术，也喜欢做一些小工具，更想做出真正属于自己的产品。  
> 我希望把无聊做有趣，把复杂讲清楚，把问题解决。  
> **Make it happen!**

Intent:

- Learning mindset
- Builder mentality
- Product ambition
- Clear personal values

### 4. Featured Project

Purpose:

- Make `open-lab-components` the center of the page

Requirements:

- Give this section the strongest informational weight
- Include links as appropriate, such as repository and demo if available
- Explain why the project matters, not just what it is

Approved Chinese copy:

> `open-lab-components` 是我在长期投入的一个开源项目，试着把教育、前端组件、AI 和系统设计放到同一个语境里。  
> 它不是一个技术含量很高、靠炫技取胜的项目，但我相信它有很实际的价值：让内容更有趣，让交互更易理解，让组件更可复用，也让一个想法真正经历从设计到实现、再到打磨的完整产品构建过程。  
> 对我来说，它不只是一些组件，更是一条持续把想法做成产品的实践路径。

Intent:

- Present the project as a long-term product-building practice
- Emphasize real usefulness over technical showmanship
- Tie together education, components, AI, and systems thinking

### 5. Exploration Path

Purpose:

- Show cross-stack curiosity without losing the main line

Approved direction:

`Test -> DevOps -> Security -> Frontend -> Python -> Rust -> AI -> Design -> Product`

Requirements:

- Present this as a path or map, not a dense bullet list
- Tie the path back to better systems and better user experience

### 6. GitHub Stats Row

Purpose:

- Add a little visual energy and supporting signal

Approved direction:

- Two cards side by side
- Light, clean appearance
- Left: GitHub stats
- Right: top languages

Approved implementation choice:

- Use `github-readme-stats` for both cards
- Use the standard stats card plus the top-languages card

Why this choice:

- Closest to the desired effect while staying easy to maintain
- Mature ecosystem and common setup
- Better fit than an all-in-one custom dashboard for this stage

Styling guidance:

- Prefer a light or transparent theme
- Use matching themes across both cards
- Keep the cards visually secondary to the featured project

### 7. Skill Icons

Purpose:

- Make the capability spectrum easy to scan

Requirements:

- Use `skill-icons`
- Show only selected tools and languages
- Do not try to represent every possible skill

Suggested focus areas:

- Java
- Spring
- Docker
- Linux
- TypeScript
- React
- Python
- Rust
- GitHub Actions
- AI-related tools if they fit the final set

### 8. Contact Links

Purpose:

- Provide a clean way to continue the conversation

Requirements:

- Keep it short
- Include website and email
- Optional: a short current focus line if it does not add clutter

## Approved Component Set

Keep:

- `capsule-render` hero banner
- Optional restrained typing subtitle
- `github-readme-stats` stats card
- `github-readme-stats` top languages card
- `skill-icons`
- Lightweight language switch

Do not include for the first version:

- Visitor counter
- Trophy cards
- Snake animation
- Quote widgets
- Music widgets
- Blog feed blocks
- Large badge collections
- Multiple moving components competing for attention

## English README Requirements

The English file should:

- Keep the same structure as the Chinese file
- Preserve the same personality and message
- Read naturally in English rather than translating word-for-word

The English version should not become a different brand voice.

## Deliverables

Implementation should produce:

- `README.md` in Chinese
- `README.en.md` in English
- A clean language switch between them
- The approved sections and component choices

## Risks and Guardrails

Risk:

- The profile could slide back into a generic "I know many technologies" README

Guardrail:

- Keep the featured project central
- Keep the intro compact
- Keep exploration as a path, not a list dump

Risk:

- The page could become visually noisy from too many profile widgets

Guardrail:

- Limit dynamic components
- Use light styling
- Treat stats as support, not the headline

## Final Direction

The final README should feel like:

- a builder's profile
- with one clear featured project
- a broad but coherent learning path
- a little visual polish
- and a strong preference for clarity over performance
