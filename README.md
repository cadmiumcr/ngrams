# N-Grams

N-Grams can be obtained for Arrays of Strings, or with single Strings (which will first be tokenized).

## Installation

1. Add the dependency to your `shard.yml`:

   ```yaml
   dependencies:
     cadmium_ngrams:
       github: cadmiumcr/ngrams
   ```

2. Run `shards install`

## Usage

```crystal
require "cadmium_ngrams"
```

#### bigrams

```crystal
ngrams = Cadmium.ngrams.new
ngrams.bigrams("these are some words")
# => [["these", "are"], ["are", "some"], ["some", "words"]]
```

#### trigrams

```crystal
ngrams = Cadmium.ngrams.new
ngrams.trigrams("these are some words")
# => [["these", "are", "some"], ["are", "some", "words"]]
```

#### arbitrary n-grams

```crystal
ngrams = Cadmium.ngrams.new
ngrams.ngrams("some other words here for you", 4)
# => [["some", "other", "words", "here"], ["other", "words", "here", "for"], ["words", "here", "for", "you"]]
```

#### padding

n-grams can also be returned with left or right padding by passing a start and/or end symbol to the bigrams, trigrams or ngrams.

```crystal
ngrams = Cadmium.ngrams.new
ngrams.ngrams("these are some words", 4, "[start]", "[end]")
# => [
      ["[start]", "[start]", "[start]", "these"],
      ["[start]", "[start]", "these", "are"],
      ["[start]", "these", "are", "some"],
      ["these", "are", "some", "words"],
      ["are", "some", "words", "[end]"],
      ["some", "words", "[end]", "[end]"],
      ["words", "[end]", "[end]", "[end]"]
    ]
```

## Contributing

1. Fork it (<https://github.com/cadmiumcr/ngrams/fork>)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## Contributors

- [Chris Watson](https://github.com/watzon) - creator and maintainer
