# CVデータメモ

- PDF, WebのCVページ、WebのPresentationsページは全て `_data/cv.yml` をソースにしている
- `_data/cv_web.yml`, `_data/presentations.yml` は廃止済み

PDF生成:

```bash
uv run rendercv render --watch _data/cv.yml --design assets/rendercv/design.yaml --locale-catalog assets/rendercv/locale.yaml --settings assets/rendercv/settings.yaml
```
