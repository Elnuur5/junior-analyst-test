
# Registration API

## Endpoint
POST /api/v1/users/register

---

## Request

{
  "email": "test@gmail.com",
  "password": "Password123",
  "firstName": "John",
  "lastName": "Doe"
}

---

## Response (success)

{
  "userId": 101,
  "message": "User successfully registered"
}

---

## HTTP Status Codes

201 — пользователь успешно создан  
400 — неверные или неполные данные  
409 — пользователь с таким email уже существует  
500 — ошибка на стороне сервера  

---

## Error cases

400 Bad Request — не заполнены обязательные поля или неверный формат данных  
409 Conflict — email уже занят  
500 Internal Server Error — непредвиденная ошибка сервера  

---

# Backend logic (как это работает)

1. Получен запрос на регистрацию пользователя  
2. Проверяются обязательные поля (email, password, firstName, lastName)  
3. Проверяется формат email  
4. Проверяется пароль (минимум 8 символов)  
5. Проверяется, есть ли пользователь с таким email в базе  
6. Если пользователь существует — возвращается ошибка 409  
7. Пароль хешируется перед сохранением  
8. Создаётся новый пользователь в базе данных  
9. Пользователь сохраняется  
10. Возвращается userId и сообщение об успешной регистрации  
