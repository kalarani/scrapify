## ScrApify

ScrApify is a library to build APIs by scraping static sites with an ActiveRecord like querying interface

### Installation

```
$ gem install scrapify
```

### Usage

Define html url and declare attributes using xpath or css selectors.
Scrapify classes must have a key attribute defined.

```
class Pizza
  include Scrapify::Base
  html "http://www.dominos.co.in/menuDetails_ajx.php?catgId=1"

  attribute :name, css: ".menu_lft li a"
  attribute :image_url, xpath: "//li//input//@value"

  key :name
end
```

Now you can use finder methods to extract data from a static site

```
> Pizza.all

> pizza = Pizza.find('mushroom')
> pizza.name
> pizza.image_url

> Pizza.first
> Pizza.last

> Pizza.count
```