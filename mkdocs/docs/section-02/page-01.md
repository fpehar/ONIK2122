# Section 2 / Page 1


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
