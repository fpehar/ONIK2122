# Section 1 / Page 1

# Section 1 / Page 1

Example `go` code:

```go
// JSONResponse represents data structure of json response
type JSONResponse struct {
    URL       string    `json:"url"`
    Status    int       `json:"status"`
    CheckedAt time.Time `json:"checked_at"`
    Elapsed   float64   `json:"elapsed,omitempty"`
    Length    int       `json:"length,omitempty"`
    Find      *string   `json:"find,omitempty"`
    Found     *bool     `json:"found,omitempty"`
}
```

Example `python` code:

```python
class KlassForSort:
    """Example class"""

    attr1 = 1
    Attr2 = 2
    Name2 = 'name2'

    def __init__(self):
        self.name = 'Name'

    def get_name_and_method(self):
        return self.name + ' get_name_and_method'

    @property
    def admin1(self):
        return True
```

## What about content tabs?

=== "Go"

    ```go
    // JSONResponse represents data structure of json response
    type JSONResponse struct {
        URL       string    `json:"url"`
        Status    int       `json:"status"`
        CheckedAt time.Time `json:"checked_at"`
        Elapsed   float64   `json:"elapsed,omitempty"`
        Length    int       `json:"length,omitempty"`
        Find      *string   `json:"find,omitempty"`
        Found     *bool     `json:"found,omitempty"`
    }
    ```

=== "Python"

    ```python
    class KlassForSort:
        """Example class"""

        attr1 = 1
        Attr2 = 2
        Name2 = 'name2'

        def __init__(self):
            self.name = 'Name'

        def get_name_and_method(self):
            return self.name + ' get_name_and_method'

        @property
        def admin1(self):
            return True
    ```

# Code blocks

``` py
import tensorflow as tf
```

## Custom titles

``` py title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

## Adding annotations

``` yaml
theme:
  features:
    - content.code.annotate # (1)
```

1.  :man_raising_hand: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be expressed in Markdown.


