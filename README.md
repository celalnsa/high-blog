# Blog

Hexo static blog for `https://blog.hehigh.com`.

## Publish

```bash
npm ci
npx hexo clean
npx hexo generate
npx hexo deploy
```

GitHub Pages serves the generated `gh-pages` branch from `/`. Keep the custom
domain in `source/CNAME` so `public/CNAME` is regenerated during deploy.
