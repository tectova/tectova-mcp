---
name: fashion-runway-research
description: Answer questions about fashion models' runway careers, runway show casts, fashion houses' casting histories and models by country at New York, London, Milan and Paris fashion weeks, using the Tectova MCP tools. Use when the user asks who walked a show or a fashion week, which houses a model has walked for, which models a house keeps casting, or which models from a country are new or most cast.
---

# Fashion runway research with Tectova

The Tectova tools read Tectova's documented runway record of the Big Four fashion weeks
(New York, London, Milan, Paris) since 2002. They are read-only.

## How to call the tools

1. **Resolve names first.** For a model, creative, house or agency, call
   `search_fashion_records` and take the slug from the hit. Don't guess slugs.
2. **Pick the tool.**
   - A person's career: `get_talent_runway_record` with the talent slug.
   - A house's shows and the faces it keeps casting: `get_brand_runway_history` with the
     brand slug.
   - One show's cast: `get_show_cast` with a show path such as `/shows/prada/ss2027-rtw`,
     taken from a brand history or a talent record.
   - Models of one nationality: `get_country_talent` with the country or demonym.
3. **Fashion-week questions:** pass `city` (`new-york`, `london`, `milan` or `paris`).
4. **"This season" questions:** pass `season` together with `city`. The latest season is
   `ss2027` at the time of writing; the "as of" date in each answer shows how current the
   data is. Without a city, `season` doesn't apply; use `section: "current_season"` instead.
5. **Lists are paginated.** Pass `next_cursor` back as `cursor` when the user needs the rest.

## How to report the answer

- Cite the tectova.com URL each answer returns and its "as of" date.
- Describe counts as "on Tectova's record". It is a documented record, not a complete
  career, and a model may have walked shows Tectova doesn't hold.
- Never present Tectova as a ranking of anyone's worth or talent. "Most cast" means most
  shows on record, nothing more.
- If a name isn't found, say it isn't on Tectova's record. Don't fill the gap from memory.

## Example questions

| Question | Call |
|---|---|
| "Which Chinese models walked New York Fashion Week this season?" | `get_country_talent` with `country: "Chinese"`, `city: "new-york"`, `season: "ss2027"` |
| "Which casting directors cast Japanese models most often?" | `get_country_talent` with `country: "Japanese"`, `section: "casting_directors"` |
| "Which houses has Julia Nobis walked for most?" | `search_fashion_records`, then `get_talent_runway_record` |
| "Which models does Saint Laurent cast again and again?" | `search_fashion_records`, then `get_brand_runway_history` |
| "Who walked Prada's SS27 womenswear show?" | `get_brand_runway_history` for the show path, then `get_show_cast` |
