# website for ManKind Project Japan

New site for ManKind Project Japan, currently at https://mkpjapan.github.io/

## Requirements
Setup Jekyll based on github pages:
[Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)

## Running the Site

1. ~/.../GitHub/mkpjapan.github.io>bundle exec jekyll serve --incremental
2. Go to http://127.0.0.1:4000/

## How the Site is Structured

### String Data
Strings for the site generally go into _data/strings.yml with a header for the section followed by strings for the section. These
strings are then accessed via  assign s = site.data.strings[page.foo_section].

It's done this way to allow the writers the flexibility to change the yml file without having to go through the html files
themselves.

For lists which are repeated, they fall into either a subfolder or their own yml file (like testimonials / faqs) to allow
changing them to be separate. Things in #_includes are essentially skeletons which just read string data from the yml files under
_data.