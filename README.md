# ALL-ABOUT-CONTROLLERS--API-POST-GET-CREATE....ETC-

# Product Controller

This file contains functions to create a new product and fetch all products in the database. It interacts with the `Product` model and uses consistent naming conventions for fields across the model, controller, and routes.

### File: `controllers/productController.js`

```javascript
const modelKaname = require('../models/Product');    

// Function to create a new product
exports.createProduct = async (req, res) => {
  try {
    // Extract fields from the request body
    const { name, price, description, category } = req.body;   // model se field dekh lo thats'why  1st create model then come to controller

    // Create a new Product instance
    const tumharaDataSave = new modelKaname({
      name,          // Matches the "name" field in the model
      price,         // Matches the "price" field in the model
      description,   // Matches the "description" field in the model
      category,      // Matches the "category" field in the model
      createdAt: new Date() // Auto-sets the date or could be omitted to use default
    });

    await tumharaDataSave.save(); // Save product to the database
    res.status(201).json({ message: 'Product created successfully', product });
  } catch (error) {
    res.status(500).json({ error: 'Failed to create product', details: error.message });
  }
};


```







```
// Function to get all products
exports.getAllProducts = async (req, res) => {
  try {
    const products = await Product.find(); // Fetches all products
    res.status(200).json(products);
  } catch (error) {
    res.status(500).json({ error: 'Failed to fetch products', details: error.message });
  }
};
```
