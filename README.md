# Test task from Shved Mykhailo

## 1 Part : Launch postman collection called Pet store.postman_collection.json

Follow these steps to import and run a Postman collection :

### Step 1: Import the Collection and Environment Files
1. **Open Postman**.
2. Go to **File > Import** or click the **Import** button in the top left corner.
3. **Drag and drop** the collection (`.json`) or select it using the file selector.

### Step 2: Run the Collection
1. Go to **Collections** in the left sidebar.
2. Open the **imported collection**.
3. Click the **Run** button to start executing the requests in the collection with the chosen environment.



## 2 Part : Тест кейси для ендпоінта `POST https://petstore.swagger.io/v2/pet`

### Тест кейс 1
- **Id:** `01`
- **Summary:** Перевірка створення нового запису з коректними даними та усіма полями.
- **Priority:** High
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит на ендпоінт з наступними даними:
     ```json
     {
       "id": 1,
       "category": {
         "id": 1,
         "name": "Dogs"
       },
       "name": "doggie",
       "photoUrls": ["https://example.com/photo.jpg"],
       "tags": [
         {"id": 1, "name": "tag1"}
       ],
       "status": "available"
     }
     ```
  2. **Expected result:** Новий запис створений успішно. Статус відповіді: 200, дані відповідають відправленим у `body`.
- **Who created test case:** Shved Mykhailo

---

### Тест кейс 2
- **Id:** `02`
- **Summary:** Перевірка створення запису з коректними значеннями, тільки обов`язкових полів.
- **Priority:** High
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит тільки з полями name та photoUrls:
    ```json
     {
       "name": "doggie",
       "photoUrls": ["https://example.com/photo.jpg"]
     }
     ```
  2. **Expected result:** Відповідь з кодом 200 та дані відповідають відправленим у `body`.
- **Who created test case:** Shved Mykhailo

---

### Тест кейс 3
- **Id:** `03`
- **Summary:** Перевірка обов’язковості полів name та photoUrls.
- **Priority:** High
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит без поля `name` та `photoUrls`.
  2. **Expected result:** Відповідь з кодом 400 та повідомленням про відсутність 2 обов’язкових полів.
- **Who created test case:** Shved Mykhailo

---

### Тест кейс 4
- **Id:** `04`
- **Summary:** Перевірка роботи з некоректним форматом поля `photoUrls`.
- **Priority:** Medium
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит із значенням `photoUrls: "invalid_url"`.
  2. **Expected result:** Відповідь з кодом 400 та повідомленням про некоректний формат поля `photoUrls`.
- **Who created test case:** Shved Mykhailo

---

### Тест кейс 5
- **Id:** `05`
- **Summary:** Перевірка типів данних полів в body
- **Priority:** High
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит з іншими типами даних для всіх полів
  2. **Expected result:** Відповідь з кодом 400 та повідомленням про некоректний формат даних
- **Who created test case:** Shved Mykhailo

---

### Тест кейс 6
- **Id:** `06`
- **Summary:** Перевірка коректного створення запису з максимально можливим значенням `id`.
- **Priority:** Medium
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит з `id: 9223372036854775807`.
  2. **Expected result:** Запис створюється успішно, статус 200, поле `id` відповідає відправленому значенню.
- **Who created test case:** Shved Mykhailo

---

### Тест кейс 7
- **Id:** `07`
- **Summary:** Перевірка поведінки при додаванні нового параметра в body.
- **Priority:** Medium
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит із коректними даними і також додати поле `petType`.
  2. **Expected result:** Відповідь з кодом 400 та повідомленням про некоректний формат даних
- **Who created test case:** Shved Mykhailo

---

### Тест кейс 8
- **Id:** `08`
- **Summary:** Перевірка відправки одного і того ж запиту декілька разів.
- **Priority:** Medium
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит на ендпоінт з наступними даними:
     ```json
     {
       "id": 1,
       "category": {
         "id": 1,
         "name": "Dogs"
       },
       "name": "doggie",
       "photoUrls": ["https://example.com/photo.jpg"],
       "tags": [
         {"id": 1, "name": "tag1"}
       ],
       "status": "available"
     }
     ```
    2. Відправити ще раз тей самий POST запит

  3. **Expected result:** Обидва запита створено успішно. Статус відповіді: 200, дані відповідають відправленим у `body`. Цей запит не ідемпотентний і також в цьому ендпоінті немає перевірки на унікальність даних, тому сутності будуть створюватись кожен раз.
- **Who created test case:** Shved Mykhailo

---

### Тест кейс 9
- **Id:** `09`
- **Summary:** Перевірка створення запису з кількома тегами.
- **Priority:** Medium
- **Environment:** `https://petstore.swagger.io/v2/pet`
- **Steps to reproduce:**
  1. Відправити POST запит з `tags`, що містять декілька об’єктів.
  2. **Expected result:** Запис створюється успішно, статус 200, значення поля `tags` містить всі надіслані теги.
- **Who created test case:** Shved Mykhailo

---


