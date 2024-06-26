# Octicons!

This is the [Bower][bower] package for [GitHub Octicons][octicons].

## Add Octicons to your project

1. Create a new file called _bower.json_ (if you don't have one already).

2. Add a new line for the Octicon dependency, pointing to the correct repository:

```json
{
  "name": "my_great_project",
  "dependencies": {
    "octicons": "*"
  }
}
```

3. Run `bower install`. The Octicons styles will be downloaded to _bower_components/octicons_.

4. Link to the `octicons.css` stylesheet in the `<head>` of your `<html>` page:

```html
<link rel="stylesheet" href="bower_components/octicons/octicons/octicons.css" />
```

4. Simply use an icon in your HTML page:

```html
<span class="octicon octicon-microscope"></span>
```

### Rails' asset pipeline

Octicons includes a stylesheet specifically for [Rails 4/Sprockets][sprockets].

1. Create a new file called _vendor/assets/bower.json_ (if you don't have one already).

2. Add a new line for the Octicon dependency, pointing to the correct repository:

```json
{
  "name": "my_great_project",
  "dependencies": {
    "octicons": "*"
  }
}
```

3. `cd` into `vendor/assets` and run `bower install`. The Octicons styles will be downloaded to _vendor/assets/bower_components/octicons_.

4. Open your config/application.rb, and add this line inside your Application:

```ruby
config.assets.precompile += %w(*.svg *.eot *.woff *.ttf)
```

5. In your application stylesheet, require `sprockets-octicons`:

```css
/*
= require sprockets-octicons
*/
```

6. Simply use an icon in your HTML page:

```html
<span class="octicon octicon-flame"></span>
```

7. If you want a view helper, add something like this to _app/helpers/application_helper.rb_:

```ruby
def octicon(code)
  content_tag :span, '', :class => "octicon octicon-#{code.to_s.dasherize}"
end
```

## Best practices

- Octicons look best in sizes that are multiples of 16px. You can update the size using the `font-size` CSS property. For example:

  ```css
  .octicon {
    font-size: 32px;
  }
  ```

- Octicons are not monospaced. This lets them work well next to type, but it means they won’t stack nicely by default. If you intend to stack octicons, such as in navigation, you will want to add some CSS to make them the same width, and centered. For example:

  ```css
  .navigation .octicon {
    width: 16px;
    text-align: center;
  }
  ```

### Resources

- [octicons.github.com](http://octicons.github.com/) - the Octicons website
- Read why [icon fonts are awesome](http://css-tricks.com/examples/IconFont/)
- How to compose your [HTML for icon font usage](http://css-tricks.com/html-for-icon-font-usage/)

## Why can't I see the characters in Font Book??

Give this a try, you should be all set:

![](http://cl.ly/image/2r1B1F2l3Q0D/content#png)

## FAQ

Check out [issues with the FAQ label](https://github.com/github/octicons/issues?q=is%3Aclosed+is%3Aissue+label%3AFAQ).

## Versions

Octicons operates similarly to [Semver](http://semver.org/) with the following version convention:

- Major: Breaking changes — removed icons, markup changes, unicode switches, css renames, icon redesigns
- Minor: Non-breaking changes — new icons, new aliases, minor icon changes
- Patch: Unnoticeable tweaks — slight visual changes, package updates

[octicons]: http://octicons.github.com
[bower]: http://bower.io/
[sprockets]: http://guides.rubyonrails.org/asset_pipeline.html
