# Specifications API – Filter Request Example

This document explains how to construct a filter request for the Specifications API using the given response data.  
**The goal:** Filter results to only show ads for "جديد" (new) and "كامري" (Camry).

---

## Example API Response

Here is a sample of the specifications data you might receive from the API:

```json
{
  "statusCode": 200,
  "key": "success",
  "message": null,
  "data": [
    {
      "id": 92,
      "name": "الماركه",
      "values": [
        {
          "id": 161,
          "name": "تويوتا",
          "spec": {
            "specId": 93,
            "specName": "تويوتا",
            "specType": 3,
            "isRequired": false,
            "isMultiSelect": false,
            "values": [
              { "id": 162, "name": "كامري" },
              { "id": 163, "name": "لاند كروز" }
            ]
          }
        },
        {
          "id": 164,
          "name": "هوندا",
          "spec": {
            "specId": 94,
            "specName": "هوندا",
            "specType": 3,
            "isRequired": false,
            "isMultiSelect": false,
            "values": [
              { "id": 165, "name": "اكورد" },
              { "id": 166, "name": "اكورد ١" }
            ]
          }
        }
      ]
    },
    {
      "id": 90,
      "name": "الحالة",
      "values": [
        { "id": 153, "name": "جديد" },
        { "id": 154, "name": "مستعمل " }
      ]
    },
    { "id": 87, "name": "عدد الكيلومترات", "values": null },
    { "id": 82, "name": "سنة الصنع", "values": null }
  ]
}
```

---

## How to Build the Filter Request

To filter for ads that are both:
- **"جديد" (New)** (`id: 153`) from the specification `"الحالة"` (`id: 90`)
- **"كامري" (Camry)** (`id: 162`) from the specification `"تويوتا"` (`specId: 93`)

Your filter request should look like this:

```json
{
  "specIds": [
    {
      "specId": 93,
      "specOptionsIds": [162]
    },
    {
      "specId": 90,
      "specOptionsIds": [153]
    }
  ]
}
```

**Explanation:**
- `"specId": 93` refers to the "تويوتا" brand, with option `"specOptionsIds": [162]` for "كامري".
- `"specId": 90` refers to "الحالة", with option `"specOptionsIds": [153]` for "جديد".

---

## Example Full Request Body

If you want to include these filters in a larger request (e.g., searching for ads), your request might look like this:

```json
{
  "AdType": 1,
  "MainCategoryId": 21,
  "SubCategoryId": 52,
  "AdSorting": 1,
  "SpecIds": [
    {
      "SpecId": 93,
      "SpecOptionsIds": [162]
    },
    {
      "SpecId": 90,
      "SpecOptionsIds": [153]
    }
  ]
}
```

> **Note:**  
> - Make sure to use the correct key names and match the casing expected by your API (e.g., `SpecId` vs `specId`, `SpecOptionsIds` vs `specOptionsIds`).  
> - The order of keys does not matter, but the structure must be correct.

---

## Summary

- **To filter by "جديد" (new):** Use `"specId": 90`, `"specOptionsIds": [153]`
- **To filter by "كامري" (Camry):** Use `"specId": 93`, `"specOptionsIds": [162]`
- **Include these in your main request's `SpecIds` array.**

If you have further questions or need to filter by other values, use the corresponding `specId` and option `id` from the response data.
