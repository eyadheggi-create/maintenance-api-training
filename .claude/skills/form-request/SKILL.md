---
name: form-request
description: Use when creating or modifying Laravel Form Requests, validation rules, authorization, request preparation, or API validation.
---

# Form Request conventions

1. Class names follow Laravel conventions:
   - StoreThingRequest
   - UpdateThingRequest

2. Authorization belongs in `authorize()`.

3. Validation rules belong in `rules()`.

4. Never place validation inside Controllers.

5. Use `prepareForValidation()` when input normalization is needed.

6. Custom validation messages should support Arabic and English.

# Example

```php
class StoreMaintenanceRequestRequest extends FormRequest
{
    public function authorize(): bool
    {
        return $this->user()->can('create', MaintenanceRequest::class);
    }

    protected function prepareForValidation(): void
    {
        $this->merge([
            'title' => trim((string) $this->title),
        ]);
    }

    public function rules(): array
    {
        return [
            'title' => ['required', 'string'],
        ];
    }
}
```
