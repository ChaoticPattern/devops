# devops


```tsx
import { Controller, useForm } from 'react-hook-form';

const { control } = useForm<SaveRecordModel>();
// react-hook-form 'useForm'

...
return (
  <...>
  {/* register the input field (e.g. Controlled) */}
  <Controller
    control={control}
    name="hkid"
    rules={{
      required: 'HKID is required',
      maxLength: { value: 20, message: 'Max 20 characters' },
    }}
    render={({
      field: { onChange, onBlur, value, name, ref },
      fieldState: { invalid, error },
    }) => (
      <TextField
        inputRef={ref}
        onChange={onChange}
        onBlur={onBlur}
        value={value}
        error={invalid}
        helperText={error?.message}
        inputProps={{ "aria-labelledby": "hkid-label" }}
      />
    )}
  />
  <Controller
    name="patCat"      // field name in the data model
    control={control}
    rules={{
      required: 'Cat is required',
      maxLength: { value: 20, message: 'Max. 20 characters' },
    }}
    render={({
      field: { value, onChange, ref }
    }) => (
      <Select
        value={value}
        onChange={(e) => onChange(e.target.value as string)}
        inputRef={ref}
      >
        {[
          { value: '', display: '' },
          { value: 'in', display: 'In Patient' },
          { value: 'out', display: 'Out Patient' },
        ].map((c) => (
          <MenuItem key={c.value || '(empty)'} value={c.value}>
            {c.display}
          </MenuItem>
        ))}
      </Select>
    )}
  />
  <...>
)
```
