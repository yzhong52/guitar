# Guitar Site — CLAUDE.md

A personal guitar learning reference site built with Jekyll, hosted at `https://yzhong52.github.io/guitar`. Contains chord diagrams, lyrics, and strumming patterns for songs Yuchen is learning.

## Development

```bash
bundle exec jekyll serve
```

Requires Ruby 3.0.3 (managed via rbenv). Ruby 3.1+ breaks nokogiri compatibility.

## Repository Structure

```
_chord/         # Song/lesson pages (main content collection)
_pages/         # about.md, tags.md, 404.html
_includes/      # chord-begin and chord-end HTML snippets
_data/          # navigation.yml
assets/chord/   # chord diagram images (.jpg)
assets/images/  # bio photos and misc
template.md     # boilerplate for new song files
```

## Adding a New Song

File naming convention: `_chord/[NUMBER]-[slug].md`
- Number indicates learning priority/order (01 = beginner, higher = advanced)
- Use `template.md` as the starting point

### Front Matter

```yaml
---
title: "Song Title"
excerpt: "Artist · Year"
---
```

Optional fields: `classes: wide`, `toc: true`, `toc_sticky: false`, `tags: [tag1, tag2]`

### Content Structure

1. Intro notes (capo, strumming pattern, key info)
2. Chord diagrams wrapped in includes:
   ```
   {% include chord-begin %}
   [chord diagrams using Unicode box-drawing characters]
   {% include chord-end %}
   ```
3. Lyrics with chord markers in a `<pre>` block — chords placed above the syllable where they change
4. Optional YouTube embed at the end:
   ```
   {% include video id="YOUTUBE_ID" provider="youtube" %}
   ```

### Chord Diagram Format

Uses Unicode box-drawing characters (`╒═╤═╕`, `├─┼─┤`, `└─┴─┘`). Open strings marked with `◯`, muted with `x`.

## Jekyll Configuration

- Theme: `minimal-mistakes@4.24.0`
- Collection `_chord` outputs to `/:collection/:path/`
- Layout defaults for `_chord`: single layout, no author profile/comments, sharing enabled
- Analytics: Google Analytics (G-WNL5K1V17C)
