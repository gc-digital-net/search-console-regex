# Make Claude tailor the regex to your site

Claude can't see your Search Console, so give it your real searches first.

**Export:** Search Console > Performance > Search results > last 3 months > Export > Download CSV. Attach the Queries file (or the whole zip) to Claude.

Add this line to every prompt:

> Check every regex against the sample searches I gave you before you answer. If you are not sure it works in RE2, say so.

---

## 1. Find the patterns in your searches

```
Here is my Search Console query export. My site is about [what you sell or do] in [country / language].

1. Read the top 500 searches by impressions.
2. Find 8 patterns that repeat: modifiers, question words, model codes, local words, product attributes, words in my language.
3. For each pattern write one RE2 regex for Search Console (no lookahead, no lookbehind, under 4,096 characters).
4. For each regex, list 5 searches from my export it matches and any it should match but misses.

Use my real words and my language, not English examples.
```

## 2. Build one from plain English

```
Write an RE2 regex for Google Search Console (Performance > Query > Custom regex) that matches [what you want, e.g. "searches that include a size like 55 inch or 65"].

Give me 5 searches it should match and 5 it should not, and check each one. No lookahead or lookbehind.
```

## 3. Hide your brand

```
My brand is [brand]. Here are my top branded searches: [paste].

Write one regex for "Doesn't match regex" that catches every spelling, typo and spacing of my brand, and nothing else. Show me which of my searches it removes.
```

## 4. Group your pages

```
Here are my site's top 200 URLs: [paste].

Group them by page type (category, product, blog, guide, location...). For each type write an RE2 regex for the Page filter that matches that type only. Flag any URL that fits two groups.
```

## 5. Turn the results into a to-do list

```
Here is my export after applying this regex: [paste regex + results].

For each search, tell me which page on my site should rank for it, whether that page exists, and what to add to it. Group by page. Start with searches at position 8 to 20.
```

---

Back to the [cheat sheet](README.md).
