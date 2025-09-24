

## Example Specification Response

Here is a sample of the specification data structure returned from the backend:

```json
{
  "statusCode": 200,
  "key": "success",
  "message": null,
  "data": [
    {
      "id": 99,
      "name": "صناعه الكنب",
      "values": [
        {
          "id": 178,
          "name": "اسيا",
          "spec": {
            "specId": 100,
            "specName": "اسيا",
            "specType": 3,
            "isRequired": false,
            "isMultiSelect": false,
            "values": [
              { "id": 179, "name": "السعودية" },
              { "id": 180, "name": "الامارات" }
            ]
          }
        },
        {
          "id": 183,
          "name": "افريقا",
          "spec": {
            "specId": 101,
            "specName": "افريقا",
            "specType": 3,
            "isRequired": false,
            "isMultiSelect": false,
            "values": [
              { "id": 184, "name": "مصر" },
              { "id": 185, "name": "السودان" }
            ]
          }
        }
      ]
    },
    {
      "id": 97,
      "name": "لون الكنب",
      "values": [
        { "id": 170, "name": "ابيض" },
        { "id": 172, "name": "احمر" }
      ]
    },
    {
      "id": 96,
      "name": "نوع الكنب",
      "values": [
        { "id": 167, "name": "زاويه" },
        { "id": 169, "name": "كامل" }
      ]
    }
  ]
}
```

---

## Example User Selection

Suppose the user selects these options:
- **صناعه الكنب**: 
  - "اسيا" → "السعودية", "الامارات"
  - "افريقا" → "مصر", "السودان"
- **لون الكنب**: "ابيض", "احمر"
- **نوع الكنب**: "زاويه", "كامل"

---

## API Submission Format

The selected options are mapped and sent to the backend as:

```json
{
  "AdType": 1,
  "MainCategoryId": 27,
  "SubCategoryId": 58,
  "AdSorting": 1,
  "SpecIds": [
    { "SpecId": 100, "SpecOptionsIds": [179, 180] },   // اسيا: السعودية, الامارات
    { "SpecId": 101, "SpecOptionsIds": [184, 185] },   // افريقا: مصر, السودان
    { "SpecId": 97,  "SpecOptionsIds": [170, 172] },   // لون الكنب: ابيض, احمر
    { "SpecId": 96,  "SpecOptionsIds": [167, 169] }    // نوع الكنب: زاويه, كامل
  ]
}
```

---

## Mapping Table

| Spec Name         | SpecId | Selected Options      | SpecOptionsIds     |
|-------------------|--------|----------------------|--------------------|
| اسيا             | 100    | السعودية, الامارات   | [179, 180]         |
| افريقا           | 101    | مصر, السودان         | [184, 185]         |
| لون الكنب        | 97     | ابيض, احمر           | [170, 172]         |
| نوع الكنب        | 96     | زاويه, كامل          | [167, 169]         |

---




