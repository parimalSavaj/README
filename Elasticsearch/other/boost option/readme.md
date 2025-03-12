### **🔍 Boost in Elasticsearch - Explained Simply**

#### 📌 **What is Boost?**

Boost ka matlab hai **search results ki priority badhana ya kam karna**. Agar aap chahte ho ki kuch documents **zyada important lagein** Elasticsearch ko, toh aap boost ka use kar sakte ho.

👉 **Boost sirf ranking pe effect dalta hai, filtering pe nahi!**

- Boost kisi document ko **match hone se rokta nahi hai**
- Sirf **relevance score** badhata ya kam karta hai

---

## 🔹 **1. Basic Boost Example**

Agar aapke paas `title` aur `description` field hai aur aap chahte ho ki `title` zyada important ho, toh aap boost ka use kar sakte ho:

```json
GET my_index/_search
{
  "query": {
    "bool": {
      "should": [
        { "match": { "title": { "query": "smartphone", "boost": 2.0 } } },
        { "match": { "description": { "query": "smartphone", "boost": 1.0 } } }
      ]
    }
  }
}
```

✅ **Isme `title` field ko `description` ke mukable 2x zyada priority di gayi hai.**

**Matlab agar kisi document me `smartphone` title me milta hai, toh uska score zyada hoga aur wo search results me upar aayega.**

---

## 🔹 **2. Boost Inside Range Query**

Agar aap price range wale products me kisi particular range ko zyada importance dena chahte ho, toh:

```json
GET my_index/_search
{
  "query": {
    "range": {
      "price": {
        "gte": 500,
        "lte": 1000,
        "boost": 2.0
      }
    }
  }
}
```

✅ **Iska matlab hai ki 500-1000 price range wale products ko zyada weight diya jayega.**

Agar kisi document ka price **200-300** hai, wo bhi match karega, **lekin 500-1000 wale products search results me upar aayenge!**

---

## 🔹 **3. Boost Inside Term Query**

Agar aap chahte ho ki kisi particular category ke products ko **zyada importance mile**, toh:

```json
GET my_index/_search
{
  "query": {
    "bool": {
      "should": [
        { "term": { "category.keyword": { "value": "electronics", "boost": 2.0 } } },
        { "term": { "category.keyword": { "value": "furniture", "boost": 1.0 } } }
      ]
    }
  }
}
```

✅ **Is query me `electronics` category ko `furniture` se zyada weight diya gaya hai.**  
👉 Matlab agar ek product `electronics` hai, toh wo `furniture` wale products ke upar dikhai dega.

---

## 🔹 **4. Boosting at Query Level**

Agar aap ek **poori query ko dusri query ke mukable zyada important karna chahte ho**, toh:

```json
GET my_index/_search
{
  "query": {
    "bool": {
      "should": [
        { "match": { "title": { "query": "laptop", "boost": 3.0 } } },
        { "match": { "description": { "query": "gaming", "boost": 1.5 } } }
      ]
    }
  }
}
```

✅ **Agar kisi document me `laptop` title me hai, toh wo `gaming` keyword wale documents se upar dikhai dega.**

---

## 📌 **Boosting Ka Use Kab Karein?**

1️⃣ Jab aap **kisi specific field ko zyada importance dena chahein.**  
2️⃣ Jab aap **kisi particular value wale documents ko prioritize karna chahein.**  
3️⃣ Jab aap **ek query ko dusri query ke mukable zyada important dikhana chahein.**  
4️⃣ Jab aap **filtered data me kuch range ya category ko importance dena chahein.**

**🚀 Boosting ka sahi use aapke search results ko aur intelligent bana sakta hai!**
