# GitHub Wiki Upload Instructions

This folder is ready to be copied into a GitHub Wiki repository.

## Option 1: Upload manually through GitHub UI

1. Open your repository.
2. Go to the **Wiki** tab.
3. Create pages using the `.md` files in this folder.
4. Use the filename as the page title, without `.md`.

## Option 2: Clone wiki locally

Replace `<REPO_URL>` with your repository wiki URL.

```bash
git clone <REPO_URL>.wiki.git
cd <repo-name>.wiki
cp /path/to/ASHU_Mentor_AI_Studio_GitHub_Wiki/*.md .
git add .
git commit -m "Add ASHU Mentor AI Studio wiki"
git push
```

## Recommended Page Order

1. Home
2. Demo and Live App
3. Architecture and Product Design
4. Complete Technical Specification
5. Training and Interview Workflow
6. Digital Presenter Voice and Lip-Sync Pipeline
7. Background Rendering and Cache Reuse
8. Feature Reference
9. Acceptance Criteria Mapping
10. Evidence Pack and Reporting
11. Security Consent and Governance
12. Quick Links
13. About ASHU Mentor AI Studio
