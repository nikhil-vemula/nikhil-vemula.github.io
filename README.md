# Personal Blog

Blog uses Hugo static site generator.

```
hugo server -D # Start server building drafts
hugo new content posts/<name>

hugo new content posts/leetcode/leetcode-daily/<slug>.md
```

```
tailwindcss -i ./tailwind/homepage.css -o ./static/homepage.css --watch  
```

## Developer 101

- The content from `/layouts` overrides the content from `/themes/PaperMod/layouts/`