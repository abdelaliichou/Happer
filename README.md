# Happer

**API Documentation**

---

### Base URLs
- **Development:** `https://happer-test.francecentral.cloudapp.azure.com/`
- **Production:** `https://happer-production.francecentral.cloudapp.azure.com/`

---

## **Authentication**

### **Signup**
**URL:** `POST /api/users/register`
**Body:**
```json
{
  "email": "email",
  "first_name": "first_name",
  "last_name": "last_name",
  "gender": "gender",
  "password": "password",
  "password_confirmation": "confirmation_password",
  "code": "sponsorship_code",
  "country": "country"
}
```

### **Login**
**URL:** `POST /users/login`
**Body:**
```json
{
  "email": "email",
  "password": "password"
}
```

---

## **Newsfeed**

### **Newsfeed Creator**
1. **Get All Categories**
   - **URL:** `GET /api/categories`
   - **Headers:** `Authorization: Token`

2. **Get All Selfies**
   - **URL:** `GET /api/selfies/influencer?category={currentCategorie.id}&page={page}&validated=VALIDATED&country={country}`
   - **Headers:** `Authorization: Token`

### **Newsfeed Discover**
1. **Get All Selfies**
   - **URL:** `GET /api/selfies?category={id}&page={page}&validated=VALIDATED&country={country}`
   - **Headers:** `Authorization: Token`

---

## **User Profile**

1. **Modify Password**
   - **URL:** `PUT /api/users/modify_password`
   - **Body:**
   ```json
   {
     "newPassword": "newPassword",
     "confirmPassword": "confirmPassword",
     "oldPassword": "oldPassword"
   }
   ```
   - **Headers:** `Authorization: Token`

2. **Update User Profile**
   - **URL:** `PUT /api/users/{user.id}`
   - **Body:**
   ```json
   {
     "first_name": "firstName",
     "last_name": "lastName",
     "address": "address",
     "postal_code": "postalCode",
     "city": "city",
     "birthdate": "birthdate",
     "phone": "phone",
     "country": "country"
   }
   ```
   - **Headers:** `Authorization: Token`

3. **Get User Information & Address**
   - **URL:** `GET /users/me`
   - **Headers:** `Authorization: Token`

4. **Delete Profile Picture**
   - **URL:** `GET /api/users/picture/delete`
   - **Headers:** `Authorization: Token`

5. **Upload Profile Picture**
   - **URL:** `POST /api/users/upload`
   - **Body:** `{ "imagefile": "imagefile" }`
   - **Headers:** `Authorization: Token`

6. **Delete User Profile**
   - **URL:** `DELETE /api/users/{userId}`
   - **Body:** `{ "code": "code" }`
   - **Headers:** `Authorization: Token`

7. **Reset Password**
   - **URL:** `PUT /api/users/reset_password`
   - **Body:**
   ```json
   {
     "email": "email",
     "code": "code",
     "password": "password"
   }
   ```
   - **Headers:** `Authorization: Token`

---

## **Product Page**

1. **Like Product**
   - **URL:** `POST /api/likes`
   - **Body:**
   ```json
   {
     "selfie_id": "selfie.id",
     "user_id": "user.id"
   }
   ```
   - **Headers:** `Authorization: Token`

2. **Dislike Product**
   - **URL:** `DELETE /api/likes/user`
   - **Body:**
   ```json
   {
     "selfie_id": "selfie.id",
     "user_id": "user.id"
   }
   ```
   - **Headers:** `Authorization: Token`

---

## **Cart**

1. **Add Product to Cart**
   - **URL:** `POST /carts/add`
   - **Body:**
   ```json
   {
     "item_id": "itemId",
     "quantity": "quantity",
     "size": "size",
     "user_id": "user_Id"
   }
   ```
   - **Headers:** `Authorization: Token`

2. **Delete Product from Cart**
   - **URL:** `DELETE /carts/item`
   - **Body:** `{ "item_id": "itemId" }`
   - **Headers:** `Authorization: Token`

3. **Get All Cart Products**
   - **URL:** `GET /carts/me`
   - **Headers:** `Authorization: Token`

4. **Get Product by ID**
   - **URL:** `GET /items/{itemId}`
   - **Headers:** `Authorization: Token`

---

## **Payment**

1. **Stripe Payment Popup**
   - **URL:** `POST /carts/stripe`
   - **Body:** `{ "api_version": "2022-11-15" }`
   - **Headers:** `Authorization: Token`

---

## **Influencer Page**

1. **Get Selfies Shared by Influencer**
   - **URL:** `GET /selfies/profile/{influencerId}`
   - **Headers:** `Authorization: Token`

2. **Get Influencer Profile**
   - **URL:** `GET /users/profile/{influencerId}`
   - **Headers:** `Authorization: Token`

3. **Get Number of Followers**
   - **URL:** `GET /follows/user/{influencerId}`
   - **Headers:** `Authorization: Token`

4. **Follow Influencer**
   - **URL:** `POST /follows`
   - **Body:**
   ```json
   {
     "follower_id": "userFollowedId",
     "user_id": "influencerId"
   }
   ```
   - **Headers:** `Authorization: Token`

5. **Unfollow Influencer**
   - **URL:** `DELETE /follows/user`
   - **Body:**
   ```json
   {
     "target_id": "influencerId"
   }
   ```
   - **Headers:** `Authorization: Token`

---
