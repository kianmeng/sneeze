# Sneeze

Render Elixir data-structures to HTML. Inspired by [Hiccup](https://github.com/weavejester/hiccup).

[![CircleCI](https://circleci.com/gh/ShaneKilkelly/sneeze.svg?style=shield)](https://circleci.com/gh/ShaneKilkelly/sneeze)

## Usage

The `Sneeze.render/1` function will render a list of 'nodes' to html. A node can be any of:

- A tag: `[:br]`
- A tag with a body: `[:p, "hello"]`
- A tag with attributes: `[:input, %{type: "text", class: "form-field", name: "widget-input"}]`
- A tag with attributes and a body: `[:p, %{class: "article-content"}, "hello"]`
- A bare, stringable node: `22`
- A "raw html" node, which will not be escaped: `[:__@raw_html, "<span>derp</span>"]`


Of course, the `body` of any node can be an arbitrary number of other nodes.


## Examples

```elixir
Sneeze.render([:p %{class: "greeting"} "hello world"])
# => <p class="greeting">hello world</p>

Sneeze.render([:br])
# => <br />

Sneeze.render([:span, "<a>will be escaped</a>"])
# => <span>&lt;a&gt;will be escaped&lt;/a&gt</span>;

Sneeze.render([:div, [:__@raw_html, "<span>totally not escaped</span>"]])
# => <div><span>totally not escaped</span></div>

Sneeze.render(
  [:ul, %{class: "super-cool-list"},
   [:li, [:a, %{href: "/"},        "Home"]],
   [:li, [:a, %{href: "/about"},   "About"]],
   [:li, [:a, %{href: "/contact"}, "Contact"]]]
)
# => <ul class="super-cool-list"><li><a href="/">Home</a></li>...</ul
```


## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed as:

  1. Add `sneeze` to your list of dependencies in `mix.exs`:

    ```elixir
    def deps do
      [{:sneeze, "~> 0.2.0"}]
    end
    ```

  2. Ensure `sneeze` is started before your application:


## Bugs, Improvements and Contributing

Open an issue or pull-request on [GitHub](https://github.com/ShaneKilkelly/sneeze), all contributions welcome! :)
