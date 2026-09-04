# chambers.io

[chambers.io][] - my website powered by [Jekyll][] and the [Minimal Mistakes][] theme.

## Build/Run Locally

`bundle install`

`bundle exec jekyll serve`

[chambers.io]: https://chambers.io
[Jekyll]: https://jekyllrb.com/
[Minimal Mistakes]: https://github.com/mmistakes/minimal-mistakes

## Rake Tasks

```
rake blog:create[title]       # Creates a new Jekyll blog post
rake link:create[title,link]  # Creates a new linkblog post
rake now:commit               # Commits changes to the now page and optionally pushes them
rake now:sync                 # Syncs the now page to dakota.omg.lol
rake now:update               # Updates the last_modified_at date in the now page front matter to today
```
