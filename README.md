# Fast Foodies

## Project Description
People need to eat, and coincidentally, are short on time. Here comes our idea for our fast food restaurant. We are basing our database on the functions and business model of said fast-food restaurant.

## Assumptions
- Cooks will not eat the food
- Front staff cannot be cooks or managers
- Managers cannot be cooks
- Customers can either order through the drive-thru or sit down, not both
- One cook can cook multiple orders
- One customer can make multiple orders
- One front staff can serve multiple customers
- Customers cannot substitute or add ingredients
- Managers will manage a group of employees in the restaurant 
- A Cook can cook any order
- All burgers have two buns and one patty
- All customers who enter the restaurant make an order
- Receipt will be either printed or emailed, no "none" option
- Customer will only talk to one front staff per order

## Entity Dictionary
<b>Entity:</b> Burgers <br>
<b>Description:</b> Burger is a type of sandwich and a subclass of Food.<br>
<b>Attributes:</b> 
- Lettuce, Boolean
- Ketchup, Boolean
- Mayo, Boolean
- Mustard, Boolean
- Onions, Boolean
- Tomatoes, Boolean
- Food_Number, Int
- Primary Key: Food_Number, inherited from Food

<b>Entity:</b> Cooks<br>
<b>Description:</b> Cooks are people who work in the kitchen and are a subclass of Employee. <br>
<b>Attributes:</b>
- Frying Pan, VarChar(16)
- Primary Key: Employee_ID inherited from Employee 

<b>Entity:</b> Customer<br>
<b>Description:</b> Customer is the person who comes to the restaurant to buy food by giving an order to the front staff<br>
<b>Attributes:</b> 
- Name, VarChar(32)
- Cell Number, Int
- Primary Key: Cell_Number and Name 

<b>Entity:</b> Drinks <br>
<b>Description:</b>  Drinks are stuff to be drunk and a subclass of Order. <br>
<b>Attributes:</b>
- Size, VarChar(8)
- Price, Decimal(3,2)
- Name, VarChar(32)
- Drink_Number, Int
- Primary Key: Drink_Number


<b>Entity:</b> Employee<br>
<b>Description:</b> Employee is the person who works at the restaurant.<br>
<b>Attributes:</b>
- Employee ID, Int
- Employment Date, Date
- First Name, VarChar(16)
- Last Name, VarChar(16)
- Salary, Decimal(5,2)
- Primary Key: Employee ID

<b>Entity:</b> Food<br>
<b>Description:</b> Food is the item eaten by customers.<br>
<b>Attributes:</b>
- Expiration Date, Date
- Price, Decimal(3,2)
- Name, VarChar(60)
- Food Number, Int
- Primary Key: Food Number

<b>Entity:</b> Fries<br>
<b>Description:</b> Fries are fried potato sticks and a subclass of Food.<br>
<b>Attributes:</b>
- Size, VarChar(8)
- Style, VarChar(16)
- Salt, Boolean
- Food Number, Int
- Primary Key: Food Number, inherited from Food

<b>Entity:</b> Front Staff<br>
<b>Description:</b> Front staff are employees who work with customers directly and are a subclass of Employee <br>
<b>Attributes: </b>
- Position, VarChar(32)
- Primary Key: Employee ID inherited from Employee

<b>Entity:</b> Manager<br>
<b>Description:</b> Manager is the person who manages employees and is a subclass of Employee. <br>
<b>Attributes:</b>
- Keys, VarChar(16)
- Primary Key: Employee ID inherited from Employee



<b>Entity:</b> Order <br> 
<b>Description:</b> Order is the request of food desired by the customer and taken by the Restaurant. <br>
<b>Attributes:</b>
- Payment Type, VarChar(32)
- Order Number, Int
- Date placed, Date
- Primary Key: Order Number

<b>Entity:</b> Receipt<br>
<b>Description:</b> Receipt is a record of an order.<br>
<b>Attributes:</b>
- Format, VarChar(16)
- Order Number, Int
- Primary Key: Order Number, inherited from Order

<b>Entity:</b> Salads<br>
<b>Description:</b> Salad is raw lettuce with other ingredients and a subclass of Food. <br>
<b>Attributes:</b>
- Size, VarChar(8)
- Dressing, Boolean
- Food Number
- Primary Key: Food Number, inherited from Food

<b>Entity:</b> Shakes<br>
<b>Description:</b> Shakes are a drink of blended ice cream and a subclass of Drinks. <br>
<b>Attributes:</b>
- Flavor, VarChar(12)
- Food Number
- Primary Key: Drink Number, inherited from Drink

<b>Entity:</b> Sodas <br>
<b>Description:</b> Sodas are carbonated drinks and a subclass of Drinks.<br>
<b>Attributes:</b> 
- Brand, VarChar(12)
- Food Number
- Primary Key: Drink Number, inherited from Drink

<b>Entity:</b> Tea <br>
<b>Description:</b> Teas are a type of beverage and a subclass of Drinks.<br>
<b>Attributes:</b> 
- Type, VarChar(12)
- Food Number
- Primary Key: Drink Number, inherited from Drink

<br>

## Relationship Dictionary

<b>Relationship:</b> Has <br>
<b>Description:</b> Order has Food<br>
<b>Entities:</b> Order, Food<br>
<b>Cardinality:</b> 1:N (1-to-Many)<br>
<b>Participation:</b> Partial-Partial<br>

<b>Relationship:</b> Has2<br>
<b>Description:</b> Order has Drinks<br>
<b>Entities:</b> Order, Drinks<br>
<b>Cardinality:</b> 1:N (1-to-Many)<br>
<b>Participation:</b> Partial-Partial<br>

<b>Relationship:</b> Manages<br>
<b>Description:</b> Manager manages Employees<br>
<b>Entities:</b> Manager, Employee<br>
<b>Cardinality:</b> 1:N (1-to-Many)<br>
<b>Participation:</b> Partial-Partial<br>

<b>Relationship:</b> Places<br>
<b>Description:</b> Front Staff Places Order<br>
<b>Entities:</b> Front Staff, Order<br>
<b>Cardinality:</b> 1:N (1-to-Many)<br>
<b>Participation:</b> Partial-Total<br>

<b>Relationship:</b> Prepares<br>
<b>Description:</b> Cooks prepare Food<br>
<b>Entities:</b> Cooks, Food<br>
<b>Cardinality:</b> 1:N (1-to-Many)<br>
<b>Participation:</b> Partial-Partial<br>

<b>Relationship:</b> Produces<br>
<b>Description:</b> An Order produces a receipt<br>
<b>Entities:</b> Order, Receipt<br>
<b>Cardinality:</b> 1:N (1-to-Many)<br>
<b>Participation:</b> Partial-Total<br>

<b>Relationship:</b> Talks To<br>
<b>Description:</b> Customer talks to Front Staff<br>
<b>Entities:</b> Customer, Front Staff<br>
<b>Cardinality:</b> 1:1 (1-to-1)<br>
<b>Participation:</b> Partial-Partial<br>

<br>

## Schema Dictionary
<b>Entity:</b> Burgers <br>
<b>Description:</b> Burger is a type of sandwich and a subclass of Food.<br>
<b>Attributes:</b> 
- Lettuce, Boolean
- Ketchup, Boolean
- Mayo, Boolean
- Mustard, Boolean
- Onions, Boolean
- Tomatoes, Boolean
- Food_Number, Int
- Primary Key: Food_Number
- Foreign Key: Food_Number, references Food.Food_Number

<b>Entity:</b> Cooks<br>
<b>Description:</b> Cooks are people who work in the kitchen and are a subclass of Employee. <br>
<b>Attributes:</b>
- Frying Pan, VarChar(16)
- Primary Key: Employee_ID 
- Foreign Key: Employee_ID, references Employee.Employee_ID
- Foreign Key: Manager_ID references Manager.Manger_ID


<b>Entity:</b> Customer<br>
<b>Description:</b> Customer is the person who comes to the restaurant to buy food by giving an order to the front staff<br>
<b>Attributes:</b> 
- Name, VarChar(32)
- Cell Number, Int
- Primary Key: Cell_Number and Name 
- Foreign Key: Employee_ID, references Employee.Employee_ID

<b>Entity:</b> Drinks <br>
<b>Description:</b>  Drinks are stuff to be drunk and a subclass of Order. <br>
<b>Attributes:</b>
- Size, VarChar(8)
- Price, Decimal(3,2)
- Name, VarChar(32)
- Drink_Number, Int
- Primary Key: Drink_Number
- Foreign Key: Order_Number references Order.Order_Number

<b>Entity:</b> Employee<br>
<b>Description:</b> Employee is the person who works at the restaurant.<br>
<b>Attributes:</b>
- Employee ID, Int
- Employment Date, Date
- First Name, VarChar(16)
- Last Name, VarChar(16)
- Salary, Decimal(5,2)
- Primary Key: Employee ID

<b>Entity:</b> Food<br>
<b>Description:</b> Food is the item eaten by customers.<br>
<b>Attributes:</b>
- Expiration Date, Date
- Price, Decimal(3,2)
- Name, VarChar(60)
- Food Number, Int
- Primary Key: Food Number
- Foreign Key: Employee_ID
- Foreign Key: Order_Number references Order.Order_Number


<b>Entity:</b> Fries<br>
<b>Description:</b> Fries are fried potato sticks and a subclass of Food.<br>
<b>Attributes:</b>
- Size, VarChar(8)
- Style, VarChar(16)
- Salt, Boolean
- Food Number, Int
- Primary Key: Food Number
- Foreign Key: Food_Number references Food.Food_Number

<b>Entity:</b> Front Staff<br>
<b>Description:</b> Front staff are employees who work with customers directly and are a subclass of Employee <br>
<b>Attributes: </b>
- Position, VarChar(32)
- Primary Key: Employee ID 
- Foreign Key: Manager_ID references Manager.Manger_ID
- Foreign Key: Employee_ID, references Employee.Employee_ID

<b>Entity:</b> Manager<br>
<b>Description:</b> Manager is the person who manages employees and is a subclass of Employee. <br>
<b>Attributes:</b>
- Keys, VarChar(16)
- Primary Key: Employee ID 
- Foreign Key: Employee_ID references Employee.Employee_ID

<b>Entity:</b> Order <br> 
<b>Description:</b> Order is the request of food desired by the customer and taken by the Restaurant. <br>
<b>Attributes:</b>
- Payment Type, VarChar(32)
- Order Number, Int
- Date placed, Date
- Primary Key: Order Number
- Foreign Key: Employee_ID references Employee.Employee_ID

<b>Entity:</b> Receipt<br>
<b>Description:</b> Receipt is a record of an order.<br>
<b>Attributes:</b>
- Format, VarChar(16)
- Order Number, Int
- Primary Key: Order Number
- Foreign Key: Order_Number references Order.Order_Number

<b>Entity:</b> Salads<br>
<b>Description:</b> Salad is raw lettuce with other ingredients and a subclass of Food. <br>
<b>Attributes:</b>
- Size, VarChar(8)
- Dressing, Boolean
- Food Number
- Primary Key: Food Number,
- Foreign Key: Food_Number references Food.Food_Number

<b>Entity:</b> Shakes<br>
<b>Description:</b> Shakes are a drink of blended ice cream and a subclass of Drinks. <br>
<b>Attributes:</b>
- Flavor, VarChar(12)
- Food Number
- Primary Key: Drink Number
- Foreign Key: Drink_Number references Drink.Drink_Number

<b>Entity:</b> Sodas <br>
<b>Description:</b> Sodas are carbonated drinks and a subclass of Drinks.<br>
<b>Attributes:</b> 
- Brand, VarChar(12)
- Food Number
- Primary Key: Drink Number
- Foreign Key: Drink_Number references Drink.Drink_Number

<b>Entity:</b> Tea <br>
<b>Description:</b> Teas are a type of beverage and a subclass of Drinks.<br>
<b>Attributes:</b> 
- Type, VarChar(12)
- Food Number
- Primary Key: Drink Number
- Foreign Key: Drink_Number references Drink.Drink_Number