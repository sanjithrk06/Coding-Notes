
# Users

> [!User Services]
## Create User

- Validate the inputs,
- Hash the password,
- Check exist,
- Create the user,
- Return User.
---
## Find User By Id

- `User.findById(userId).populate("address")`,
- Check exist,
- Return User.
---
## Get User By Email

- Find One by email (`User.findOne({email})`),
- Check exist,
- Return User.
---
## Get User Profile By Token

- Use JWT Provider (`getUserIdFromToken`) to get the `userId`,
- Using the `userId`, call the function [[Functionalities(Services & Controllers)#Find User By Id]].
- Check exist,
- Return user.
---
## Get all users

- `find()` method,
- return user.
---
> [!User Controller]
## Get a User Profile

- Get the JWT from the `req.header.authorization`
- Call the function [[#Get User Profile By Token]] and pass the JWT in the parameter.
- Return the user.
---
## Get All the Users

- Call the function [[#Get all users]].
- Return the users.
---
# Auth

> [!Auth Controller]
## Register

- **Create a user** - (Call the function [[#Create User]] and Pass the `req.body` in the parameter).
- **Generate JWT** - ( Call the function [[#Generate Token]] and pass the `user._id` in the parameter).
- **Create Cart** - ( Call the function [[#Create Cart]] and pass the `user._id` in the parameter).
- **Return JWT** in response.
---
## Login

- **Get the email & password** from `req.body`,
- **Fetch User** - (Call the function [[#Get User By Email]]),
- **Check the User**,
- **Password Validation** (`bcrypt.compare(password, user.password)`),
- **Generate JWT** - ( Call the function [[#Generate Token]] and pass the `user._id` in the parameter).
- **Return JWT** in response.
---
# Cart

> [!Cart Service]
## Create Cart

- New Cart by passing `user` as parameter.
- Save the cart using `.save()` method.
- Return the saved cart.
---
## Find User Cart

- **Fetch the Cart** (`Cart.findOne({user: userId})`),
- **Fetch the Cart Items** (`CartItem.find({cart: cart._id}).populate("product")`),
- Assign `cart.cartItems = cartItems`,
- Initialize (**Total Price, Total Discounted Price, Total Items**) to $0$.
- Iterate through each cartItems and update the prices, items.
```js
for(let cartItem of cart.cartItems) {
	totalPrice += cartItem.price;
	totalDiscountedPrice += cartItem.dicountedPrice;
	totalItems += cartItem.quantity;
}
```
- Update the updated prices and items to cart.
```js
cart.totalPrice = totalPrice;
cart.totalDiscountedPrice = totalDiscountedPrice;
cart.totalItems = totalItems;
```
- Return the cart.
---
## Add Cart Item

- **Fetch the Cart** (`Cart.findOne({user: userId})`),
- **Fetch the Product** from `req`,
- **Check it is already present or not in cartItems** (`CartItem.findOne({cart: cart._id, product: product._id, userId})`),
- If not, create new Cart Item.
- Push the Cart Item to Cart and save() it.
---
# Cart Items
