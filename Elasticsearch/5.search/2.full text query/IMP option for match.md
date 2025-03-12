# 🔹 OpenSearch match Query Documentation

## 🔥 **match Query ke Important Parameters:**

### 1️⃣ **query**

- ✅ Search keyword specify karta hai.
- **Example:**
  ```json
  "query": "opensearch tutorial"
  ```

### 2️⃣ **operator**

- **Default:** `OR`
- ✅ Decide karta hai ki search words **AND** ya **OR** relation me consider hon.
- **Example:**
  ```json
  "operator": "AND"
  ```
  🔹 Iska matlab: Dono words **(opensearch AND tutorial)** present hone chahiye.

### 3️⃣ **fuzziness**

- ✅ Typos aur spelling mistakes handle karta hai.
- **Values:** `AUTO`, `1`, `2` (jitna zyada, utna flexible fuzzy matching)
- **Example:**
  ```json
  "fuzziness": "AUTO"
  ```
  🔹 **"openseerch"** bhi match karega (kyunki "opensearch" se milta-julta hai).

### 4️⃣ **prefix_length**

- ✅ Fuzzy matching se pehle **kitne characters exact match hone chahiye.**
- **Example:**
  ```json
  "prefix_length": 2
  ```
  🔹 "openseerch" match karega **lekin "pnsearch" nahi**, kyunki pehle 2 letters **("op")** same hone chahiye.

### 5️⃣ **fuzzy_transpositions**

- ✅ Letter swapping allow karta hai ya nahi.
- **Default:** `true`
- **Example:**
  ```json
  "fuzzy_transpositions": false
  ```
  🔹 Agar `false` hai, to **"gril" → "girl"** match nahi karega.

### 6️⃣ **minimum_should_match**

- ✅ Decide karta hai ki **kitne words match hone chahiye.**
- **Example:**
  ```json
  "minimum_should_match": "75%"
  ```
  🔹 Agar 4 words search ho rahe hain, to kam se kam 3 words match hone chahiye.

### 7️⃣ **boost**

- ✅ Query ki importance badhane ke liye.
- **Example:**
  ```json
  "boost": 2.0
  ```
  🔹 Higher boost = Higher relevance.

---

---

### 🔥 **Extra Parameters for match Query**

### 1️⃣ `lenient`

- **Kya karta hai?**  
  ✅ Agar data type mismatch ho jaye (e.g., number field pe text search ho), to error throw karne ki jagah ignore karega.
- **Default:** `false`
- **Example:**
  ```json
  "lenient": true
  ```
  🔹 Agar `title` ek **integer field** hai aur aap usme `"opensearch"` search kar rahe ho, to error **nahi aayega**, balki OpenSearch intelligently query handle karega.

---

### 2️⃣ `zero_terms_query`

- **Kya karta hai?**  
  ✅ Agar query empty ho ya stop words (e.g., `the`, `is`, `a`) ke wajah se remove ho jaye, to kya response dena hai?
- **Values:** `"none"` (default) | `"all"`
- **Example:**
  ```json
  "zero_terms_query": "all"
  ```
  🔹 Agar search term sirf stop words hote hain (`"is a the"`), to `"none"` pe kuch return **nahi hoga**, par `"all"` pe **saare documents return honge**.

---

### 3️⃣ `auto_generate_synonyms_phrase_query`

- **Kya karta hai?**  
  ✅ Multi-word queries ke liye **synonym expansion** allow karta hai.
- **Default:** `true`
- **Example:**
  ```json
  "auto_generate_synonyms_phrase_query": false
  ```
  🔹 `"quick fox"` search karne pe **synonym-based expansion disable ho jayegi**.

---
