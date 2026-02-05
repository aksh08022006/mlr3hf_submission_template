# Instructions to publish and add to the R-Soc wiki

1. Create a GitHub repo (if you don't have one yet) and push your reports and code. Example:

```bash
mkdir mlr3hf
cd mlr3hf
# copy your files into this directory
git init
git add .
git commit -m "Contributor tests: easy + hard reports"
git remote add origin git@github.com:YOUR_USERNAME/mlr3hf.git
git branch -M main
git push -u origin main
```

2. (Optional) Publish the reports as GitHub Pages by pushing HTML or enabling Pages from `main` branch.

3. Edit the R-Soc wiki page: https://github.com/rstats-gsoc/gsoc2026/wiki/mlr3hf and add the `wiki-snippet.md` content into the "Potential contributor test results" section. Replace placeholders with real links.

4. Email mentors with `mentor_email.txt` content (update placeholders). Use their emails:
   - toby.hocking@r-project.org
   - sebastian.fischer@stat.uni-muenchen.de
