# Promis
---
## Promise (Va'da) JavaScript tilida asinxron amallar uchun ishlatiluvchi obyekt bo'lib, har bir asynchronous amalni bajarib, uning natijasini kuzatish uchun imkoniyat beradi. U shunday natijalarni qaytaradi: yaxshi (resolve) yoki yomon (reject). Asinxron amallar, masalan, fayllardan ma'lumot olish, serverdan ma'lumotlar yuklash, uzun vaqt talab qiladigan operatsiyalar kabi vazifalarni bajarishda ishlatiladi.
---
### 1. Pending - Va'da hali bajarilmayotgan va natija qaytarmagan holat.
### 2. Fulfilled - Va'da yaxshi natija bilan bajarilgan va o'z va'dasini to'liq topshirgan holat (resolve).
### 3. Rejected - Va'da yomon natija bilan bajarilgan va uning va'dasini bajarmagan holat (reject).
#### Promise yaratish uchun odatiy sintaksis:
```sh
const promise = new Promise((resolve, reject) => {
  // Amalni bajarish
  // Agar amal muvaffaqiyatli bajarilsa, resolve bilan natija qaytariladi:
  // resolve(natija);
  
  // Agar amal yuzaga kelmasa, reject bilan xato qaytariladi:
  // reject(xato);
});

```
---
# Promis methods()
---
### 1. then() - Va'da yaxshi natija (resolve) bilan bajarilsa, then() metodi ishga tushiriladi. U, yaxshi natijani olish uchun ishlatiladi.
```sh
promise.then((result) => {
  console.log(result); // Yaxshi natija
}).catch((error) => {
  console.log(error); // Yomon natija
});
```
---
### 2. catch() - Va'da yomon natija (reject) bilan bajarilsa, catch() metodi ishga tushiriladi. U, yomon natijani olish uchun ishlatiladi.
```sh
promise.catch((error) => {
  console.log(error); // Yomon natija
});
```
---
### 3. finally() - Va'da qaysi natija (yaxshi yoki yomon) bilan bajarilsa bo'lsin, finally() metodi ishga tushiriladi. U, amal yakuniga kelganda ishga tushiriladi.
```sh
promise.finally(() => {
  console.log("Amal yakunlandi");
});
```
---
### 4. Promise.all() - Bitta yoki undan ko'p Promiselarni bajarish natijalarini kuzatib turish uchun ishlatiladi. U barcha Promiselarni bajarilishi kutilganda ishga tushiriladi va biror Promis jadal elementi ham yomon natija bilan bajarilsa, Promise.all() barcha yomon natijalarni qaytaradi.
```sh
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Va'da 1"), 2000);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Va'da 2"), 1000);
});

Promise.all([promise1, promise2])
  .then((results) => {
    console.log(results); // ["Va'da 1", "Va'da 2"]
  })
  .catch((error) => {
    console.log(error);
  });
```
---
### 5. Promise.race() - Bitta yoki undan ko'p Promiselarni bajarish va birinchisi ishga tushadigan va'dani qaytarish uchun ishlatiladi.
```sh
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Va'da 1"), 2000);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Va'da 2"), 1000);
});

Promise.race([promise1, promise2])
  .then((result) => {
    console.log(result); // "Va'da 2" - Birinchi bajarilgan va'da
  })
  .catch((error) => {
    console.log(error);
  });
```
