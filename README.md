# website for ManKind Project Japan

New site for ManKind Project Japan, currently at https://mkpjapan.org/

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

## How to do things.

### Removing a Section To the Landing Page (Home)
1. Go to _layouts/home.html
2. Remove the section you want
3. If your section was part of nav.html go to _includes\nav.html and remove it from the list there.
3. Push the change.

### Adding a Section To the Landing Page (Home)
1. Create your new section in _includes. Something like MyNewSection.html
2. Write out your section
3. In _layouts/home.html include it like the other sections in the order you want it to appear in.
4. In nav.html, add your section to the header (or not)

### How to change a string
1. You can search for the string by just searching _data for the string you're looking for
2. Change the string inside of _data in the yml file you found it in
3. run the site locally and see the string change.

### Excluding a file from the site
1. If you have something in static/ just move it into static/exclude. These are assets that are not used in the site, but could be used
in the future.

## Beware

Jekyll sites are essentially just frontend code which means the user will download nearly all assets of the site itself. Everything
in the _site folder is directly downloaded to the user's machine. This means:

1. All jpegs which didn't come from an online source must have their jpeg headers stripped to anonymize them
2. Any face pics or identifying information must be scrutinized heavily before pushing it
3. Scrub any strings in the repo for identifying information especially posts.

### Other things

Because Jekyll is wholly frontend code, use of php and ajax is essentially impossible (no back end to speak of). Due to that
we can't use certain things like captchas or standard fullstack technology. We should consider getting a backend eventually
even if it's just to keep posts on a server.

Because _site is essentially downloaded onto a client's device, the smaller the _site folder is the faster it will be; so be
judicious about what you put into it. Ultimately we do need to support slower speed internet if there are people who are
interested from abroad.