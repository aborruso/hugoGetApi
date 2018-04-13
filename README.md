# Hugo JSON API using Hugo's Custom Output Formats

Source code for [Build a JSON API With Hugo's Custom Output Formats](https://forestry.io/blog/build-a-json-api-with-hugo/)

Demo Site: https://hugo-api-demo.netlify.com/

## Discussion

- [Discourse](https://discourse.gohugo.io/t/build-a-json-api-with-hugos-custom-output-formats/11523/)
- [HN](https://news.ycombinator.com/item?id=16830678)

## Known Issue

**This issue is not in the [original
code](https://github.com/regisphilibert/hugoGetApi), but only in this fork where
I am experimenting with the `dict` + `jsonify` syntax.**

Currently `dict` + `jsonify` approach is used. But as `.Render` use is also
needed, the rendered `"item"` gets _jsonified_ twice and causes JSON for that
rendered item to become escaped.

### Hack

To around around that, this [hack][] is used.

This hack assumes that the actual JSON will never have:

- `{` at beginning of a string
- `}` at the end of a string
- Escaped double quote (`\"`) anywhere in a string

## Example output

- https://hugo-api-demo.netlify.com/players/index.json


[hack]: https://github.com/kaushalmodi/hugoGetApi/commit/cd15f4ba728dcc51851130fea9bf3bf03cbeb1c1
