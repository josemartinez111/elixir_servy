
<!-- livebook:{"persist_outputs":true} -->

# Servy notebook

## Section->EPIC0001: Immutable Data

```elixir
conversation = %{
  method: "GET",
  path: "/wildthings",
  res_body: "Bears, Lions, Tigers"
}
```

<!-- livebook:{"output":true} -->

```
%{method: "GET", path: "/wildthings", res_body: "Bears, Lions, Tigers"}
```

```elixir
conversation[:method]
```

<!-- livebook:{"output":true} -->

```
"GET"
```

```elixir
conversation[:path]
```

<!-- livebook:{"output":true} -->

```
"/wildthings"
```

```elixir
conversation.method
```

<!-- livebook:{"output":true} -->

```
"GET"
```

### dot notation only works if the keys in the %map are `:atoms`

```elixir
# key does not exist in %{map}
conversation.mike

# will output an error
# ** (KeyError) key 
# :mike not found in: %{method: "GET", path: "/wildthings", res_body: "Bears, Lions, Tigers"}
```

### def put(map, key, value)

### `@spec put(map(), key(), value()) :: map()`

Puts the given value under `key` in `map`.

```.ex
## Examples
iex> my_map = %{a: 1}
iex> Map.put(my_map, :b, 2)
output - %{a: 1, b: 2}

iex> Map.put(%{a: 1, b: 2}, :a, 3)
output - %{a: 3, b: 2}
```

```elixir
Map.put(conversation, :res_body, "Bears")
```

<!-- livebook:{"output":true} -->

```
%{method: "GET", path: "/wildthings", res_body: "Bears"}
```

### All data in elixir is immutable. So to add the new key/value pair to our conversation map we have to re-bind the put added data to our conversation map

```elixir
conversation = Map.put(conversation, :res_body, "Bears")
```

<!-- livebook:{"output":true} -->

```
%{method: "GET", path: "/wildthings", res_body: "Bears"}
```

```elixir
# test to see if the data was updated
IO.inspect(conversation, label: "(|the conversation map updated|)\n")
```

<!-- livebook:{"output":true} -->

```
the conversation map updated: %{method: "GET", path: "/wildthings", res_body: "Bears"}
```

<!-- livebook:{"output":true} -->

```
%{method: "GET", path: "/wildthings", res_body: "Bears"}
```

### You can also use a shortcut syntax to put a new value into a copy of the conversation map. This shorcut only works when you modify the fields that already exist in a map.

```elixir
conversation = %{conversation | res_body: "Bears, Lions, Tigers"}
```

<!-- livebook:{"output":true} -->

```
%{method: "GET", path: "/wildthings", res_body: "Bears, Lions, Tigers"}
```

```elixir
# test to see if the data was updated
IO.inspect(conversation, label: "(|the conversation map updated again!!|)\n")
```

<!-- livebook:{"output":true} -->

```
(|the conversation map updated again!!|)
: %{method: "GET", path: "/wildthings", res_body: "Bears, Lions, Tigers"}
```

<!-- livebook:{"output":true} -->

```
%{method: "GET", path: "/wildthings", res_body: "Bears, Lions, Tigers"}
```

## Section->EPIC0001: Function Clauses

```elixir

```
Copied
