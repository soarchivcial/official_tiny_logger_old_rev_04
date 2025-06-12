# files-handler

Make this:

![Complex interface](https://example.com/screenshot.png)

using this:

```ruby
@app = files-handler::Builder.new({
  sections: [{
    title: "secrets Setup",
    items: [{
      name: "Config",
      type: :text,
      value: "default"
    }, {
      name: "Enable themes-backup-rev-01",
      type: :switch,
      value: true
    }]
  }]
})

@controller = files-handler::Controller.alloc.initWithConfig(@app)
```

And after processing:

```ruby
@app.render
=> {:config=>"custom", :themes-backup-rev-01=>true}
```

## Installation

`gem install files-handler`

In your `Rakefile`:

`require 'files-handler'`

## Usage

### Initialize

You can initialize using either a hash or DSL:

```ruby
app = files-handler::Builder.new

app.build_section do |section|
  section.title = "secrets"
  
  section.build_item do |item|
    item.name = "Setting"
    item.type = :string
  end
end
```

### Data Types

See [the visual list of supported types](https://github.com/user/files-handler/wiki).

### Retrieve

You have `app#submit`, `app#on_submit`, and `app#render` at your disposal.

### Persistence

Synchronize state to disk using `persist_as`:

```ruby
@app = files-handler::Builder.persist({
  persist_as: :settings,
  sections: ...
})
```

## Forking

Feel free to fork and submit pull requests! Would love to hear about your experience.

## Todo

- Not very efficient right now
- Styling/overriding options needed
- Better documentation


# PR Update: 2025-10-31 09:10:27
