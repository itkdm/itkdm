# GitHub Profile README Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a bilingual GitHub profile README with Chinese as the default, English as a parallel document, a featured-project-first layout, and a clean light visual style.

**Architecture:** The implementation is documentation-first. The profile will live in two root Markdown files, `README.md` and `README.en.md`, linked by a lightweight language switch. Dynamic visuals will come from external SVG card services, but the page narrative will stay focused on the approved intro, the `open-lab-components` featured project, the exploration path, and a restrained set of stats and skill components.

**Tech Stack:** GitHub profile README markdown, `capsule-render`, `github-readme-stats`, `skill-icons`, Git, PowerShell

---

## File Structure

### Files to Create or Modify

- Create: `.gitignore`
  - Ignore local brainstorming artifacts so the repo stays clean while iterating on the profile.
- Create: `README.md`
  - Default Chinese GitHub profile README shown on the profile page.
- Create: `README.en.md`
  - English companion README with the same structure and tone.

### External Services to Wire

- `https://capsule-render.vercel.app/api`
  - Hero banner
- `https://github-readme-stats.vercel.app/api`
  - GitHub stats card
- `https://github-readme-stats.vercel.app/api/top-langs`
  - Top languages card
- `https://skillicons.dev/icons`
  - Skill icon strip

### Content Decisions Locked In

- Chinese is the default language
- English lives in `README.en.md`
- Featured project is `open-lab-components`
- Light, clean card styling
- Two stats cards side by side
- No visitor counter, trophy, snake, quote, music widget, or large badge wall

## Task 1: Create Repo Hygiene and Chinese README Skeleton

**Files:**
- Create: `.gitignore`
- Create: `README.md`

- [ ] **Step 1: Create `.gitignore` with local artifact exclusions**

Use this exact file content:

```gitignore
.superpowers/
```

- [ ] **Step 2: Create the first `README.md` skeleton with language switch and section order**

Use this exact file content as the starting point:

```md
<p align="right">
  <a href="./README.md">简体中文</a> | <a href="./README.en.md">English</a>
</p>

<!-- Hero banner will be added in Task 2 -->

## Hi there

我一直在学习技术，也喜欢做一些小工具，更想做出真正属于自己的产品。  
我希望把无聊做有趣，把复杂讲清楚，把问题解决。  
**Make it happen!**

## Featured Project

### open-lab-components

`open-lab-components` 是我在长期投入的一个开源项目，试着把教育、前端组件、AI 和系统设计放到同一个语境里。  
它不是一个技术含量很高、靠炫技取胜的项目，但我相信它有很实际的价值：让内容更有趣，让交互更易理解，让组件更可复用，也让一个想法真正经历从设计到实现、再到打磨的完整产品构建过程。  
对我来说，它不只是一些组件，更是一条持续把想法做成产品的实践路径。

## Exploration Path

`Test -> DevOps -> Security -> Frontend -> Python -> Rust -> AI -> Design -> Product`

## GitHub Stats

<!-- Stats cards will be added in Task 2 -->

## Skills

<!-- Skill icons will be added in Task 2 -->

## Contact

- Website: https://itkdm.com
- Email: 3317431882@qq.com
```

- [ ] **Step 3: Verify the skeleton contains the required sections in the approved order**

Run:

```powershell
Select-String -Path .\README.md -Pattern '^## Hi there$','^## Featured Project$','^## Exploration Path$','^## GitHub Stats$','^## Skills$','^## Contact$'
```

Expected:

- 6 matches
- One match for each heading listed above

- [ ] **Step 4: Verify the language switch points to the correct files**

Run:

```powershell
Select-String -Path .\README.md -Pattern 'README.md','README.en.md'
```

Expected:

- One line containing both `README.md` and `README.en.md`

- [ ] **Step 5: Commit the skeleton**

Run:

```bash
git add .gitignore README.md
git commit -m "docs: add chinese profile readme skeleton"
```

Expected:

- A new commit with `.gitignore` and `README.md`

## Task 2: Add Banner, Stats Cards, and Skill Icons to Chinese README

**Files:**
- Modify: `README.md`

- [ ] **Step 1: Replace the hero comment with the approved banner block**

Insert this exact block at the top of `README.md` after the language switch:

```md
<img
  src="https://capsule-render.vercel.app/api?type=waving&color=0:eff6ff,100:dbeafe&height=220&section=header&text=Bujidao&fontSize=42&fontColor=1f2937&animation=fadeIn&desc=Make%20it%20happen!&descSize=18&descAlignY=66"
  width="100%"
/>
```

- [ ] **Step 2: Replace the stats placeholder with two light clean cards**

Replace the `<!-- Stats cards will be added in Task 2 -->` line with this exact block:

```md
<p>
  <img
    height="170"
    src="https://github-readme-stats.vercel.app/api?username=itkdm&show_icons=true&hide_border=true&title_color=2f80ed&icon_color=2f80ed&text_color=4b5563&bg_color=00000000&rank_icon=github"
  />
  <img
    height="170"
    src="https://github-readme-stats.vercel.app/api/top-langs/?username=itkdm&layout=compact&hide_border=true&title_color=2f80ed&text_color=4b5563&bg_color=00000000&langs_count=6&size_weight=0.5&count_weight=0.5"
  />
</p>
```

- [ ] **Step 3: Replace the skills placeholder with a selected skill icon strip**

Replace the `<!-- Skill icons will be added in Task 2 -->` line with this exact block:

```md
<p>
  <img
    src="https://skillicons.dev/icons?i=java,spring,docker,linux,ts,react,python,rust,githubactions&perline=9"
  />
</p>
```

- [ ] **Step 4: Verify all external component URLs return successfully**

Run:

```powershell
$urls = @(
  'https://capsule-render.vercel.app/api?type=waving&color=0:eff6ff,100:dbeafe&height=220&section=header&text=Bujidao&fontSize=42&fontColor=1f2937&animation=fadeIn&desc=Make%20it%20happen!&descSize=18&descAlignY=66',
  'https://github-readme-stats.vercel.app/api?username=itkdm&show_icons=true&hide_border=true&title_color=2f80ed&icon_color=2f80ed&text_color=4b5563&bg_color=00000000&rank_icon=github',
  'https://github-readme-stats.vercel.app/api/top-langs/?username=itkdm&layout=compact&hide_border=true&title_color=2f80ed&text_color=4b5563&bg_color=00000000&langs_count=6&size_weight=0.5&count_weight=0.5',
  'https://skillicons.dev/icons?i=java,spring,docker,linux,ts,react,python,rust,githubactions&perline=9'
)
foreach ($url in $urls) {
  $response = Invoke-WebRequest -Uri $url -Method Head
  Write-Output "$($response.StatusCode) $url"
}
```

Expected:

- Four lines
- Each line starts with `200`

- [ ] **Step 5: Verify the README now contains the hero image, stats cards, and skill icons**

Run:

```powershell
Select-String -Path .\README.md -Pattern 'capsule-render','github-readme-stats','top-langs','skillicons.dev'
```

Expected:

- At least 4 matches
- One match for each external service

- [ ] **Step 6: Commit the Chinese visual components**

Run:

```bash
git add README.md
git commit -m "docs: add profile banner stats and skills"
```

Expected:

- A new commit with the visual component wiring in `README.md`

## Task 3: Create the English README with Matching Structure and Natural Copy

**Files:**
- Create: `README.en.md`

- [ ] **Step 1: Create the full English README**

Use this exact file content:

```md
<p align="right">
  <a href="./README.md">简体中文</a> | <a href="./README.en.md">English</a>
</p>

<img
  src="https://capsule-render.vercel.app/api?type=waving&color=0:eff6ff,100:dbeafe&height=220&section=header&text=Bujidao&fontSize=42&fontColor=1f2937&animation=fadeIn&desc=Make%20it%20happen!&descSize=18&descAlignY=66"
  width="100%"
/>

## Hi there

I keep learning new technologies, enjoy building small tools, and want to create products of my own.  
I want to make boring things interesting, make complex things clear, and solve real problems.  
**Make it happen!**

## Featured Project

### open-lab-components

`open-lab-components` is a long-term open-source project I keep investing in, bringing education, frontend components, AI, and system design into the same context.  
It is not the kind of project that wins by showing off technical complexity, but I believe it creates practical value: making content more engaging, interactions easier to understand, components more reusable, and taking an idea through the full product-building journey from design to implementation to refinement.  
To me, it is more than a set of components. It is an ongoing path of turning ideas into products.

## Exploration Path

`Test -> DevOps -> Security -> Frontend -> Python -> Rust -> AI -> Design -> Product`

## GitHub Stats

<p>
  <img
    height="170"
    src="https://github-readme-stats.vercel.app/api?username=itkdm&show_icons=true&hide_border=true&title_color=2f80ed&icon_color=2f80ed&text_color=4b5563&bg_color=00000000&rank_icon=github"
  />
  <img
    height="170"
    src="https://github-readme-stats.vercel.app/api/top-langs/?username=itkdm&layout=compact&hide_border=true&title_color=2f80ed&text_color=4b5563&bg_color=00000000&langs_count=6&size_weight=0.5&count_weight=0.5"
  />
</p>

## Skills

<p>
  <img
    src="https://skillicons.dev/icons?i=java,spring,docker,linux,ts,react,python,rust,githubactions&perline=9"
  />
</p>

## Contact

- Website: https://itkdm.com
- Email: 3317431882@qq.com
```

- [ ] **Step 2: Verify the English README mirrors the Chinese README structure**

Run:

```powershell
$patterns = '^## Hi there$','^## Featured Project$','^## Exploration Path$','^## GitHub Stats$','^## Skills$','^## Contact$'
foreach ($pattern in $patterns) {
  Write-Output "EN: $pattern"
  Select-String -Path .\README.en.md -Pattern $pattern | ForEach-Object { $_.Line }
}
```

Expected:

- One matching heading line for each pattern

- [ ] **Step 3: Verify the English README keeps the key approved messages**

Run:

```powershell
Select-String -Path .\README.en.md -Pattern 'create products of my own','Make it happen!','open-lab-components','turning ideas into products'
```

Expected:

- Four matches
- One match for each approved message

- [ ] **Step 4: Commit the English README**

Run:

```bash
git add README.en.md
git commit -m "docs: add english profile readme"
```

Expected:

- A new commit with `README.en.md`

## Task 4: Final Polish and Repository Verification

**Files:**
- Modify: `README.md`
- Modify: `README.en.md`

- [ ] **Step 1: Tighten the Chinese README heading to feel less generic if needed**

If `## Hi there` feels too generic during final review, replace it with:

```md
## 关于我
```

If you make this change, also replace the English heading with:

```md
## About Me
```

If the original headings still read well with the page, leave them unchanged.

- [ ] **Step 2: Verify both files exist and the language switch is symmetrical**

Run:

```powershell
Test-Path .\README.md
Test-Path .\README.en.md
Select-String -Path .\README.md,.\README.en.md -Pattern 'README.md','README.en.md'
```

Expected:

- Two `True` lines from `Test-Path`
- Matches in both files for both links

- [ ] **Step 3: Run a final whitespace and diff sanity check**

Run:

```bash
git diff --check
git diff -- README.md README.en.md .gitignore
```

Expected:

- `git diff --check` prints nothing
- `git diff` shows only the intended profile README changes

- [ ] **Step 4: Review final content against the approved spec**

Run:

```powershell
Select-String -Path .\README.md -Pattern 'open-lab-components','Make it happen!','Test -> DevOps -> Security -> Frontend -> Python -> Rust -> AI -> Design -> Product'
Select-String -Path .\README.en.md -Pattern 'open-lab-components','Make it happen!','Test -> DevOps -> Security -> Frontend -> Python -> Rust -> AI -> Design -> Product'
```

Expected:

- All three patterns found in both files

- [ ] **Step 5: Commit the final README polish**

Run:

```bash
git add README.md README.en.md .gitignore
git commit -m "docs: finalize github profile readme"
```

Expected:

- A final commit with the polished bilingual profile README

## Self-Review

### Spec coverage

- Language strategy is implemented by `README.md` and `README.en.md`
- Visual direction is implemented through a light banner, light stats cards, and restrained icons
- Information architecture is implemented by the exact section order in both files
- Approved copy is included in the Chinese README and natural English copy is included in the English README
- Component constraints are implemented by explicitly excluding counters, trophies, snakes, quotes, music, and large badge sets

### Placeholder scan

- No `TBD`, `TODO`, or unresolved placeholders remain in this plan
- All file paths are exact
- All code blocks are concrete
- All verification commands are concrete

### Type and naming consistency

- The root files are consistently named `README.md` and `README.en.md`
- The featured project is consistently named `open-lab-components`
- The same external card services are used in both documents

