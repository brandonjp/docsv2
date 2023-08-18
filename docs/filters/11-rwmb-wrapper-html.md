---
title: rwmb_wrapper_html
---

import FieldHTML from '../_parts/_field-html.md';

This filter is used to change the wrapper HTML of a field, e.g. the HTML content **inside the `<div class="rwmb-field..."></div>`**.

<FieldHTML />

Syntax:

```php
apply_filters( 'rwmb_wrapper_html', $html, $field, $meta );
```

This filter accepts 3 parameters:

Name|Description
---|---
`$html`| The wrapper HTML of the field
`$field`| Field settings
`$meta`| Field value

This filter has variations:

- `rwmb_wrapper_html`: apply to all fields
- `rwmb_{$field_type}_wrapper_html`: apply to fields with a specific type
- `rwmb_{$field_id}_wrapper_html`: apply to a the field with a specific id
